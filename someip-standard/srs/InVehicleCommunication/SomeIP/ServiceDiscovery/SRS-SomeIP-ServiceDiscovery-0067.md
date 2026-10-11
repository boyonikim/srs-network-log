---
uid: SRS-UID-e32f32c8258c
id: SRS-SomeIP-ServiceDiscovery-0067
cb_id: 40466966
domain: someip
parent: SRS-UID-88c1c630dd53
title: Initial Event Transmission After Subscription Ack
status: Define
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

SOME/IP Service Discovery 기능은 service provider가 InitialDataRequested 플래그가 설정된 SubscribeEventGroup 요청을 수락하여 SubscribeEventGroupAck을 전송한 경우, 해당 SubscribeEventGroup entry의 TTL이 만료되기 전까지 해당 EventGroup에 속한 각 event의 최신 값을 SubscribeEventGroupAck 전송 이후에 해당 consumer의 unicast endpoint로 전송하여야 한다.

※ 예외 규칙: SOME/IP Service Discovery 기능은 해당 event의 최신 값이 존재하지 않는 경우 해당 event의 initial event를 전송하지 않아야 한다.

## Notes
