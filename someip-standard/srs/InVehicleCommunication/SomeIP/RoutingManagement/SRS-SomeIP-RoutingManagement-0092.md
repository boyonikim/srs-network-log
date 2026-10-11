---
uid: SRS-UID-2f0f0d96b5a9
id: SRS-SomeIP-RoutingManagement-0092
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Ethernet Fault Service Termination Path Dispatch
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter:
- uid: SRS-UID-168afc4c4227
  cb_id: 40610528
related_items:
- SRS-SomeIP-RoutingManagement-0017
- SRS-SomeIP-RoutingManagement-0058
- SRS-SomeIP-RoutingManagement-0062
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

SOME/IP Routing Management 소프트웨어는 정상 중단 조건을 만족하지 못하거나 이벤트 수신 시점부터 {P_EthFault_ServiceSuspend_Timeout} 이내에 StopOffer 및 StopSubscribe 전송을 완료하지 못한 상태에서 link loss 또는 TTL expiry가 감지되면, StopOffer 및 StopSubscribe 전송이 불가능한 경우에는 전송 불가 시의 offer 및 subscription 만료·Unsubscribe 경로를 적용하고 전송이 가능한 경우에는 전송 가능 시의 StopOffer·Unsubscribe 종료 경로를 적용하여야 한다.

## Notes

정상 중단 조건 판단과 타임아웃 내 전송은 SRS-SomeIP-RoutingManagement-0017이 규정한다. 전송 불가 시 경로는 SRS-SomeIP-RoutingManagement-0058, 전송 가능 시 경로는 SRS-SomeIP-RoutingManagement-0062가 규정하며, 이 item은 그 둘 중 어느 경로가 적용되는지를 결정하는 디스패치 규칙만 책임진다.
