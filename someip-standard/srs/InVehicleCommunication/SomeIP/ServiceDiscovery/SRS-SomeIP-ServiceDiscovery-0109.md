---
uid: SRS-UID-5e3b544c4217
id: SRS-SomeIP-ServiceDiscovery-0109
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Publication TTL Handling
status: Define
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
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 첫 SubscribeEventGroup 수락으로 시작한 notification publication을 해당 subscription의 TTL이 만료되기 전까지만 수행하여야 한다.

## Notes

