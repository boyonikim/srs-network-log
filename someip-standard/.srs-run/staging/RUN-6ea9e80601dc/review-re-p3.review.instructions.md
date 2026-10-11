# Task instruction packet

Paths below are relative to the Skill root or their named original source. Only manifest fresh evaluation IDs are judgment targets. Extra rules retained for context do not expand scope.

Original source: agents/re-reviewer.md

# agents/re-reviewer.md

먼저 [공통 task 실행 계약](../references/task-execution.md)을 읽고 적용한다.

> 위임받는 Subagent가 읽는 지침. 상위 Agent의 대화 이력을 상속하지 않는 것으로
> 취급하고, 여기 적힌 것과 task manifest가 가리키는 입력 파일만으로 판단한다.
> **이 Subagent는 파이프라인을 재시작하거나 다른 단계를 위임하지 않는다.** 검토
> 결과 JSON을 반환하는 것으로 임무가 끝난다.

## 범위

`policies/writing-rules.yaml`에 등재된 요구공학 규칙 10개
(`RE-ATOMIC-001`, `RE-FORM-001`, `RE-RESP-001`, `RE-TYPE-001`,
`RE-EXCEPT-001`, `RE-PARAMREF-001`, `RE-COMPLETE-001`, `RE-AMBIG-001`,
`RE-SUBJECT-001`, `RE-VERIFY-001`) 전부 지원한다. 이 중
`RE-ATOMIC-001`/`RE-AMBIG-001`/`RE-SUBJECT-001`/`RE-VERIFY-001` 4개는 이
문서가 직접 탐지 로직을 갖지 않는다 — `srs-clarity` 스킬 위임 절(아래)
참고. 나머지 6개는 이 Subagent 자신의 판정 로직을 그대로 쓴다.

## 배치·replay·context 규칙

이 task는 leaf별 Subagent 호출이 아니라 한 axis/round의 bounded batch다.
`task manifest.input.candidate_leaves`는 이번 round의 전체 평가 후보이고,
`input.leaves`는 그중 이 task에서 실제로 fresh 평가할 leaf다.
`input.context_leaves`는 related/module/L2 비교를 위한 **읽기 전용** 파일이다.

- `input.dispatch_plan.entries`의 `role: target` 항목만 평가한다.
- 각 target/group의 `fresh_rule_ids`마다 decision을 하나씩 반환한다.
  수행하지 못한 규칙도 BLOCKED와 사유로 남긴다. `replay_rule_ids`는 controller가 PASS stamp에서
  병합하므로 Subagent가 다시 평가하거나 `source: replayed`로 만들지 않는다.
- `role: context` leaf는 내용을 읽어 target 판정의 비교·evidence로 사용할 수
  있지만 독립적인 `checks`, `leaf_evaluations`, verdict, stamp를 만들지 않는다.
- context leaf도 함께 수정해야 한다고 판단하면 `context_promotions`에만
  요청한다. 요청은 현재 task의 `role: context` leaf에 한정하고, 실제 재평가는
  controller가 `*-pN` follow-up bounded batch를 만들어 수행한다. 다음 task에서
  promoted leaf는 일반 target처럼 fresh 평가한다.
- replay 여부, stamp 유효성, 대상 scope 확장은 Subagent가 판단하지 않는다.
  요청 범위 밖 leaf를 임의로 추가하거나 자동으로 평가하지 않는다.
- `input.dispatch_plan.unavailable_evaluations`에 있는 `(subject, rule)`은
  제어기가 **디스패치하지 못한** 평가다(예: module/L2 scope 규칙인데 그 group의
  member leaf가 이번 요청 범위에 전부 들어오지 않음). 이 rule들은
  `required_checks`에는 들어 있으나 대응하는 `role: target` 엔트리가 없다.
  각 항목을 그 `subject_type`/`subject_key`/`rule_id`/`reason` 그대로
  controller가 정식 결과의 `not_evaluated`에 보존한다. 다른 leaf에 끼워 넣어(anchoring) 판정을
  통과시키지 않는다 — 그렇게 하면 stamp가 엉뚱한 subject에 남아 다음 라운드에
  재사용되지 않고, 판정 근거도 거짓이 된다. 임의로 PASS를 주지도 않는다.

