---
uid: SRS-UID-2a1cbfe4b279
id: SRS-SomeIP-ServiceDiscovery-0081
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: SD Endpoint Transport Protocol
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0078
- SRS-SomeIP-RoutingManagement-0048
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 SD endpoint(multicast 및 unicast 모두)에서 UDP transport를 사용하여야 하며, SD 메시지는 지연 시간이 짧은 주기적 announcement 성격을 가지므로 TCP connection 수립 지연을 피하기 위해 UDP를 사용한다. 이 UDP 고정 선택은 SD 제어 메시지(OfferService/FindService/SubscribeEventgroup/StopOfferService 등 SD entry)에만 적용되며, service/method 단위 실제 데이터 payload의 TCP/UDP 선택은 related_items에 정의된 RoutingManagement transport policy를 따른다.

## Notes
