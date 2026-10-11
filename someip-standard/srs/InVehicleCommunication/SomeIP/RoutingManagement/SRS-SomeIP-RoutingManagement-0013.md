---
uid: SRS-UID-dfbfc1b21529
id: SRS-SomeIP-RoutingManagement-0013
cb_id: 38285345
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: SOME/IP Communication Resource Release on Network Interface Restart
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_ChannelRelease_Timeout
  type: uint32
  range: 100~5000
  unit: ms
  default: '1000'
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

SOME/IP Routing Management 기능은 PHY link-up 상태가 유지된 상태에서 Network Interface 재시작을 감지하면 감지 시점부터 {P_ChannelRelease_Timeout} 이내에 기존 SOME/IP 통신 자원을 해제하여야 한다.

SOME/IP Routing Management 기능은 Network Interface 재시작 감지 시점부터 {P_ChannelRelease_Timeout}이 경과하였는데도 해제되지 않은 기존 SOME/IP 통신 자원이 있으면 해당 잔여 자원을 통신에 사용할 수 없는 상태로 처리하고 해제하여야 한다.

## Notes
