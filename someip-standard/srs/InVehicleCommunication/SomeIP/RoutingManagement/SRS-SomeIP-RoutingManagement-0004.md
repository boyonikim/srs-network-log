---
uid: SRS-UID-b23269fdfb7d
id: SRS-SomeIP-RoutingManagement-0004
cb_id: 38285339
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Initialization Timeout Failure Detection
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_RM_Init_Timeout
  type: uint32
  range: 1000~30000
  unit: ms
  default: '8000'
mapped_parameter: []
related_items: [SRS-UID-55f4f1b550fd]
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---

## Description

SOME/IP Routing Management 소프트웨어는 초기화 시작 시점부터 {P_RM_Init_Timeout} 이내에 준비 상태(서비스 등록 테이블 초기화, SD 상태 머신 초기화, 통신 채널 확립 및 EventGroup 구독 목록 초기화 완료)에 도달하지 못할 경우, 초기화 실패로 처리하여야 한다.

## Notes

초기화 실패 시 application에 미들웨어 초기화 오류를 통지하는 동작은 SRS-SomeIP-RoutingManagement-0083에서, 미들웨어 초기화 완료 이벤트를 통지하지 않는 동작은 SRS-SomeIP-RoutingManagement-0082에서 규정한다.
