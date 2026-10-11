---
uid: SRS-UID-85f5de3ef645
id: SRS-SomeIP-ServiceDiscovery-0006
cb_id: 38285349
domain: someip
parent: SRS-UID-88c1c630dd53
title: Active Service Offer Limit
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_MaxOfferInstances
  type: uint16
  range: 1~256
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

SOME/IP Service Discovery 기능은 service provider가 동시에 활성화하는 Service Offer 절차 수를 {P_SD_MaxOfferInstances} 이하로 제한하여야 한다.

## Notes
