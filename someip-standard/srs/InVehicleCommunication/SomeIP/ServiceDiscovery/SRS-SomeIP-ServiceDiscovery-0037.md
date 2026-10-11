---
uid: SRS-UID-015c9a147431
id: SRS-SomeIP-ServiceDiscovery-0037
cb_id: 38210988
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Subscription Creation
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0038
- SRS-SomeIP-ServiceDiscovery-0043
- SRS-SomeIP-ServiceDiscovery-0035
- SRS-SomeIP-ServiceDiscovery-0119
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 consumer로부터 정상 파싱한 SubscribeEventGroup 요청의 Service ID 및 Instance ID가 해당 provider가 제공 중인 service instance와 일치하고 EventGroup ID가 해당 service instance에서 지원하는 EventGroup을 식별하며 Service ID, Instance ID, EventGroup ID 및 TTL 값이 모두 허용 범위 내이고 해당 provider가 구독을 수락한 경우, 해당 EventGroup에 대한 subscription을 생성하여야 한다.

SOME/IP Service Discovery 기능은 신규 subscription 생성 여부를 판단할 때 Service ID의 허용 범위를 0x0001~0xFFFE, Instance ID의 허용 범위를 0x0001~0xFFFE, EventGroup ID의 허용 범위를 0x0001~0xFFFF, TTL의 허용 범위를 0x000001~0xFFFFFF로 적용하여야 한다.
## Notes
