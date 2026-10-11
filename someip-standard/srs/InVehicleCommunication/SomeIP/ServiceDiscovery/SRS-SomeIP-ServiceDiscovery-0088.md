---
uid: SRS-UID-7047ef12aaf5
id: SRS-SomeIP-ServiceDiscovery-0088
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: SubscribeEventGroup TTL Zero Handling
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0037
- SRS-SomeIP-ServiceDiscovery-0043
- SRS-SomeIP-ServiceDiscovery-0052
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 TTL 값이 0x000000인 SubscribeEventGroup 요청을 수신하면 이를 필드 값 범위 위반도 구조적 파손도 아닌 구독 중지 요청으로 처리하여야 하며, SubscribeEventGroupNack을 전송하지 않고 해당 consumer를 활성 subscriber 목록에서 제거하여야 한다.

## Notes
