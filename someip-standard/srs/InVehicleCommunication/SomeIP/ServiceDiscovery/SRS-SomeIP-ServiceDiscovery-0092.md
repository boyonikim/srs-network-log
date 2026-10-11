---
uid: SRS-UID-c9002a00cfc6
id: SRS-SomeIP-ServiceDiscovery-0092
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: Sleep Preparation Timeout Failure Handling
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SleepPreparationTimeout
  type: uint32
  range: 10~500
  unit: ms
  default: '50'
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

SOME/IP Service Discovery 기능은 {P_SleepPreparationTimeout}ms 이내에 sleep 진입 준비가 완료되지 않으면 sleep 진입 준비 미완료 상태를 유지하여야 하며, application에 sleep 진입 준비 완료 상태를 통지하여서는 안 된다.

## Notes

