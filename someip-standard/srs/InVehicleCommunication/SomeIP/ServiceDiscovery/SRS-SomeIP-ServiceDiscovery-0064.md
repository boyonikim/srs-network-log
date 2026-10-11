---
uid: SRS-UID-f8f5a0fc4391
id: SRS-SomeIP-ServiceDiscovery-0064
cb_id: 40466965
domain: someip
parent: SRS-UID-88c1c630dd53
title: OfferService Response to FindService
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_RequestResponseDelay_Min
  type: uint32
  range: 0~1000
  unit: ms
  default: '10'
- name: P_SD_RequestResponseDelay_Max
  type: uint32
  range: 1~3000
  unit: ms
  default: '50'
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

SOME/IP Service Discovery 기능은 {P_SD_RequestResponseDelay_Min}을 {P_SD_RequestResponseDelay_Max} 이하로 구성하여야 한다.

## Notes
