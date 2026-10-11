---
uid: SRS-UID-659d73813109
id: SRS-SomeIP-RoutingManagement-0074
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Discovery Resumption After Network Interface Restart
status: Draft
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

SOME/IP Routing Management 기능은 PHY link-up 상태가 유지된 상태에서 감지된 Network Interface 재시작에 따라 기존 SOME/IP 통신 자원의 해제가 완료된 후 service discovery를 재개하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 기능은 기존 SOME/IP 통신 자원의 해제가 완료되기 전에는 service discovery 재개를 수행하지 않아야 한다.

## Notes
