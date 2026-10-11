---
uid: SRS-UID-a92ae9773aae
id: SRS-SomeIP-ServiceDiscovery-0102
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Find Repetition Handling
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_FindInitialDelay_Min
  type: uint32
  range: 0~1000
  unit: ms
  default: '100'
- name: P_SD_FindInitialDelay_Max
  type: uint32
  range: 0~3000
  unit: ms
  default: '300'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0011
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 FindService 전송 후 해당 service의 OfferService를 수신하지 못한 경우 Repetition Phase 재전송 정책에 따라 FindService를 재전송하여야 한다.

## Notes

