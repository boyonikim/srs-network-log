---
uid: SRS-UID-bcb20d226ca4
id: SRS-SomeIP-ServiceDiscovery-0112
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Notification UDP Transport
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

SOME/IP Service Discovery 기능은 notification payload가 UDP MTU 이하이고 구성된 notification transport policy의 latency 및 reliability 요구조건을 충족하는 경우 multicast endpoint로의 전송에 L4 transport로 UDP를 사용하여야 한다.

## Notes

