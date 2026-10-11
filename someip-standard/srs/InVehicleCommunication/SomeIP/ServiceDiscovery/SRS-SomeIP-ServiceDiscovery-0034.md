---
uid: SRS-UID-e18807e14794
id: SRS-SomeIP-ServiceDiscovery-0034
cb_id: 38285356
domain: someip
parent: SRS-UID-88c1c630dd53
title: Concurrent Subscriber Limit
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_MaxSubscribers
  type: uint16
  range: 1~512
  unit: count
  default: '64'
mapped_parameter: []
related_items: []
spec_pattern_type: nonfunctional
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 동시에 관리하는 subscriber로 등록된 consumer 수를 {P_SD_MaxSubscribers} 이하로 제한하여야 한다.

## Notes
