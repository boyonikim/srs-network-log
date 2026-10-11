---
uid: SRS-UID-2f1e3187898d
id: SRS-SomeIP-ServiceDiscovery-0058
cb_id: 38285351
domain: someip
parent: SRS-UID-88c1c630dd53
title: Sleep Preparation Completion Notification
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
spec_pattern_type: nonfunctional
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider의 sleep 진입 준비 절차에서 `StopOfferService 전송 완료 시점`부터 application에 sleep 진입 준비 완료 상태를 통지하기까지의 지연 시간을 {P_SleepPreparationTimeout}ms 이하로 유지하여야 한다.
## Notes
