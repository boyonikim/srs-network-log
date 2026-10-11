---
uid: SRS-UID-2fa8bcb446e7
id: SRS-SomeIP-ServiceDiscovery-0099
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: SubscribeEventGroupAck Suppression
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

SOME/IP Service Discovery 기능은 SubscribeEventGroup entry를 수신하였으나 해당 구독을 수락하지 않는 경우 해당 consumer에게 SubscribeEventGroupAck을 전송하지 않아야 한다.

## Notes

