---
uid: SRS-UID-f5fba0ccc640
id: SRS-SomeIP-ServiceDiscovery-0110
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: Persistent Subscription Renewal Exception
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_SubRenewalRatio
  type: uint8
  range: 50~90
  unit: percent
  default: '75'
mapped_parameter: []
related_items: []
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 TTL이 0xFFFFFF인 subscription에 대해서는 갱신을 위한 SubscribeEventGroup 재전송을 수행하지 않아야 한다.

## Notes

