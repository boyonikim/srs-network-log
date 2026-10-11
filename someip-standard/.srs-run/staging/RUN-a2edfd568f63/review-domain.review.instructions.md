# Task instruction packet

Paths below are relative to the Skill root or their named original source. Only manifest fresh evaluation IDs are judgment targets. Extra rules retained for context do not expand scope.

Original source: agents/domain-reviewer.md

# agents/domain-reviewer.md

먼저 [공통 task 실행 계약](../references/task-execution.md)을 읽고 적용한다.

> 위임받는 Subagent가 읽는 지침. 상위 Agent의 대화 이력을 상속하지 않는 것으로
> 취급하고, 여기 적힌 것과 task manifest가 가리키는 입력 파일만으로 판단한다.
> **이 Subagent는 파이프라인을 재시작하거나 다른 단계를 위임하지 않는다.** 검토
> 결과 JSON을 반환하는 것으로 임무가 끝난다.
>
## 무엇을 검토하는가

task manifest의 `required_checks`는 `scripts/runtime/review_planner.py`가
`domain-packs/<domain>/`를 통해 생성했다 — leaf가 속한 domain(들)의 **이
프로젝트 자신이 소유한 로컬 체크리스트**에서 **그때그때 실시간으로** 추출한
rule id 목록이다. 검토를 시작하기 전에 반드시 아래 파일들을 **직접 읽는다**:

1. `domain-packs/<domain>/domain.yaml` — `local_checklist_path`/
   `local_rule_meta_path`(이 프로젝트 소유, 로컬)와 `source_skill.*`(sibling
   지식 스킬 포인터, 참조만) 구분, `rule_id_prefix` 매핑.
2. instruction packet에 포함된 체크리스트 발췌를 사용한다. packet이 없으면
   `domain-packs/<domain>/domain.yaml`의 `local_checklist_path`가 가리키는
   파일 (예: `domain-packs/ethernet/srs-review-checklist.md`) — 규칙 본문,
   Detect/Severity/Scope 서술이 여기 있다. **이 파일이 정본이다.** 이 파일은
   sibling 스킬이 아니라 이 프로젝트 자신의 review-dispatch 산출물이므로
   sibling 스킬을 따로 열 필요가 없다. 규칙 본문이 sibling 지식 스킬의 특정
   claim/expert record를 바로 이름으로 가리키는 경우도 있다. 아래 3번의
   guide/CLI에서 해당 근거를 조회한다.
3. `doctor`의 `resolved_root`를 사용한다. 공용 지식 스킬의 `guide_path`와
   `consumer_contract_path`를 먼저 읽고, 검토에 필요한 기술 근거만 CLI로
   질의한다. 경로와 domain 값은 `cli_entry_path`/`cli_domain_filter`를
   사용한다. shell 문자열을 조합하지 말고 인자 목록으로 다음 형태를 실행한다:

   ```sh
   python3 <resolved_root>/<cli_entry_path> consult \
     --query "<검토할 기술 질문>" --audience skill --purpose evidence \
     --consumer srs
   ```

   `SRS_NETWORK_KNOWLEDGE_DATA_ROOT`가 지정되면 동일 CLI에 `--data-root <경로>`를 전달한다. 버전/데이터 비호환을 legacy search 성공으로 대체하지 않는다.

   저수준 검색이 필요한 경우에만 `search --domain <cli_domain_filter>
   --query "<질문>"`을 사용한다. `cli_default_source_versions`가 비어 있으면
   source edition을 추측하지 않는다. leaf나 프로젝트 입력에 적용 edition이
   명시된 경우에만 `--source-version SOURCE_ID=VERSION`을 반복 전달한다.
   반환 JSON 전체를 task의 `output_path`와 같은 디렉터리에 근거 파일로 보존한다. 제출 JSON의
   `knowledge_evidence`에 파일의 절대 `path`와 원본 바이트의 `sha256`을 넣는다.
   controller는 이를 정식 artifact로 보존하고 이후 읽을 때 무결성을 확인한다.
   동일 release·질의·출처 버전·조건의 응답은 재사용할 수 있으나 적용성 판단은 별도다.
   `contract_version`은 1이어야 한다. NEEDS_SCOPE/CONFLICT/NO_EVIDENCE는 구조화된
   질의 결과이며 CLI 오류와 구분한다. `evidence_status`와 `review_state`를 별도로 확인한다.
   `expert_knowledge`, `consumer_guidance`, `retrieval_breakdown`, `documentation_lookup` 등
   추가 필드도 버리지 않는다. supporting_claim_refs와 reference_routes는 탐색 포인터이고,
   해당 edition으로 조회한 근거를 대신하지 않는다. QNX manual lookup의 OK는 제품 적용성
   또는 전체 evidence_status를 승격하지 않는다.
   반환 bundle의 `release`, `contract_version`, source/claim id, version,
   conditions, `required_actions`, `source_gaps`를 판정 근거에 함께 보존한다.
   expert guidance는 `normative_evidence: false` 경계를 유지하고 표준 evidence를
   이기지 않는다. sibling/guide/CLI가 없으면 캐시나 추측으로 대체하지 말고
   영향받는 rule을 `BLOCKED`로 반환하고 누락된 경로를 rationale에 적는다.
   근거 우선순위는 `domain-packs/<domain>/source-policy.yaml`을 따른다
   (CLI evidence > 적용성 서술).
