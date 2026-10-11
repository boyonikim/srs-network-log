---
uid: SRS-UID-909832e4ca50
id: SRS-SomeIP-ServiceDiscovery-0010
cb_id: 38210986
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Find Initial Wait Timing
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
spec_pattern_type: nonfunctional
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 {P_SD_FindInitialDelay_Min}을 {P_SD_FindInitialDelay_Max} 이하로 구성하여야 한다.
## Notes
