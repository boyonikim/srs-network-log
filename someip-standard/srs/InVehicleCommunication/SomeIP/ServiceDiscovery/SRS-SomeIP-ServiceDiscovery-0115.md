---
uid: SRS-UID-acb1c88d4eae
id: SRS-SomeIP-ServiceDiscovery-0115
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: FindService Repetition Exhaustion Handling
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
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 consumer가 최대 {P_SD_FindRepetitionMax}회의 FindService 재전송을 모두 소진할 때까지 해당 service의 OfferService를 수신하지 못한 경우, FindService 재전송을 중단하고 해당 service의 OfferService를 수신하지 못하였음을 application에 통지한 뒤 Repetition Phase를 종료하고 Main Phase로 진입하여야 한다.

## Notes

