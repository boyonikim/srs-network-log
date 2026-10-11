---
uid: SRS-UID-5e36f4036910
id: SRS-SomeIP-ServiceDiscovery-0094
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: Sleep Recovery Link Establishment Failure Handling
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_SleepRecoveryFindDelay
  type: uint32
  range: 100~2000
  unit: ms
  default: '500'
mapped_parameter: []
related_items:
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

SOME/IP Service Discovery 기능은 consumer가 sleep 상태에서 복귀한 후 Ethernet link 확립이 확인되지 않은 동안에는 FindService를 전송하지 않고 link 확립 확인을 반복하여야 한다.
SOME/IP Service Discovery 기능은 {P_SD_SleepRecoveryFindDelay}ms 이내에 link 확립이 확인되지 않으면 application에 Ethernet link 미확립으로 Service Find 절차를 개시하지 못하였음을 통지하여야 한다.

## Notes