## RE-ATOMIC-001 / RE-AMBIG-001 / RE-SUBJECT-001 / RE-VERIFY-001 — srs-clarity 스킬 위임

대상: leaf의 `## Description` 본문(+ frontmatter 일부).

이 4개 rule_id는 이 문서 자신의 판정 로직이 없다 — **반드시
`skill("srs-clarity")`를 호출**해 그 판정을 그대로 가져와 쓴다. 이
Subagent 자신이 모호성/주어/검증가능성/원자성을 별도로 재해석하거나
독자적인 로직으로 대신 판정하지 않는다(중복 판정 금지, srs-clarity
호출 결과가 유일한 근거다).

**호출 방식 — CodeBeamer 관련 절은 전부 건너뛴다.** srs-clarity는 원래
CodeBeamer 아이템 URL 기반 대화형·쓰기 스킬(트래커 선택,
`ask_user` 아이템 피커, `clarity_api.py fetch`/CB 필드 업데이트)이지만,
지금 리뷰 대상은 CodeBeamer 아이템이 아니라 **이 task manifest가 가리키는
로컬 leaf 파일**이다. 그래서:

1. `skill("srs-clarity")`로 스킬을 로드하되, `SKILL.md`/
   `srs-clarity-workflow.md`가 지시하는 트래커 조회 · `ask_user` 아이템
   선택 · CodeBeamer fetch/update 호출은 **하나도 실행하지 않는다.**
   이 Subagent는 애초에 대화형 `ask_user`나 CodeBeamer 쓰기를 수행할 수
   없는 역할이므로, 그 경로를 흉내 내지 않는다.
2. 그 대신 srs-clarity의 판정 프롬프트(`instruction_SRS_clarity_single.md`)
   하나만 로컬로 적용한다. 그 프롬프트의 `<INPUT_DATA>` 자리에 이 leaf의
   값을 직접 채운다: `req_id`←leaf `uid`(또는 `id`), `parent`←
   `related_items`/소속 모듈, `summary`←`title`, `inclusion_type`/
   `optional_condition`←frontmatter에 있으면 그 값, 없으면 `-`,
   `param_def`←frontmatter의 파라미터 정의가 있으면 그 값, 없으면 `-`,
   `description`←leaf `## Description` 본문 그대로.
3. 그 프롬프트의 `<REVIEW_CRITERIA>`/`<OUTPUT_FORMAT_RULES>`를 그대로
   적용해 "4대 기준 체크"(기준1 모호성, 기준2 주어 명확성, 기준3 검증
   가능성, 기준4 원자성) O/X와 사유를 얻는다.
4. 그 결과를 아래처럼 매핑한다:

   | srs-clarity 4대 기준 | rule_id |
   |---|---|
   | 기준1. 모호성 배제 | `RE-AMBIG-001` |
   | 기준2. 주어 명확성 | `RE-SUBJECT-001` |
   | 기준3. 검증 가능성 | `RE-VERIFY-001` |
   | 기준4. 원자성 | `RE-ATOMIC-001` |

   O → `verdict: PASS`, `evidence: null`. X → `verdict: FAIL`이고
   `evidence`는 **leaf 원문의 진짜 부분 문자열**이어야 한다(상위 Gate가
   substring 일치로 재검증한다 — srs-clarity가 낸 "사유" 문장을 그대로
   베끼지 않는다. 그 사유가 가리키는 leaf 원문 조각을 직접 찾아 채운다).
   그 부분 문자열을 leaf 원문에서 찾을 수 없으면 `verdict: BLOCKED`로
   표시하고 이유를 남긴다 — `PASS`로 임의 확정하지 않는다. `rationale`에는
   srs-clarity의 사유 문장을 요약해 담고, srs-clarity가 함께 낸
   "__개선 제안:__" 내용이 있으면 이어서 짧게 덧붙여도 된다(스키마에
   전용 필드가 없으므로 `rationale` 문자열 하나에 담는다).
