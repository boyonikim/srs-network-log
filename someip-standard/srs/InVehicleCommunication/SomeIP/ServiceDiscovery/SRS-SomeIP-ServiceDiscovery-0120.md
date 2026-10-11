---
uid: SRS-UID-bee68cb50519
id: SRS-SomeIP-ServiceDiscovery-0120
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: SubscribeEventGroup Acknowledgement Timeout
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_SubscribeAckTimeout
  type: uint32
  range: project-defined positive duration
  unit: ms
  default: project-defined
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0066
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 SubscribeEventGroupAck 응답이 {P_SD_SubscribeAckTimeout}ms 이내에 수신되지 않으면 해당 subscription의 확인 절차를 종료하고 확인된 상태로 취급하여서는 안 된다.

## Notes


