---
uid: SRS-UID-fd373ea06c04
id: SRS-SomeIP-ServiceDiscovery-0086
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: Invalid SubscribeEventGroup Request Handling
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0038
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 Service ID, Instance ID, EventGroup ID 또는 TTL 값이 허용 범위를 벗어난 SubscribeEventGroup 요청을 수신하면 해당 EventGroup subscription을 생성하지 않아야 한다.

## Notes