5. `skill("srs-clarity")` 호출 자체가 이 실행 환경에서 불가능하다면(도구
   미제공 등), 이 4개 중 현재 배정된 fresh rule만 `verdict: BLOCKED`로 정직하게
   보고한다 — 우회해서 다른 로직으로 대신 판정하지 않는다.
6. **srs-clarity가 낸 출력 원문을 버리지 않는다.** 위 매핑은 4대 기준만
   `review.json`으로 옮기고 "유형 분류"와 "개선 제안" 테이블은 흘려보내는데,
   그 둘은 나중에 CodeBeamer 아이템에 그대로 올라갈 내용이다. 아래
   "두 번째 산출물" 절에 따라 따로 저장한다.

## RE-FORM-001 — 형식

대상: leaf의 `## Description` 본문.

Description이 최소 하나의 정규 규칙 문장 — "[SW unit]은 [조건]에서
[동작]하여야 한다" 형태(조건절은 생략 가능) — 을 포함해야 한다.

- 위반: Description이 목적·배경 서술만 있고 "~하여야 한다"류의 의무
  문장이 하나도 없는 경우. 이런 서술은 L3/SyRS에 속하는 내용이지 L4 SRS의
  형식이 아니다.
- 위반이 아님: 의무 문장이 있으면 그 표현이 매끄럽지 않거나 문장이 길어도
  PASS다 — 이 규칙은 표현의 우아함이 아니라 "규칙 문장이 존재하는가"만
  본다. 표현의 모호함은 `RE-AMBIG-001`의 몫이다.
- 판정 절차: `checks`에 `verdict: PASS`, `evidence: null`로 기록한다.
  위반이면 `verdict: FAIL`을 기록하고 `evidence`는 Description 중
  의무 문장이 없다는 판정의 근거가 되는 **원문 그대로의 부분 문자열**
  (보통 목적/배경 서술 문장 자체)이어야 한다.
- 판단 근거가 불충분하면(예: 본문이 잘려 있어 의무 문장의 존재 여부를 판단할
  수 없음) `verdict: BLOCKED`로 표시하고 이유를 남긴다. `PASS`로 임의
  확정하지 않는다.

## RE-RESP-001 — 책임 단일성

대상: leaf의 `## Description` 본문. `id`의 L3 토큰과 `title`은 책임 범위를 이해하는 단서이며 주체명과 일치해야 하는 소유권 매핑이 아니다.

leaf는 자기 모듈 하나의 책임만 기술해야 한다. Description의 "~하여야 한다"
문장에서 행위 주체가 이 leaf가 속한 모듈이 아니라 이름이 다른 모듈/컴포넌트로
읽히면(예: ServiceDiscovery leaf인데 "이더넷 드라이버는 ~하여야 한다"처럼 다른
모듈에 의무를 지우면) 계층 위반이다.

- 위반이 아님: 다른 모듈이 문장에 언급만 되고(예: "…로부터 수신하면"처럼 입력
  출처로만 등장), 실제 의무(하여야 한다)의 주체는 여전히 이 leaf의 모듈인
  경우.
- 본문의 의무 주체가 단일 SW unit이면 별도 owner mapping을 요구하지 않는다. 이름이 다른 것만으로 FAIL/BLOCKED를 만들지 않고, 다른 unit에 의무를 지웠다는 실제 근거를 확인한다.
- 판정 절차: 위반 없으면 `verdict: PASS`, `evidence: null`. 위반이면
  `verdict: FAIL`이고 `evidence`는 다른 모듈에 의무를 지우는 문장의 **원문
  그대로의 부분 문자열**이어야 한다.

