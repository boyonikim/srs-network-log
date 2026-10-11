---
uid: SRS-UID-6f3b094b82cc
id: SRS-SomeIP-RoutingManagement-0058
cb_id: 40610543
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Expiry on Link Loss or TTL Expiry
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0092
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 Ethernet interface fault가 발생했음을 나타내는 상태 변화 이벤트 수신 시점에 link loss 또는 TTL expiry가 감지되어 StopOffer 및 StopSubscribe를 전송할 수 없으면 해당 offer 및 subscription을 만료 처리하고 Unsubscribe를 수행하여야 한다. 이 만료 처리는 StopOffer/Unsubscribe 전송 가능 시의 종료 절차와 서로 배타적인 조건(StopOffer/StopSubscribe 전송 불가 시)에만 적용되는 별도 경로다.

여기서 StopOffer는 service offer 중단을 위한 SD 엔트리를, StopSubscribe는 해당 service의 EventGroup 구독 취소를 위한 TTL=0 SD 엔트리를 가리키며, 둘은 서비스 제공 중단과 구독 취소라는 서로 다른 절차다.

## Notes

StopOffer/Unsubscribe 전송 가능 시의 종료 절차는 SRS-SomeIP-RoutingManagement-0062에서 규정한다.


