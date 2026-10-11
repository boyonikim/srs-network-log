---
uid: SRS-UID-631981184c37
id: SRS-SomeIP-ServiceDiscovery-0116
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: FindService Repetition Early Termination
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
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 consumer가 Repetition Phase 진행 중 해당 service의 OfferService를 수신한 경우 잔여 재전송 횟수와 무관하게 FindService 재전송을 즉시 중단하고 FindService를 전송하지 않는 Main Phase로 진입하여야 한다.

## Notes