## RE-TYPE-001 — 유형 일치

대상: leaf frontmatter의 `spec_pattern_type` 필드와 `## Description` 본문.

`spec_pattern_type`이 본문이 실제로 서술하는 형태와 일치해야 한다:

| `spec_pattern_type` | 본문이 보여야 할 형태 |
|---|---|
| `mode_state` | 상태/전이 — 트리거 → 결과 상태 |
| `data_logic` | 입력 → 연산/검증 → 출력 |
| `interface_comm` | 경계를 넘는 메시지/API 교환 |
| `exception_fault` | 결함의 탐지 → 보고 → 복구 |
| `nonfunctional` | 타이밍/용량/품질 제약 |

- `mode_state`의 결과 상태는 의무 주체가 도달해야 할 상태다. 이미 발생한 PHY 상태 변화를 보고하는 행위 자체를 SW unit의 상태 전이로 간주하지 않는다. 보고 지연의 상한을 규정하는 문장은 `nonfunctional`이며, 수신자와 메시지 교환 자체를 규정하면 `interface_comm`이다.
- 위반이 아님: 본문이 선언된 유형의 핵심 형태를 충족하면 PASS. 부수적으로 시간값이 있다는 이유만으로 다른 유형으로 재분류하지 않는다.
- 위반: 선언된 유형의 핵심 형태는 없고 다른 유형의 형태가 명확한 경우. `evidence`는
  frontmatter의 `spec_pattern_type` 값 문자열(예: `mode_state`)이어야 한다 —
  leaf 원문(frontmatter 포함)에 그대로 나타나는 부분 문자열이므로 유효하다.
- 본문이 표의 어느 형태에도 뚜렷이 속하지 않아 판단이 어려우면
  `verdict: BLOCKED`로 표시하고 이유를 남긴다.

## RE-EXCEPT-001 — 예외 경로

대상: `## Description`과 frontmatter `spec_pattern_type`/`related_items`,
그리고 연관 형제 leaf의 **실제 내용**.

`spec_pattern_type`이 `mode_state`/`data_logic`/`interface_comm`인 leaf는
비정상 경로(보통 `※ 예외 규칙` 절)를 다뤄야 한다. `exception_fault`와
`nonfunctional`은 면제 — 그 즉시 `verdict: PASS`.

### 정상 동작과 예외 대응의 경계

판정 대상은 상태 이름의 좋고 나쁨이 아니라 **명시한 비정상 조건과 대응 동작의 쌍**이다.
링크 상실(UP→DOWN), 오류 입력, timeout 만료처럼 본문에 드러난 비정상 조건에
대한 이벤트·거부·복구 동작이 있으면 그 요구사항 자체가 예외 대응을 다룬다.
`※ 예외 규칙` 제목이나 별도 문장이 없어도 절차 1에서 PASS다.
그 대응 자체의 실패를 원문이 언급하지 않았다면 새로운 실패 경로를 만들어
요구하지 않는다. 상태 이름만 있거나 대응 동작이 없으면 이 근거로 PASS하지 않는다.

| 본문과 확인된 context | RE-EXCEPT-001 판정 |
|---|---|
| 링크가 UP에서 DOWN으로 전환되면 100ms 이내 이벤트를 발행한다 | PASS: 링크 상실 조건과 대응이 모두 있음. 의무 문장 형식은 RE-FORM-001에서 별도 판정 |
| 링크가 DOWN에서 UP으로 전환되면 연결 완료 이벤트를 발행한다. 관련 형제 없음 | FAIL: 연결 성립 정상 경로만 있음 |
| 정상 송신만 서술하지만 읽은 관련 형제가 송신 실패 시 오류 보고를 책임짐 | PASS: 형제의 실제 대응을 근거로 위임 확인 |
| 정상 송신만 서술하고 관련 예외 형제 파일을 열 수 없음 | BLOCKED: 링크 존재만으로 PASS하지 않음 |

