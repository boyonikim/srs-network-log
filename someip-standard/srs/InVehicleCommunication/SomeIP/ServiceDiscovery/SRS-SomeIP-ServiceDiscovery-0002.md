---
uid: SRS-UID-5455aee01afe
id: SRS-SomeIP-ServiceDiscovery-0002
cb_id: 40438668
domain: someip
parent: SRS-UID-88c1c630dd53
title: Routing Initialization Timeout Notification
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_RoutingInitializationTimeout
  type: uint32
  range: 100~30000
  unit: ms
  default: '5000'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0001
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 자신의 초기화 완료 시점을 기산점으로 하여, routing management 소프트웨어로부터 SOME/IP Service Discovery 처리 및 Service Offer 전송 허용을 의미하는 routing 초기화 완료 통지를 {P_SD_RoutingInitializationTimeout}ms 이내에 수신하지 못한 경우 application에 초기화 실패를 통지하여야 한다.

## Notes
