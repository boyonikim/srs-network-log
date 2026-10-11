---
uid: SRS-UID-299c2c3e3a58
id: SRS-SomeIP-RoutingManagement-0036
cb_id: 40610535
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: FindService Start After Discovery Trigger
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0002
- SRS-SomeIP-RoutingManagement-0096
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 준비 완료 후 consumer의 service discovery 요청을 수신하면 FindService를 개시하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 준비 완료 전이거나 consumer의 service discovery 요청이 수신되지 않으면 FindService를 개시하지 않아야 한다.

## Notes
Ethernet link-up 지연 및 탐색 실패 재시도는 SRS-UID-d6ff734e0cea 요구사항에서 규정한다.
