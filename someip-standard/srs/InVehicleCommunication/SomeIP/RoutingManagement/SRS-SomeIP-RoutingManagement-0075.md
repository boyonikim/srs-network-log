---
uid: SRS-UID-d1038ac62015
id: SRS-SomeIP-RoutingManagement-0075
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: SD State Machine Initial State
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter:
- uid: SRS-UID-dec119b739b5
  cb_id: 38210984
related_items:
  - SRS-SomeIP-RoutingManagement-0002
  - SRS-SomeIP-RoutingManagement-0034
  - SRS-SomeIP-RoutingManagement-0094
  - SRS-SomeIP-ServiceDiscovery-0003
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 power-on 시 SD 상태 머신을 Initial Wait Phase 진입 전 상태로 리셋하여야 한다.

SOME/IP Routing Management 소프트웨어는 Initial Wait Phase에 진입할 때마다(리셋 이후 최초 진입 포함) {P_SD_InitialDelay_Min}을 {P_SD_InitialDelay_Max} 이하로 하는 범위 내에서 균등 분포 난수로 선택한 지연을 적용하여야 한다.

## Notes
