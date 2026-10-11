---
uid: SRS-UID-50180248c1f8
id: SRS-SomeIP-RoutingManagement-0019
cb_id: 40610537
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Registration Wait Timeout Notification
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_RM_ServiceRegisterWait_Timeout
  type: uint32
  range: 1000~10000
  unit: ms
  default: '5000'
mapped_parameter: []
related_items: []
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---

## Description

SOME/IP Routing Management 소프트웨어는 자신의 초기화 완료 신호를 최대 {P_RM_ServiceRegisterWait_Timeout} 동안 대기하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 대기 시간 초과 시 application에 service 등록 비가용 상태를 통지하여야 한다.

## Notes
