---
uid: SRS-UID-54ac7aca6d5c
id: SRS-SomeIP-ServiceDiscovery-0063
cb_id: 38285328
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Resubscription Exhaustion Handling
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_SubscribeRetryMax
  type: uint8
  range: 0~10
  unit: count
  default: '3'
mapped_parameter:
- uid: SRS-UID-90652d5d7aa3
  cb_id: 38285360
related_items:
- SRS-SomeIP-ServiceDiscovery-0045
- SRS-SomeIP-ServiceDiscovery-0076
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 EventGroup resubscription의 최초 전송 및 최대 {P_SD_SubscribeRetryMax}회 재전송 각각의 전송 시점부터 {P_SD_SubscribeRetryDelay}ms 동안 SubscribeEventGroupAck 또는 SubscribeEventGroupNack을 수신하지 못하고 더 이상 허용된 재전송 횟수가 남아 있지 않으면 TTL을 0으로 설정한 StopSubscribeEventGroup entry를 전송하여 해당 EventGroup의 subscription을 종료하여야 한다.
## Notes