PASS rationale에도 비정상 조건·대응 동작 또는 면제 유형·책임 형제를 구체적으로
적는다. 판단할 정보가 부족하면 BLOCKED이며, 다른 규칙의 FAIL을 이 규칙에 전파하지 않는다.

`related_items`는 "내용상 연관·상호보완" 링크이지 "예외를 위임했다"는
선언이 아니다. 링크의 **방향은 의미가 없다** — 이 leaf가 형제를 가리키든
형제가 이 leaf를 가리키든 똑같이 연관이다. 제어기가 양방향 형제를 모두
`input.context_leaves`로 넣어 주므로, **형제가 이 leaf를 되가리키지 않는다는
이유로 FAIL을 주지 않는다.** 책임 여부는 형제의 내용을 읽어야 안다.

판정 순서는 다음과 같다. 중간에 결론이 나면 거기서 멈춘다.

1. **자기 본문을 먼저 본다.** `## Description`이 예외/비정상 경로를
   서술하면 `verdict: PASS`.
2. **연관 형제를 모은다.** 이 leaf의 `related_items`가 가리키는 leaf와,
   `input.context_leaves`/`input.leaves` 중 자기 `related_items`로 이 leaf를
   가리키는 leaf를 **합쳐서** 본다. 둘 다 없으면 `verdict: FAIL` —
   `evidence`는 정상 경로만 서술한다는 판정의 근거가 되는 이 leaf 원문의
   부분 문자열(보통 정상 동작 문장 자체).
3. **형제가 있으면 그 내용을 실제로 확인한다.** **링크가 존재한다는 사실만으로
   PASS를 주지 않는다.** 형제 중 하나라도 다음 둘 중 하나면 위임이 성립한
   것으로 보고 `verdict: PASS`:
   - 그 형제의 `spec_pattern_type`이 `exception_fault`다
   - 그 형제의 `## Description`이 이 leaf의 정상 경로에 대응하는 예외/
     비정상 동작을 서술한다
   `rationale`에 **어느 형제가 무엇을 책임지는지** 구체적으로 적고, 그 형제를
   정방향(`related_items`)에서 찾았는지 역방향에서 찾았는지 함께 적는다.
   "related_items가 있으므로 위임됨" 같은 무근거 사유는 금지다.
4. **아직 확인하지 못한 연관 형제가 있으면** `verdict: BLOCKED`로 표시하고
   어느 식별자를 못 열었는지 남긴다. 확인한 형제 중 위임이 성립한 경우는
   이미 3번에서 PASS로 종료한다.
5. **관련 형제를 모두 확인했지만 어느 것도 3을 만족하지 않으면** `verdict: FAIL`.
   `evidence`는 이 leaf 원문의 부분 문자열로 기록하고, `rationale`에 확인한
   형제와 예외를 책임지지 않는 이유를 적는다.
6. 판단이 어려우면(예: 본문이 잘려 있음) `verdict: BLOCKED`.

## RE-PARAMREF-001 — 파라미터 참조

대상: `## Description` 본문의 `{P_Name}` 참조와 frontmatter
`parameter_definition`/`mapped_parameter`, 그리고 그 파라미터를 소유한 다른
leaf의 `parameter_definition`.

본문의 파라미터 참조는 `{P_Name}` 중괄호 문법만 인정한다. 먼저 네 집합을
구한다:

- `own` = 이 leaf `parameter_definition[].name` 전체
- `foreign` = 본문의 `{P_Name}` 중 `own`에 없는 것 (= 외부 소유)
- `declared` = 이 leaf `mapped_parameter[].uid` 전체
- `required` = `foreign`을 `parameter_definition`으로 소유한 leaf들의 `uid`
  (자기 자신 제외). 소유 leaf는 `input.leaves`와 `input.context_leaves`
  양쪽에서 찾는다.

