---
uid: SRS-UID-3c103d95e803
id: SRS-SomeIP-ServiceDiscovery-0060
cb_id: 40438698
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Find Restart on Sleep Recovery
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

SOME/IP Service Discovery 기능은 consumer가 sleep 상태에서 복귀한 후 Ethernet link 확립을 확인한 시점으로부터 {P_SD_SleepRecoveryFindDelay}ms 이내에 FindService 전송을 시작하여야 한다.
## Notes
