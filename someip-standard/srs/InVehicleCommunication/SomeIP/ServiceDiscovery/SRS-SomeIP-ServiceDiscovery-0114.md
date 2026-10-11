---
uid: SRS-UID-4ed9027c76ae
id: SRS-SomeIP-ServiceDiscovery-0114
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Notification Transport Selection Basis
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

SOME/IP Service Discovery 기능은 구성된 notification transport policy에서 정의한 latency 및 reliability 요구조건을 충족하고 notification payload가 UDP MTU 이하인 경우 multicast notification 전송에 UDP를 사용하여야 한다.
SOME/IP Service Discovery 기능은 notification payload가 UDP MTU를 초과하여 segmentation이 필요한 경우 SOME/IP-TP Segmentation Protocol을 사용하여야 한다.

## Notes

