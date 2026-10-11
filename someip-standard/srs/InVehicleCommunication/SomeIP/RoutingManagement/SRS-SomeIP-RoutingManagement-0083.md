---
uid: SRS-UID-c6ee13f28768
id: SRS-SomeIP-RoutingManagement-0083
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Middleware Initialization Failure Notification
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: [SRS-UID-b23269fdfb7d]
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 미들웨어 초기화가 실패하면 application에 미들웨어 초기화 오류를 통지하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 미들웨어 초기화 실패 여부를 판단할 수 없으면 미들웨어 초기화 오류 통지 여부를 결정하지 않아야 하며, 유효한 판단 결과가 확보될 때까지 통지를 완료한 것으로 처리하지 않아야 한다.

## Notes


