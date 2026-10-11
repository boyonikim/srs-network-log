---
uid: SRS-UID-e006e35dd145
id: SRS-SomeIP-ServiceDiscovery-0066
cb_id: 40466967
domain: someip
parent: SRS-UID-88c1c630dd53
title: Subscription Renewal Before TTL Expiry
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_SubRenewalRatio
  type: uint8
  range: 50~90
  unit: percent
  default: '75'
mapped_parameter: []
related_items: []
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 활성 상태인 EventGroup subscription을 유지하기 위해 직전 SubscribeEventGroupAck 수신 시점으로부터 해당 subscription TTL의 {P_SD_SubRenewalRatio}%가 경과한 시점에 SubscribeEventGroup 요청을 재전송하여야 하며, subscription이 더 이상 활성 상태가 아니면 SubscribeEventGroup 요청을 재전송하여서는 안 된다.
## Notes