4. 평가 범위는 manifest `input.dispatch_plan.entries`의
   `subject_type`/`evaluation_scope`/`member_uids`를 따른다. leaf 수나
   요청 대상 수로 추정하지 않는다. group target은 member 전체를 읽는다.
   `coverage-model.yaml`은 scope 정의를 확인할 필요가 있을 때만 읽는다.
5. `domain-packs/<domain>/parameter-policy.yaml` — 파라미터 값을 다루는 규칙일
   때 OBSERVED/NORMATIVE/근거 없는 TBD를 구분하는 기준.

## 판정 원칙

### 배치·replay·context 규칙

이 task는 leaf별 Subagent 호출이 아니라 한 axis/round의 bounded batch다.
`task manifest.input.candidate_leaves`는 이번 round의 전체 평가 후보이고,
`input.leaves`는 그중 이 task에서 실제로 fresh 평가할 leaf다.
`input.context_leaves`는 related/module/L2 비교를 위한 **읽기 전용** 파일이다.

- `input.dispatch_plan.entries`의 `role: target` 항목만 평가한다.
- 각 target/group의 `fresh_rule_ids`마다 decision을 하나씩 반환한다.
  수행하지 못한 규칙도 BLOCKED와 사유로 남긴다. `replay_rule_ids`는 controller가 PASS stamp에서
  병합하므로 Subagent가 다시 평가하거나 `source: replayed`로 만들지 않는다.
- `role: context` leaf는 내용을 읽어 target/group 판정의 비교·evidence로 사용할
  수 있지만 독립적인 `checks`, `leaf_evaluations`, verdict, stamp를 만들지 않는다.
- context leaf도 함께 수정해야 한다고 판단하면 `context_promotions`에만
  요청한다. 요청은 현재 task의 `role: context` leaf에 한정하고, 실제 재평가는
  controller가 `*-pN` follow-up bounded batch를 만들어 수행한다. 다음 task에서
  promoted leaf는 일반 target처럼 fresh 평가한다.
- replay 여부, stamp 유효성, 대상 scope 확장은 Subagent가 판단하지 않는다.
  요청 범위 밖 leaf를 임의로 추가하거나 자동으로 평가하지 않는다.
- `input.dispatch_plan.unavailable_evaluations`에 있는 `(subject, rule)`은
  제어기가 **디스패치하지 못한** 평가다(예: module/L2 scope 규칙인데 그
  group의 member leaf가 이번 요청 범위에 전부 들어오지 않음). 이 rule들은
  `required_checks`에는 들어 있으나 대응하는 `role: target` 엔트리가 없다.
  각 항목을 그 `subject_type`/`subject_key`/`rule_id`/`reason` 그대로
  controller가 정식 결과의 `not_evaluated`에 보존한다. 다른 leaf에 끼워 넣어(anchoring) 판정을
  통과시키지 않는다 — 그렇게 하면 stamp가 엉뚱한 subject에 남아 다음 라운드에
  재사용되지 않고, 판정 근거도 거짓이 된다. 임의로 PASS를 주지도 않는다.
