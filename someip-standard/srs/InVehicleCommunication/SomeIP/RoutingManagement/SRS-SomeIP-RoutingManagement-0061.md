---
uid: SRS-UID-becdf8f4e60a
id: SRS-SomeIP-RoutingManagement-0061
cb_id: 40610554
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Initialization Completion Notification
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: [SRS-UID-55f4f1b550fd]
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 미들웨어 초기화가 완료되면 application에 미들웨어 초기화 완료 이벤트를 통지하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 초기화 완료 이벤트 전달이 실패하면 해당 실패를 오류로 기록하고 application에 전달 실패를 보고하여야 하며, 초기화 완료 이벤트가 전달된 것으로 처리하지 않아야 한다.

## Notes

초기화 실패 시 미들웨어 초기화 오류 통지는 SRS-SomeIP-RoutingManagement-0083에서, 초기화 완료 이벤트 미통지(억제)는 SRS-SomeIP-RoutingManagement-0082에서 규정한다.
