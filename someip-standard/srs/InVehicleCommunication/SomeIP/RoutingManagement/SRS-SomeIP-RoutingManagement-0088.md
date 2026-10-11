---
uid: SRS-UID-3cbbc7ed9209
id: SRS-SomeIP-RoutingManagement-0088
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Registration Rejection Error Response
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: data_logic
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 거부한 등록 요청의 등록 요청자에게 정의된 SOME/IP error response code를 registration request API의 반환값으로 반환하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 거부 사유에 대응하는 정의된 SOME/IP error response code가 존재하지 않으면 해당 등록 요청을 등록 완료 상태로 처리하여서는 안 된다.

## Notes


