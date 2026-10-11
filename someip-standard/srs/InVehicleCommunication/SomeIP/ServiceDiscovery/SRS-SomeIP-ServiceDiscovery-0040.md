---
uid: SRS-UID-8132938cb9b6
id: SRS-SomeIP-ServiceDiscovery-0040
cb_id: 38285366
domain: someip
parent: SRS-UID-88c1c630dd53
title: Subscription TTL Timer Restart
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

SOME/IP Service Discovery 기능은 service provider가 consumer로부터 EventGroup subscription 갱신을 위한 SubscribeEventGroup entry를 수신하면, 해당 entry에 포함된 TTL 값으로 해당 consumer의 EventGroup subscription 만료 타이머를 재설정하여야 한다.

※ 예외 규칙: SOME/IP Service Discovery 기능은 EventGroup subscription 갱신을 위한 SubscribeEventGroup entry를 수신하지 않은 경우 해당 consumer의 EventGroup subscription 만료 타이머를 재설정하지 않아야 한다.

## Notes
