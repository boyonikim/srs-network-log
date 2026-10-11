---
uid: SRS-UID-4512c6aad481
id: SRS-SomeIP-ServiceDiscovery-0041
cb_id: 38285365
domain: someip
parent: SRS-UID-88c1c630dd53
title: Persistent Subscription Handling
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0066
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 consumer로부터 수신한 SubscribeEventGroup entry의 TTL이 0xFFFFFF인 경우 해당 consumer의 EventGroup subscription을 service provider의 다음 reboot까지 유효한 상태로 유지하여야 한다.

## Notes
