---
uid: SRS-UID-aadbffd4c099
id: SRS-SomeIP-RoutingManagement-0006
cb_id: 38285340
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Re-registration Handling After Abnormal Termination
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---

## Description

SOME/IP Routing Management 소프트웨어는 비정상 종료 후 재시작 완료 시, 재연결하는 local application으로부터 재수신되는 service 등록 요청을 신규 service 등록 요청으로 수용하여 service 등록 절차를 개시하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 재연결 완료 후 재등록 요청이 수신되지 않은 service의 등록 상태를 등록 없음 상태로 유지하여야 한다.

## Notes
