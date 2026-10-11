---
uid: SRS-UID-c0161cfccccd
id: SRS-SomeIP-RoutingManagement-0056
cb_id: 40610555
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Re-registration After Network Interface Restart
status: Specified
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

SOME/IP Routing Management 소프트웨어는 PHY link-up 상태가 유지된 상태에서 감지된 Network Interface 재시작에 따라 기존 SOME/IP 통신 자원의 해제가 완료되면 재시작 직전까지 등록 상태였던 모든 service를 재시작 이전과 동일한 service ID로 재등록하여야 한다.
SOME/IP Routing Management 소프트웨어는 각 대상 service의 등록 상태가 등록 없음에서 등록 완료로 전환된 시점을 해당 service의 재등록 완료로 판정하여야 한다.

SOME/IP Routing Management 소프트웨어는 기존 SOME/IP 통신 자원의 해제가 완료되기 전에는 service 재등록을 수행하지 않아야 한다.

## Notes

Service discovery 재개는 SRS-SomeIP-RoutingManagement-0074에서 규정한다.
