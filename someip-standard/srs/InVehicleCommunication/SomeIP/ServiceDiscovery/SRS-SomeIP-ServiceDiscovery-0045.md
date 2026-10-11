---
uid: SRS-UID-90652d5d7aa3
id: SRS-SomeIP-ServiceDiscovery-0045
cb_id: 38285360
domain: someip
parent: SRS-UID-88c1c630dd53
title: SubscribeEventGroup Retry
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_SubscribeRetryMax
  type: uint8
  range: 0~10
  unit: count
  default: '3'
- name: P_SD_SubscribeRetryDelay
  type: uint32
  range: 10~5000
  unit: ms
  default: '500'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0044
- SRS-SomeIP-ServiceDiscovery-0049
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 SubscribeEventGroup 요청을 전송한 후 service provider로부터 SubscribeEventGroupAck 또는 SubscribeEventGroupNack을 수신하기 전까지 최대 {P_SD_SubscribeRetryMax}회, {P_SD_SubscribeRetryDelay}ms 간격으로 해당 SubscribeEventGroup 요청을 재전송하여야 한다.

SOME/IP Service Discovery 기능은 최초 전송 및 최대 {P_SD_SubscribeRetryMax}회 재전송 각각의 전송 시점부터 {P_SD_SubscribeRetryDelay}ms 동안 SubscribeEventGroupAck 또는 SubscribeEventGroupNack을 기다리고, 마지막 허용 전송의 응답 대기 시간이 만료될 때까지 어느 응답도 수신하지 못하면 해당 EventGroup subscription 시도를 실패로 종료하고 해당 EventGroup subscription을 미성립 상태로 유지하여야 한다.
SOME/IP Service Discovery 기능은 {P_SD_SubscribeRetryMax}가 0이면 최초 전송의 응답 대기 시간 만료 후 응답 없이 subscription 시도를 실패로 종료하고 재전송하지 않아야 한다.

## Notes
