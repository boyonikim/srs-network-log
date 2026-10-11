---
uid: SRS-UID-936d288733a4
id: SRS-SomeIP-RoutingManagement-0003
cb_id: 38285338
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Registration After Internal State Ready
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_RM_ServiceRegister_Timeout
  type: uint32
  range: 500~10000
  unit: ms
  default: '3000'
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0002
- SRS-SomeIP-RoutingManagement-0078
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---

## Description

SOME/IP Routing Management 소프트웨어는 준비 완료 후 {P_RM_ServiceRegister_Timeout} 이내에 service 등록을 완료하여야 하며, 해당 시간 내 완료되지 않으면 service를 등록 완료 상태로 취급하여서는 안 된다.
## Notes
