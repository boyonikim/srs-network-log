---
uid: SRS-UID-54c4d342d145
id: SRS-SomeIP-RoutingManagement-0057
cb_id: 40610538
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Internal State Cleanup After Unavailability Notification
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SvcCleanup_Timeout
  type: uint32
  range: 50~2000
  unit: ms
  default: '500'
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0016
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 service provider의 비정상 종료 또는 네트워크 연결 단절로 Service Unavailable 통지가 발생한 경우, 해당 통지 후 {P_SvcCleanup_Timeout}ms 이내에 해당 service의 내부 상태를 Service Unavailable 상태로 설정하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 {P_SvcCleanup_Timeout}ms 이내에 해당 service의 내부 상태를 Service Unavailable 상태로 설정하지 못하면, 설정을 완료할 때까지 해당 service를 Service Unavailable 상태로 간주하여야 한다.

## Notes
