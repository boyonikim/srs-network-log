---
uid: SRS-UID-fecdb8a9b7eb
id: SRS-SomeIP-ServiceDiscovery-0074
cb_id: 40594164
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Notification Unicast Fallback
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0029
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 multicast 전송 조건을 만족하는 EventGroup에 multicast endpoint가 구성되어 있지 않은 경우 각 subscriber(consumer)의 unicast endpoint로 notification을 전송하여야 한다.

## Notes
