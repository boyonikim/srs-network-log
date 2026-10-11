---
uid: SRS-UID-b66e466d600e
id: SRS-SomeIP-ServiceDiscovery-0107
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: Initial Event Subscription TTL Handling
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0037
- SRS-SomeIP-ServiceDiscovery-0077
spec_pattern_type: data_logic
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 initial event 요청을 위한 SubscribeEventGroup entry에 설정된 {P_SD_Sub_TTL} 값을 TTL 필드에 포함하여야 한다.

## Notes

