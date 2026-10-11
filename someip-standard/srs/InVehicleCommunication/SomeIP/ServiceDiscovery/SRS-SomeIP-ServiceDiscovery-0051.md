---
uid: SRS-UID-7c84033aa3ab
id: SRS-SomeIP-ServiceDiscovery-0051
cb_id: 38285358
domain: someip
parent: SRS-UID-88c1c630dd53
title: Subscriber Removal on Subscription Expiry
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 consumer로부터 수신한 SubscribeEventGroup entry의 TTL이 갱신 없이 만료된 경우 해당 consumer를 EventGroup의 활성 subscriber 목록에서 제거하여야 한다.

※ 예외 규칙: SOME/IP Service Discovery 기능은 SubscribeEventGroup entry의 TTL 만료 전에 동일 consumer로부터 해당 EventGroup에 대한 유효한 SubscribeEventGroup 갱신 entry를 수신한 경우 해당 consumer를 활성 subscriber 목록에서 제거하지 않아야 한다.

## Notes
