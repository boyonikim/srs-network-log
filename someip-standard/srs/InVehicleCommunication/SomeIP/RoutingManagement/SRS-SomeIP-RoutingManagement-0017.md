---
uid: SRS-UID-168afc4c4227
id: SRS-SomeIP-RoutingManagement-0017
cb_id: 40610528
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Suspension on Ethernet Interface Fault Detection
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_EthFault_ServiceSuspend_Timeout
  type: uint32
  range: 10~1000
  unit: ms
  default: '100'
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0058
- SRS-SomeIP-RoutingManagement-0062
- SRS-SomeIP-RoutingManagement-0092
- SRS-SomeIP-RoutingManagement-0093
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 Ethernet Fault Management 모듈로부터 Ethernet interface fault 발생 상태 변화 이벤트를 수신하면 수신 시점에 해당 link가 link-up 상태이고 해당 link의 service offer 및 subscription 식별 정보가 유지되어 StopOffer 및 StopSubscribe를 전송할 수 있는지를 정상 중단 조건으로 판단하여야 한다.
SOME/IP Routing Management 소프트웨어는 정상 중단 조건을 만족하면 이벤트 수신 시점부터 {P_EthFault_ServiceSuspend_Timeout} 이내에 StopOffer 및 StopSubscribe를 전송하여 해당 link에 바인딩된 서비스의 offer 및 subscription을 중단하여야 한다.

여기서 StopOffer는 service offer 중단을 위한 SD 엔트리를, StopSubscribe는 해당 service의 EventGroup 구독 취소를 위한 TTL=0 SD 엔트리를 가리키며, 둘은 서비스 제공 중단과 구독 취소라는 서로 다른 절차다.

SOME/IP Routing Management 소프트웨어는 이벤트 수신 시점부터 {P_EthFault_ServiceSuspend_Timeout} 이내에 StopOffer 및 StopSubscribe 전송을 완료하지 못하면, link loss 또는 TTL expiry 감지 여부에 따라 결정되는 별도의 만료 또는 종료 처리 경로를 적용하여야 한다.

## Notes
