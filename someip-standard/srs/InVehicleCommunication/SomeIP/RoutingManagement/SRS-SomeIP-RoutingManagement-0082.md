---
uid: SRS-UID-911e12e10da6
id: SRS-SomeIP-RoutingManagement-0082
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Middleware Initialization Completion Event Suppression Before Readiness
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0061
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 초기화 완료 상태가 설정되지 않은 경우 application에 미들웨어 초기화 완료 이벤트를 통지하여서는 안 된다.

## Notes

