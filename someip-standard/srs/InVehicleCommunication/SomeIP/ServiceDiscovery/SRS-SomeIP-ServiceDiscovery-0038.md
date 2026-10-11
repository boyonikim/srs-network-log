---
uid: SRS-UID-067cce3cf4d4
id: SRS-SomeIP-ServiceDiscovery-0038
cb_id: 40447519
domain: someip
parent: SRS-UID-88c1c630dd53
title: Invalid SubscribeEventGroup Handling
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
- SRS-SomeIP-ServiceDiscovery-0088
- SRS-SomeIP-ServiceDiscovery-0089
- SRS-SomeIP-ServiceDiscovery-0119
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 정상 파싱한 SubscribeEventGroup 요청의 신규 subscription 생성 여부를 판단할 때 Service ID의 허용 범위를 0x0001~0xFFFE, Instance ID의 허용 범위를 0x0001~0xFFFE, EventGroup ID의 허용 범위를 0x0001~0xFFFF, TTL의 허용 범위를 0x000001~0xFFFFFF로 적용하여야 한다.
SOME/IP Service Discovery 기능은 Service ID 또는 Instance ID가 미할당 값 0x0000 또는 wildcard 값 0xFFFF이면 특정 subscription 대상의 식별 값으로 허용하지 않아야 한다.
SOME/IP Service Discovery 기능은 service provider가 TTL이 0x000001~0xFFFFFF인 SubscribeEventGroup 요청을 정상 파싱하였을 때 Service ID, Instance ID 또는 EventGroup ID가 허용 범위를 벗어나는 경우, Service ID 및 Instance ID가 해당 provider가 제공 중인 service instance와 일치하지 않는 경우, EventGroup ID가 해당 service instance에서 지원하는 EventGroup을 식별하지 못하는 경우 중 하나에 해당하면, 해당 EventGroup subscription을 생성하지 않고 해당 consumer에게 SubscribeEventGroupNack을 전송하여야 한다.
SOME/IP Service Discovery 기능은 정상 파싱한 SubscribeEventGroup entry의 TTL 값 중 0x000001~0xFFFFFE를 유한 유효기간 값으로, 0xFFFFFF를 무한 유효기간 값으로 인정하고 이 값 자체를 신규 subscription 생성 범위 위반으로 판정하여서는 안 된다.

SOME/IP Service Discovery 기능은 식별 값이 허용 범위 내이고 TTL이 0x000000인 SubscribeEventGroup 요청을 수신하면 이를 정상 StopSubscribeEventGroup 요청으로 해석하고 신규 subscription을 생성하지 않으며 TTL이 0이라는 이유로 SubscribeEventGroupNack을 전송하지 않아야 한다.
## Notes