- **`changed_member_uids`가 있는 group target은 판정 범위만 좁힌다.**
  module/L2 scope 규칙의 `role: target` 엔트리에 이 키가 있으면, 그것은
  지난 라운드 PASS 이후 **내용이 실제로 바뀐 member의 목록**이다. 이때도
  **`member_uids` 전부를 읽는다** — semantic duplication 같은 규칙은 형제
  전체를 봐야 한 leaf의 중복 여부를 알 수 있으므로, 읽기 범위를 좁히면
  판정 자체가 불가능해진다. 좁히는 것은 **다시 판정할 대상**뿐이다:
  바뀐 member가 (a) 자기들끼리, (b) 바뀌지 않은 나머지 member와 새로운
  위반을 만들었는지만 본다. 바뀌지 않은 member끼리의 관계는 지난 라운드에
  이미 PASS로 판정됐고 그 입력이 그대로이므로 다시 보지 않는다.
  `rationale`에 어느 member를 다시 판정했는지 명시한다. 이 키가 **없으면**
  group 전체를 처음부터 판정한다.

- **AI가 배정된 도메인 규칙을 의미적으로 판단한다** — 체크리스트 문구를 키워드로만
  매칭해 기계적으로 PASS/FAIL을 정하지 않는다. leaf 본문을 읽고 실제로 그
  규칙이 다루는 결함이 있는지 판단한다.
- **기술적 결론이 여러 근거 사이에서 충돌하면** source-policy.yaml의 우선순위를
  따르고, 그래도 판단이 서지 않으면 `verdict: BLOCKED`로 보고한다. PASS/FAIL
  중 하나로 임의 확정하지 않는다.
- **CLI 상태를 성공으로 뭉개지 않는다** — `status` 또는 `evidence_status`가
  `NEEDS_SCOPE | CONFLICT | NO_EVIDENCE`이면 영향받는 rule을 `BLOCKED`로
  반환하고 `required_actions`/충돌/공백을 rationale에 남긴다. `status: OK`도
  `evidence_status`, `review_state`, 각 evidence의 `applies_to`/conditions를
  확인하기 전에는 PASS 근거가 아니다. `status: ERROR`, exit code 2, JSON
  파싱 실패, 미지원 `contract_version`은 task `execution_status: ERROR`,
  `quality_verdict: BLOCKED`로 보고한다.
- **OBSERVED는 자동으로 NORMATIVE로 승격되지 않는다** — parameter-policy.yaml
  참고. leaf가 표준 인용 없이 관찰값만 제시하면서 그것을 표준처럼 서술하면
  위반 후보다.
- **group 평가를 단일 leaf 평가로 바꾸지 않는다.** 필요한 member가 누락되면
  해당 group/rule을 BLOCKED로 남긴다. leaf가 여러 개 있다는 이유만으로
  group 근거가 완전하다고 가정하지 않는다.
- **적용 제외(applicability exclusion)를 남용하지 않는다** — 어떤 rule_id를
  "이 leaf에는 적용 안 됨"으로 제외하려면 근거를 `rationale`에 구체적으로
  남긴다. domain-packs의 `applicability.default`는 fail-safe(전부 적용)이므로,
  예외를 선언하는 쪽이 입증 책임을 진다.

## 심각도 (severity)

이 축의 `severity`는 `CRITICAL | MAJOR | MINOR | INFO` 중 하나다.
로컬 체크리스트의 해당 category `Severity` 기준을 적용한다.
`local_rule_meta_path`는 scope·적용성 정보이며 severity 표가 아니다. 외부 표준의 SHALL 표현으로 심각도를 새로 추정하지 않는다. 심각도 기준이 없거나
상충하면 해당 tuple을 BLOCKED로 이유와 함께 남긴다.

`policies/quality-gate.yaml`의 `blocking_severities`(현재 `[CRITICAL, MAJOR]`)가
어떤 severity가 gate를 막는지 정한다 — 이 문서는 그 정책을 바꾸지 않는다,
이 Subagent는 사실을 보고할 뿐 gate 판정은 `scripts/runtime/gate.py`가 한다.

## 반환 형식