**아래 순서대로 보고 처음 걸리는 조건 하나만 보고한다.** 여러 조건이 동시에
성립해도 번호가 작은 쪽만 `checks`에 넣는다 — 한 leaf·한 rule_id당 check는
정확히 하나다.

| 순서 | 조건 | verdict | evidence / location |
|---|---|---|---|
| 1 | 소유 후보 leaf가 `input.leaves`/`context_leaves` 어디에도 없어 소유권을 확인할 수 없음 | `BLOCKED` | — (못 연 식별자를 `rationale`에) |
| 2 | `required - declared ≠ ∅` (외부 파라미터를 참조하는데 소유 leaf가 `mapped_parameter`에 없음) | `FAIL` | 그 `{P_Name}`을 포함한 본문 문장 / `## Description` |
| 3 | 어떤 leaf도 소유하지 않는 `{P_Name}`을 참조 | `FAIL` | 그 `{P_Name}`을 포함한 본문 문장 / `## Description` |
| 4 | `declared - required ≠ ∅` (`mapped_parameter`에 있는데 본문이 그 파라미터를 참조하지 않음) | `FAIL` | 이 leaf 원문의 `mapped_parameter:` 줄 / `frontmatter.mapped_parameter` |
| 5 | 같은 `P_Name`을 같은 L3 모듈 내 2개 이상 leaf가 `parameter_definition`으로 소유 | `FAIL` | 이 leaf `parameter_definition` 중 그 `name:` 줄 / `frontmatter.parameter_definition` |
| 6 | 위 어디에도 해당하지 않음 | `PASS` | `null` |

- **자기가 정의한 파라미터를 자기 본문에서 쓰는 것 자체는 위반이 아니다.**
  `foreign`과 `declared`가 모두 비면 조건 2·3·4를 그냥 지나가므로,
  중복 소유만 없으면 조건 6 PASS다 — `mapped_parameter: []`가 정상이다.
- **단, 그 파라미터를 같은 L3의 다른 leaf도 정의하면 조건 5 FAIL이다.** 자기
  정의·자기 참조라는 사실이 중복 소유를 면제하지 않는다. 한쪽이 소유하고 다른
  쪽은 `mapped_parameter`로 참조하도록 고쳐야 한다. `rationale`에 중복 소유자
  leaf를 전부 나열한다.
- 조건 5의 "같은 L3 모듈"은 `id`(`SRS-<L2>-<L3>-NNNN`)의 `<L3>` 토큰으로
  판단한다. 모듈이 다르면 위반이 아니다.
- 여러 leaf 배치에서는 `location` 앞에 `"<uid>: "` 접두어를 붙인다(아래
  "반환 형식" 절의 기존 규약).

### rationale에 반드시 남길 것 (형식 고정)

이 규칙은 집합 연산으로 판정한다. **집합을 실제로 계산했다는 증거를
`rationale`에 남기지 않은 판정은 무효다.** verdict와 무관하게, PASS도
포함해 아래 형식으로 시작한다:

```
own={...}, foreign={...}, declared=[...], required=[...] -> 조건 N
```

- 비어 있는 집합은 `{}` / `[]`로 **명시**한다. 생략하지 않는다.
- `required`와 `declared`의 원소는 uid를 그대로 적는다. 그 uid를 어느
  leaf에서 찾았는지(`input.leaves` / `input.context_leaves`)도 적는다.
- 조건 2·4로 FAIL이면 `required - declared` 또는 `declared - required`의
  **차집합 원소를 그대로** 적는다. 조건 5면 중복 소유자 leaf를 전부 적는다.
- 조건 6 PASS는 `required`와 `declared`가 **왜 일치하는지**가 위 한 줄로
  드러나야 한다.

집합의 실제 원소 없이 "일치함"만 쓰지 않는다. 같은 문장을 일괄 복사하지
말고 각 leaf에서 계산한 값을 남긴다. 실제 집합이 같으면 같은 결과가 나올 수 있다.

## RE-COMPLETE-001 — 완전성

대상: `## Description` 본문.

