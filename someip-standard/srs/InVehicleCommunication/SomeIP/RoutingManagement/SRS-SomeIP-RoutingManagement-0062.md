---
uid: SRS-UID-b77efffe27e3
id: SRS-SomeIP-RoutingManagement-0062
cb_id: 40610553
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: EventGroup Termination On Link Loss Or TTL Expiry
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0092
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 StopOffer 및 StopSubscribe 전송이 가능한 상태에서 link loss 또는 TTL expiry가 감지되면 해당 service offer 또는 subscription을 StopOffer 또는 Unsubscribe로 종료하여야 한다. 이 종료 절차는 StopOffer/StopSubscribe 전송 불가 시의 만료 처리와 서로 배타적인 조건(전송 가능 시)에만 적용되는 별도 경로다.

여기서 StopOffer는 service offer 중단을 위한 SD 엔트리를, StopSubscribe는 해당 service의 EventGroup 구독 취소를 위한 TTL=0 SD 엔트리를 가리키며, 둘은 서비스 제공 중단과 구독 취소라는 서로 다른 절차다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 link loss 또는 TTL expiry가 감지되지 않으면 상기 종료 동작을 수행하지 않아야 한다.

## Notes

StopOffer/StopSubscribe 전송 불가 시의 만료 처리는 SRS-SomeIP-RoutingManagement-0058에서 규정한다.


