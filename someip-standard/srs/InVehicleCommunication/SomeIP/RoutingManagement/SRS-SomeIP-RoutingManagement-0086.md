---
uid: SRS-UID-70eb93a1b2b5
id: SRS-SomeIP-RoutingManagement-0086
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Re-registered EventGroup Subscription Lifetime
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter:
- uid: SRS-UID-90652d5d7aa3
  cb_id: 38285360
related_items:
- SRS-SomeIP-ServiceDiscovery-0045
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 재수신한 SubscribeEventGroup 요청으로 생성한 subscription을 요청에 적용된 TTL 동안만 유효한 상태로 유지하여야 한다.
SOME/IP Routing Management 소프트웨어는 TTL이 만료되거나 요청에 적용된 TTL이 유효하지 않은 경우 해당 subscription을 유효한 상태로 취급하여서는 안 된다.
SOME/IP Routing Management 소프트웨어는 재수신한 SubscribeEventGroup 요청에 대해 SubscribeEventgroupAck를 수신하기 전까지 해당 subscription을 확정된 상태로 취급하지 않아야 하며, SubscribeEventgroupNack을 수신하면 해당 subscription을 거부된 상태로 처리하여야 한다.
SOME/IP Routing Management 소프트웨어는 재수신한 SubscribeEventGroup 요청에 대해 SubscribeEventgroupAck 또는 SubscribeEventgroupNack을 수신하지 못한 채 최대 {P_SD_SubscribeRetryMax}회의 재전송 각각에 대한 {P_SD_SubscribeRetryDelay}ms 응답 대기 시간이 모두 만료되면, 해당 subscription 시도를 실패로 종료하고 미성립 상태로 유지하여야 한다.

## Notes

