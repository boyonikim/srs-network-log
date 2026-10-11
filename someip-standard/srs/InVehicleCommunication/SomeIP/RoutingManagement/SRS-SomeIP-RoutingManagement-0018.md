---
uid: SRS-UID-8a374d9ae601
id: SRS-SomeIP-RoutingManagement-0018
cb_id: 38285330
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Duplicate Service ID Registration Rejection
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

SOME/IP Routing Management 소프트웨어는 이미 등록된 service ID에 대한 후속 등록 요청을 거부하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 후속 등록 요청을 거부할 때 기존에 등록된 해당 service ID의 등록 상태를 변경하지 않아야 한다.

## Notes
