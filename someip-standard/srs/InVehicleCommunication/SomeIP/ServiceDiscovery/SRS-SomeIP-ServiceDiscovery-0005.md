---
uid: SRS-UID-74abb389f183
id: SRS-SomeIP-ServiceDiscovery-0005
cb_id: 40438667
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Offer Main Phase Cyclic Timing
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_CyclicOfferDelay
  type: uint32
  range: 100~15000
  unit: ms
  default: '1000'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0003
spec_pattern_type: nonfunctional
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 Main Phase에서 {P_SD_CyclicOfferDelay} ms 주기로 OfferService를 전송하여야 한다.

## Notes
