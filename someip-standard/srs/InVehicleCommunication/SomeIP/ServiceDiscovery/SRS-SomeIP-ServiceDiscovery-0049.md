---
uid: SRS-UID-0ba532e83e72
id: SRS-SomeIP-ServiceDiscovery-0049
cb_id: 38285363
domain: someip
parent: SRS-UID-88c1c630dd53
title: Subscription Request Rejection
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0044
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 service provider로부터 SubscribeEventGroupNack을 수신하면 해당 EventGroup subscription 요청을 재전송 중단 및 subscription 미활성 상태로 종료하여야 한다.

## Notes
