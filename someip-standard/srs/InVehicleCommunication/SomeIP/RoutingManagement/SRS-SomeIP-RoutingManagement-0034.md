---
uid: SRS-UID-55f4f1b550fd
id: SRS-SomeIP-RoutingManagement-0034
cb_id: 40610539
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Middleware Initialization Completion State
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 서비스 등록 테이블 초기화, SD 상태 머신 초기화, 통신 채널 확립 및 EventGroup 구독 목록 초기화가 모두 완료되면 초기화 완료 상태를 설정하여야 하며, 하나라도 완료되지 않으면 초기화 완료 상태를 설정하여서는 안 된다.

## Notes
