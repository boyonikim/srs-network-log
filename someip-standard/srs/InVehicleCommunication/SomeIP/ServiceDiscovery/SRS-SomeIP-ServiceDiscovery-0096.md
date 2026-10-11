---
uid: SRS-UID-0cd432dd7a47
id: SRS-SomeIP-ServiceDiscovery-0096
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Subscription Expiry Handling
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_Sub_TTL
  type: uint32
  range: 1~65535
  unit: s
  default: '3'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0037
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 SubscribeEventGroup entry의 TTL이 만료되면 해당 subscription을 유효한 상태로 유지하지 않아야 한다.

## Notes

