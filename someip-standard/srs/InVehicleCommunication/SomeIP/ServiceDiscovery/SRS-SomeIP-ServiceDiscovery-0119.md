---
uid: SRS-UID-e450c4e03b0f
id: SRS-SomeIP-ServiceDiscovery-0119
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: Rejected Subscription Negative Acknowledgement
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0066
- SRS-SomeIP-ServiceDiscovery-0043
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 service provider가 subscription 요청을 수락하지 않으면 해당 consumer에게 SubscribeEventGroupNack을 전송하여야 한다.

## Notes

