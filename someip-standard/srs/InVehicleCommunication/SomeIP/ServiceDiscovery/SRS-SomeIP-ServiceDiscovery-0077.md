---
uid: SRS-UID-4b11e12b05ce
id: SRS-SomeIP-ServiceDiscovery-0077
cb_id: 40594159
domain: someip
parent: SRS-UID-88c1c630dd53
title: Initial Event Reception Timeout Notification
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0042
- SRS-SomeIP-ServiceDiscovery-0044
- SRS-SomeIP-ServiceDiscovery-0067
- SRS-SomeIP-ServiceDiscovery-0002
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 InitialDataRequested 플래그가 설정된 SubscribeEventGroup 요청에 대한 SubscribeEventGroupAck을 consumer가 수신한 후, 해당 SubscribeEventGroup entry의 TTL이 만료될 때까지 initial event를 수신하지 못하면 consumer application에 initial event 미수신을 통지하여야 한다.

## Notes
