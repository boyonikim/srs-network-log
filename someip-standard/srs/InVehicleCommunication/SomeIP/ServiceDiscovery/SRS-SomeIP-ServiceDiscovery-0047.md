---
uid: SRS-UID-08e7228197cf
id: SRS-SomeIP-ServiceDiscovery-0047
cb_id: 40438694
domain: someip
parent: SRS-UID-88c1c630dd53
title: Subscription Request Timeout
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0045
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 SubscribeEventGroup 요청을 전송한 후 service provider로부터 SubscribeEventGroupAck 또는 SubscribeEventGroupNack을 수신하지 않은 상태에서 재시도가 모두 소진되면 해당 subscription 요청을 timeout으로 종료하여야 한다.

## Notes
