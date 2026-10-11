---
uid: SRS-UID-41ad9a7d6d24
id: SRS-SomeIP-RoutingManagement-0093
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Ethernet Fault Timeout Without Link Loss Guard
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

SOME/IP Routing Management 소프트웨어는 이벤트 수신 시점부터 {P_EthFault_ServiceSuspend_Timeout} 이내에 StopOffer 및 StopSubscribe 전송을 완료하지 못하였으나 해당 link가 link-up 상태이고 해당 offer 및 subscription의 TTL이 유효하며 link loss 또는 TTL expiry가 감지되지 않은 경우, link loss 또는 TTL expiry에 따른 만료 처리 및 종료 경로를 적용하여서는 안 된다.

## Notes

SRS-SomeIP-RoutingManagement-0092가 규정하는 디스패치(전송 불가/가능 경로 선택)는 link loss 또는 TTL expiry 감지를 전제로 하므로, 이 item은 그 전제 자체가 성립하지 않는 경계 조건에서 오탐으로 종료 경로가 적용되지 않음을 명시한다.
