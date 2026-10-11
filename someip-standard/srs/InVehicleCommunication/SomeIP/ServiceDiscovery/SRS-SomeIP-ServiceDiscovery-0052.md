---
uid: SRS-UID-3fa18d66c2e8
id: SRS-SomeIP-ServiceDiscovery-0052
cb_id: 40438688
domain: someip
parent: SRS-UID-88c1c630dd53
title: Subscriber Removal on StopSubscribeEventGroup
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0051
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 consumer로부터 StopSubscribeEventGroup message를 수신한 경우 해당 consumer를 활성 subscriber 목록에서 제거하여야 한다.

## Notes
