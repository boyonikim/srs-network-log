---
uid: SRS-UID-4e3a1171bae0
id: SRS-SomeIP-ServiceDiscovery-0113
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Notification Transport Policy Scope
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_MulticastThreshold
  type: uint8
  range: 0~255
  unit: count
  default: '0'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0074
- SRS-SomeIP-ServiceDiscovery-0075
- SRS-SomeIP-ServiceDiscovery-0081
- SRS-SomeIP-RoutingManagement-0048
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 {P_SD_MulticastThreshold} 기준을 EventGroup notification의 unicast/multicast 배포 대상 선택에만 적용하여야 하며, L4 transport(TCP/UDP) 자체의 선택 기준으로 사용하여서는 안 된다. EventGroup notification이 전달하는 실제 service/method 단위 payload의 TCP/UDP transport 선택과 SD 제어 메시지의 UDP 고정 사용은 관련 transport policy를 따라야 한다.

## Notes