leaf 자신의 서술이 스스로 암시하는 분기를 빠뜨리면 위반이다 — 예를 들어
timeout 값을 정의해 놓고 timeout이 만료됐을 때의 동작을 말하지 않는 경우.
**leaf 자신이 말한 것이 암시하는 분기만 판단한다** — 이 leaf가 언급조차 하지
않은, 모듈 외부의 새로운 요구사항을 만들어내지 않는다.

- 위반이 아님: leaf가 암시하는 분기를 실제로 다루고 있으면(다른 절에서든) PASS.
  leaf가 애초에 분기를 암시하지 않는 단순 서술이면 지적할 것이 없으므로 PASS.
- 위반: `verdict: FAIL`이고 `evidence`는 분기를 암시하는(그러나 그 결과를
  말하지 않는) leaf 원문의 부분 문자열이어야 한다.
- 판단이 어려우면 `verdict: BLOCKED`로 표시한다.

## 반환 형식

[공통 검토 출력 계약](../references/task-execution.md#검토-출력)을 따른다.
`location`에는 대상 uid와 section 또는 frontmatter 필드를 적는다.
요구공학 축의 `severity`는 `null`이다.

## 두 번째 산출물 — clarity feedback (`clarity_output_path`)

task manifest에 `clarity_output_path`가 있으면, `output_path`의
`review.json`과 **별개로** 그 경로에도 파일 하나를 더 쓴다. 정본은
`contracts/clarity-feedback.schema.json`이다.

그 원문은 나중에 `mode=publish`의 마지막 단계가 CodeBeamer 아이템의
Clarity 필드에 그대로 올리는 내용이다. 여기서 버리면 다시 만들어낼
방법이 없고, 게시 시점에 다시 판정하면 "리뷰한 내용과 게시된 판정이
다를 수 있다"는 뜻이라 허용되지 않는다.

`entries`에는 이번 task에서 실제로 srs-clarity 판정을 수행한 leaf만 넣는다.
읽기 전용 context나 replay 대상의 결과를 새로 만들지 않는다.

| 필드 | 값 |
| --- | --- |
| `leaf_uid` | 그 leaf frontmatter의 `uid` 그대로 |
| `overall_verdict` | 4대 기준이 **전부 O**일 때만 `PASS`, 하나라도 X면 `FAIL` (srs-clarity 자신의 규칙) |
| `req_pattern` | srs-clarity의 "유형 분류" 4종 중 하나를 **영문 원문 그대로** (`Mode & State Behavior` / `Data Transformation & Logic` / `Interface & Communication` / `Non-Functional Constraints`) — 번역·축약하면 필드 쓰기가 거부된다 |
| `feedback_markdown` | srs-clarity 출력 **전문**(유형 분류 + 4대 기준 체크 + 개선 제안 테이블). `PASS`여도 전문 그대로 포함한다(`contracts/clarity-feedback.schema.json`이 PASS에도 개선 제안 테이블 포함을 요구) |

`task_id`와 `input_fingerprint`는 task manifest에서 그대로 옮겨 적는다.
`leaf_content_fingerprint`/`leaf_path`는 **적지 않는다** — Python이 채우는
필드이고, 지어내서 적으면 그 항목 전체가 거부된다.

srs-clarity 호출이 불가능했다면(위 5번) 이 파일을 쓰지 않는다. 비어 있거나
지어낸 판정을 남기는 것보다 없는 편이 낫다 — 없으면 나중에 게시가 막히고,
지어내면 막히지 않는다.

dispatch가 없는 task는 `required_checks` 전체를 대상으로 한다. dispatch가
있으면 현재 target의 fresh tuple만 반환하고 replay 결과는 controller에 맡긴다.

RE-EXCEPT/COMPLETE의 예외·분기 근거가 없으면 `reason_code: missing_evidence`,
`actionability: await_input`으로 기록한다. 확인되지 않은 의무를 추가하는 edit을 요구하지 않는다.
