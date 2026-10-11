---
uid: SRS-UID-5456b224cc0d
id: SRS-SomeIP-ServiceDiscovery-0035
cb_id: 40438685
domain: someip
parent: SRS-UID-88c1c630dd53
title: SubscribeEventGroupNack on Subscriber Limit
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_MaxSubscribers
  type: uint16
  range: 1~512
  unit: count
  default: '64'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0034
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 동시 subscriber(consumer) 수가 {P_SD_MaxSubscribers}에 도달한 상태에서 consumer로부터 신규 SubscribeEventGroup 요청을 수신하면 해당 consumer에게 SubscribeEventGroupNack을 반환하여야 한다.

## Notes
