---
uid: SRS-UID-9a3974fd07b5
id: SRS-SomeIP-ServiceDiscovery-0050
cb_id: 40438696
domain: someip
parent: SRS-UID-88c1c630dd53
title: Subscription Rejection Notification
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0049
- SRS-SomeIP-ServiceDiscovery-0002
- SRS-SomeIP-ServiceDiscovery-0008
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 service provider로부터 SubscribeEventGroupNack을 수신하면 해당 subscription 요청이 거부되었음을 application에 통지하여야 한다.

## Notes
