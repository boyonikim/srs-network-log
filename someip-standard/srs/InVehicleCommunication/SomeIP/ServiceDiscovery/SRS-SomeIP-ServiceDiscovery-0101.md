---
uid: SRS-UID-f26b7f9795fc
id: SRS-SomeIP-ServiceDiscovery-0101
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Find Initial Wait Transmission
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

SOME/IP Service Discovery 기능은 consumer가 각 Service Find 절차를 개시할 때마다 Initial Wait Phase에서 두 파라미터 사이의 균등 분포 난수로 새로 선택한 지연 시간 동안 대기한 후 FindService를 전송하여야 한다.

## Notes


