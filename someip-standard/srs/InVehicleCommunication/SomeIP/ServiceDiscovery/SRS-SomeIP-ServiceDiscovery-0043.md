---
uid: SRS-UID-65d3890c8401
id: SRS-SomeIP-ServiceDiscovery-0043
cb_id: 38285357
domain: someip
parent: SRS-UID-88c1c630dd53
title: SubscribeEventGroupAck Transmission
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 consumer로부터 SubscribeEventGroup entry를 수신하여 구독을 수락하는 경우 해당 consumer에게 SubscribeEventGroupAck을 전송하여야 한다. 구독을 수락하지 않는 경우에는 해당 consumer에게 SubscribeEventGroupAck을 전송하여서는 안 된다.
## Notes
