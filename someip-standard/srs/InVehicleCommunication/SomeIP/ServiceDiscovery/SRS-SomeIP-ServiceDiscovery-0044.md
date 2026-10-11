---
uid: SRS-UID-6e55455a0a49
id: SRS-SomeIP-ServiceDiscovery-0044
cb_id: 38285362
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Subscription Activation
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0045
- SRS-SomeIP-ServiceDiscovery-0049
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 service provider로부터 TTL 값이 0보다 큰 SubscribeEventGroupAck을 수신하면 해당 EventGroup subscription을 해당 Ack의 TTL 만료 전까지 활성화하여야 한다.

SOME/IP Service Discovery 기능은 SubscribeEventGroupNack을 수신하거나, 허용된 최초 전송 및 재전송 각각의 응답 대기 시간이 모두 만료될 때까지 SubscribeEventGroupAck 또는 SubscribeEventGroupNack을 수신하지 못하거나, TTL 값이 0인 SubscribeEventGroupAck을 수신한 경우 해당 EventGroup subscription을 활성화하지 않아야 한다.
## Notes
