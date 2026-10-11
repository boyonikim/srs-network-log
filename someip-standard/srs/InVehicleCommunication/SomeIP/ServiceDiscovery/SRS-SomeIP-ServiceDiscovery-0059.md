---
uid: SRS-UID-e569b8d7b21a
id: SRS-SomeIP-ServiceDiscovery-0059
cb_id: 40438672
domain: someip
parent: SRS-UID-88c1c630dd53
title: Sleep Preparation Timeout Notification
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SleepPreparationTimeout
  type: uint32
  range: 10~500
  unit: ms
  default: '50'
mapped_parameter:
- {uid: SRS-UID-2f1e3187898d, cb_id: 38285351}
related_items:
- SRS-SomeIP-ServiceDiscovery-0058
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

SOME/IP Service Discovery 기능은 sleep 진입 준비 절차에서 `StopOfferService 전송 완료 시점`으로부터 {P_SleepPreparationTimeout}ms 이내에 sleep 진입 준비가 완료되지 않으면 해당 타임아웃 경과 시점에 application에 `SleepPreparationTimeout` 결과를 통지하여야 한다.

## Notes
