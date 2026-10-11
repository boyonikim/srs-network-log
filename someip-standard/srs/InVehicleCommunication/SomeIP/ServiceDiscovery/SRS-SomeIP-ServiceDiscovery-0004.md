---
uid: SRS-UID-c7c211a83191
id: SRS-SomeIP-ServiceDiscovery-0004
cb_id: 40438666
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Offer Repetition Phase Timing
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_RepetitionBaseDelay
  type: uint32
  range: 10~5000
  unit: ms
  default: '200'
- name: P_SD_RepetitionMax
  type: uint8
  range: 1~10
  unit: count
  default: '3'
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

SOME/IP Service Discovery 기능은 service provider가 Repetition Phase에서 OfferService를 재전송하되, n회차 전송 간격을 {P_SD_RepetitionBaseDelay} ms × 2^(n-1)로 적용하고 최대 {P_SD_RepetitionMax}회 반복하여야 한다.

## Notes