[공통 검토 출력 계약](../references/task-execution.md#검토-출력)을 따른다.
`location`에는 대상 uid와 section 또는 frontmatter 필드를 적는다.
도메인 축의 `severity`는 해당 규칙의 심각도를 따른다.


Original source: domain-packs/someip/srs-review-checklist.md

<!--
domain-packs/someip/srs-review-checklist.md — this project's own
SRS-review rubric for the someip domain (review-dispatch machinery, not
domain knowledge; see domain.yaml for the ownership model).

scripts/runtime/review_planner.py reads this file directly (via
domain.yaml's local_checklist_path) to extract the CHK-NNN rule ids that
become a review-domain task's required_checks. Same shape as
domain-packs/ethernet/srs-review-checklist.md.
-->

# SRS Checklist — Vehicle SOME/IP

<!-- schema_version: someipreq.checklist.v1 -->
<!-- rule_id_pattern: CHK-NNN (3-digit zero-padded) -->

9 review categories, 35 stable rules (CHK-001–CHK-035; no unused numbering gaps).
This file is the **single domain rubric** `agents/domain-reviewer.md` applies — categories, rules,
how to detect each, and the severity to assign. Apply each rule to the target SRS, basing every
judgment on the shared network-domain-knowledge sibling skill's SOME/IP guide,
CLI evidence (`domain.yaml`의 source_skill CLI 계약), and non-normative expert guidance.

출력은 manifest의 `output_contract`와 공통 task 실행 계약을 따른다.
`CHK-NNN`은 manifest의 `SOMEIP-CHK-NNN`에 대응한다. 배정된 fresh tuple만
`decisions`로 한 번씩 반환하며 provenance와 미배정 항목은 controller가 구성한다.
근거 문서·절·claim ID와 판단 사유는 `rationale`, 위반 leaf 원문은 `evidence`에 쓴다.
체크리스트의 Detect/Severity는 판단 기준이며 별도 출력 필드를 요구하지 않는다.

## SRS level boundary (ASPICE SWE.1 → SWE.2)

SRS states externally observable software behavior, interface contract, constraints, and
verification-relevant outcomes. It does not prescribe the design mechanism used to realize them.
Caller-thread versus dispatcher-thread selection, queue/callback/lock/priority strategy, process or
binary decomposition, API/function/configuration names, socket/IPC/OS/vendor details, and
pseudo-code belong in SAD/SDD.

When execution context affects the external contract, SRS may state only the observable constraint:
for example delivery ordering, re-entrancy, concurrent-call behavior, deadline, loss/duplication
behavior, or fault response. The implementation mechanism remains a SAD/SDD decision. Use
`layering` / `CHK-035` for HOW leakage; do not manufacture a missing thread-model finding.

> **Scope of this file**: SOME/IP **technical-axis** rules only. Domain-agnostic authoring quality
> (atomicity, unambiguity, completeness, …) is handled separately and is not restated here.
> The `layering` category is a deliberate cross-cutting exception: it prevents this domain rubric
> from turning design mechanisms into SRS obligations.

**How to read each category below**: the `[ ] **CHK-NNN**` lines are the rules (machine-parsed).
The **Detect / Severity / Scope** notes under a category tell the reviewer how to surface and grade a
violation. Per-category `scope` (item / module) is assigned by `rule-meta.yaml` (this same
domain-pack directory, local).

---

## 1. `service_lifecycle`

Full Offer / Find / Subscribe / Unsubscribe lifecycle covered.

- [ ] **CHK-001**: Offer: Initial Wait Phase, Repetition Phase, Main Phase parameters named
- [ ] **CHK-002**: Find: trigger condition + retry policy
- [ ] **CHK-003**: Subscribe (EventGroup): TTL, ACK timeout, NACK handling
- [ ] **CHK-004**: Unsubscribe: graceful (StopOffer/StopSubscribe) + ungraceful (TTL expiry, link loss)
- [ ] **CHK-005**: State transitions explicit (no "service is offered when ready")

**Detect**: a Subscribe-describing item without an explicit TTL plus ACK/NACK handling and a
project-selected bounded waiting/retry policy is incomplete. Do not invent a fixed millisecond
timeout from the protocol source. An Unsubscribe path that only states the graceful
case (no TTL-expiry / link-loss handling) is the same anti-pattern.
**Severity**: required lifecycle element absent (module-confirmed) → `CRITICAL`; Subscribe/Unsubscribe
timeout unspecified → `MAJOR`.
**근거 (`rationale`)** required (doc + topic name, CLI로 조회한 근거, e.g. `SOME/IP-SD PRS, Service Lifecycle`).

## 2. `communication_patterns`

All three patterns enumerated with semantics.

- [ ] **CHK-006**: **Method**: Request-Response (timeout + error response codes)
- [ ] **CHK-007**: **Method (Fire & Forget)**: explicit no-response semantics
- [ ] **CHK-008**: **Event**: Notification semantics (push), TTL behavior on subscribe
- [ ] **CHK-009**: **Field**: Getter / Setter / Notifier triplet (specify which apply per Field)
- [ ] **CHK-010**: No conflation of Method-Response with Event

**Detect**: a state with both query (Method-style) and push (Event-style) semantics described as two
separate items rather than one Field with Getter+Notifier is a Field-model candidate, not automatically
a protocol violation; confirm intended semantics before finding.
**Severity**: a required pattern's semantics entirely absent → `MAJOR`; Method/Event conflation
(Field candidate) → `MAJOR` (suggest merge into a Field — see also category 8).
**근거 (`rationale`)** required (doc + topic name, CLI로 조회한 근거, e.g. `SOME/IP PRS, Field semantics`).

## 3. `error_handling`

Every fault mode has a handler.

- [ ] **CHK-011**: Subscribe timeout / NACK
- [ ] **CHK-012**: Service unavailable (Offer expired)
- [ ] **CHK-013**: Deserialization failure (malformed payload)
- [ ] **CHK-014**: Wrong message ID / wrong service ID
- [ ] **CHK-015**: Timeout per Method call (request-side timeout)

**Detect**: each error path needs a named handler — Subscribe bounded-wait expiry/NACK,
Offer-expired unavailability, malformed-payload
deserialization failure, wrong message/service ID, and a per-Method request-side timeout.
**Severity**: missing handler for an error the item itself implies → `MAJOR`; no handler at all for a
fault mode the protocol mandates (e.g. Method timeout) → `CRITICAL`.

## 4. `service_discovery`

SD parameters explicit.

- [ ] **CHK-016**: Initial Wait Phase delay
- [ ] **CHK-017**: Repetition Phase: max repetitions + base delay
- [ ] **CHK-018**: Main Phase cyclic offer interval
- [ ] **CHK-019**: TTL on Offer / Subscribe entries
- [ ] **CHK-020**: Multicast vs Unicast SD endpoint handling

**Detect**: an SD section that says "the service is offered repeatedly" without naming
`REPETITIONS_MAX` / `REPETITIONS_BASE_DELAY` (with doubling) / `INITIAL_DELAY_MIN`/`MAX` /
`CYCLIC_OFFER_DELAY` is incomplete.
**Severity**: an SD parameter entirely absent (module-confirmed) → `MAJOR`; a bare "TBD" with no
standard/observed-value basis → treat per `parameter-policy.yaml` (config_completeness-equivalent
finding).
**근거 (`rationale`)** required (doc + topic name, CLI로 조회한 근거, e.g. `SOME/IP-SD PRS, SD state machine`).

## 5. `serialization`

Type / endian / padding rules at SRS level (rule statement, not byte offsets).

- [ ] **CHK-021**: Endian convention (big-endian per SOME/IP PRS, but state it)
- [ ] **CHK-022**: Struct padding rules (none, alignment-based)
- [ ] **CHK-023**: String encoding (UTF-8 / UTF-16) and length-prefix
- [ ] **CHK-024**: Variant / Union semantics if used
- [ ] **CHK-025**: Optional fields encoding

**Detect**: serialization described without naming the configured payload byte order, or implicitly
assuming host endianness, is incomplete. SOME/IP header and serialization control fields use
big-endian; payload parameter byte order follows applicable configuration/evidence and must not be
inferred from the header alone.
**Severity**: endian convention unstated → `MAJOR`; standard contradicted (e.g. little-endian claimed
with no override rationale) → `CRITICAL`.
**근거 (`rationale`)** required (doc + topic name, CLI로 조회한 근거, e.g. `SOME/IP PRS, Serialization rules`).

## 6. `application_interface`

Provider / Consumer interface requirements explicit as capabilities and externally observable
behavior, not vendor signatures or design mechanisms.

- [ ] **CHK-026**: Request completion semantics (synchronous / deferred) when externally observable
- [ ] **CHK-027**: Observable delivery contract (ordering / re-entrancy / concurrent calls / deadline) when required
- [ ] **CHK-028**: Error code propagation (return code / exception / future)
- [ ] **CHK-029**: No vsomeip API name leakage

**Detect**: an item naming a vsomeip C++ API call (`vsomeip::application::register_message_handler()`,
`vsomeip::runtime::get()`, ...) where only the capability belongs — replace it with the capability
it expresses. An item may
state externally observable completion or delivery behavior when the interface requires it; absence
of a caller-thread / dispatcher-thread design choice is not a finding. A requirement that
prescribes a concrete thread, dispatcher, queue, lock, priority, process, or IPC mechanism is
evaluated under `layering` / `CHK-035`, not here. Application business behavior, middleware routing,
endpoint selection, serialization invocation, and SD lifecycle ownership must remain distinct. For a multi-process deployment, review externally observable isolation and
peer-failure behavior only; do not require a Routing-Domain or IPC implementation mechanism in SRS.
**Severity**: vsomeip API name in body → `CRITICAL`; Routing Manager/Application responsibility
blur or an explicitly required but missing observable interface contract → `MAJOR`.

## 7. `transport_layer`

TCP vs UDP rationale documented.

- [ ] **CHK-030**: Selection criteria stated (latency / reliability / frame size)
- [ ] **CHK-031**: SOME/IP-TP segmentation when payload > MTU
- [ ] **CHK-032**: Per-method or per-service transport policy

**Detect**: a service specified to use TCP/UDP with no project rationale, or UDP for a stream that
exceeds the selected path MTU without an applicable segmentation strategy, is incomplete.
**Severity**: transport chosen with no rationale → `MAJOR`; payload exceeds MTU with no SOME/IP-TP
segmentation stated → `CRITICAL`.
**근거 (`rationale`)** required (doc + topic name, CLI로 조회한 근거, e.g. `SOME/IP-TP PRS, Segmentation
header format`).

## 8. `semantic_duplication`

No two items describe the same behavior with different wording. `module`-scope check.

- [ ] **CHK-033**: Search for paired items differing only in synonym or scope (e.g., "link goes down" vs "link transitions to inactive state")
- [ ] **CHK-034**: Method + Field overlap check (state with both query and push semantics → should be a single Field with Getter+Notifier, not separate Method+Event)

**Detect**: build a behavior-paraphrase index over the module's items — high lexical overlap +
the same parameters but distinct IDs → `MAJOR` (suggest merge). A separate Method + Event pair that
semantically forms one Field is a merge candidate after confirming the intended state semantics
(see also category 2's CHK-010).
**Scope**: manifest의 group target과 member 전체를 사용한다. 필요한 member가
누락되면 배정된 규칙을 `BLOCKED`로 반환한다. 미배정 tuple은 controller가 기록한다.

## 9. `layering`

SRS states externally observable WHAT. Design mechanism belongs in SAD/SDD.

- [ ] **CHK-035**: No implementation-mechanism prescription in normative SRS text

**Detect**: flag normative body text that prescribes or names a concrete implementation mechanism,
including caller/dispatcher thread selection, callback or queue choice, lock/mutex strategy,
priority, process/binary decomposition, API/function/configuration names, socket/IPC/OS/RTOS/vendor
details, register or memory layout, or pseudo-code. The example
"the notification shall be delivered on the caller thread or a dedicated dispatcher thread selected
by build-time interface configuration" is a HOW statement and fails this rule. Replace it with the
externally observable requirement, if one exists: ordering, re-entrancy, concurrent-call behavior,
deadline, loss/duplication behavior, or fault response. Text in `## Notes` that explicitly labels a
mechanism as forbidden is not itself a finding.
**Severity**: concrete implementation mechanism in normative body → `CRITICAL`; an item whose
normative body is predominantly design prescription → `CRITICAL` (section-level).
**근거 (`rationale`)**: `ASPICE SWE.1/SWE.2 work-product boundary; implementation mechanism belongs
to SAD/SDD`.

---

## 결과와 인용

PASS도 배정된 rule과 subject의 평가를 반환한다. 근거 없는 통과나 빈 verdict
목록으로 대체하지 않는다. FAIL은 leaf 원문의 연속된 부분 문자열을 `evidence`로
쓰고, 외부 기술 근거는 `rationale`에 문서·버전·절 또는 CLI claim ID로 남긴다.
해당 근거를 확인하지 못하면 추측하지 않고 BLOCKED/미평가 사유를 보고한다.
