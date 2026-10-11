---
uid: SRS-UID-f422d5d47636
id: SRS-SomeIP-ServiceDiscovery-0011
cb_id: 40438673
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Find Repetition Phase Timing
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_FindRepetitionBaseDelay
  type: uint32
  range: 10~5000
  unit: ms
  default: '200'
- name: P_SD_FindRepetitionMax
  type: uint8
  range: 0~10
  unit: count
  default: '3'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0010
- SRS-SomeIP-ServiceDiscovery-0002
- SRS-SomeIP-ServiceDiscovery-0008
spec_pattern_type: nonfunctional
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 Repetition Phase에서 첫 번째 FindService 재전송을 n=1회차로 정의하고, 1 ≤ n ≤ {P_SD_FindRepetitionMax}인 각 재전송의 전송 간격을 {P_SD_FindRepetitionBaseDelay} ms × 2^(n-1)로 적용하여야 한다.
## Notes
