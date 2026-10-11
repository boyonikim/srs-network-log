---
uid: SRS-UID-4aa54bece4a9
id: SRS-SomeIP-ServiceDiscovery-0048
cb_id: 40438695
domain: someip
parent: SRS-UID-88c1c630dd53
title: Subscription Timeout Notification
status: Define
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
- SRS-SomeIP-ServiceDiscovery-0045
- SRS-SomeIP-ServiceDiscovery-0047
- SRS-SomeIP-ServiceDiscovery-0002
- SRS-SomeIP-ServiceDiscovery-0008
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 SubscribeEventGroup 요청을 전송한 후 최초 전송 및 최대 {P_SD_SubscribeRetryMax}회 재전송 각각에 대해 {P_SD_SubscribeRetryDelay}ms 이내에 service provider로부터 SubscribeEventGroupAck 또는 SubscribeEventGroupNack을 수신하지 못하고 더 이상 재전송 가능 횟수가 남아 있지 않으면 application에 해당 subscription 요청이 응답 없이 시간 초과로 종료되었음을 통지하여야 한다.

## Notes
