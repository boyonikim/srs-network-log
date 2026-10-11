---
uid: SRS-UID-e3771e8b9bb2
id: SRS-SomeIP-ServiceDiscovery-0029
cb_id: 38285355
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Notification Transport Mode Selection
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
spec_pattern_type: data_logic
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 EventGroup notification publication 시 {P_SD_MulticastThreshold} 및 subscriber(consumer) 수에 따라 notification 전송 방식을 선택하여야 한다. {P_SD_MulticastThreshold}가 0이면 모든 subscriber(consumer)에게 notification을 unicast로 전송하고, {P_SD_MulticastThreshold}가 0보다 크면 subscriber(consumer) 수가 {P_SD_MulticastThreshold} 미만일 때 unicast로 전송하며, subscriber(consumer) 수가 {P_SD_MulticastThreshold} 이상일 때 구성된 multicast endpoint로 전송하여야 한다.
## Notes
