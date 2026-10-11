---
uid: SRS-UID-89aadd77ac69
id: SRS-SomeIP-RoutingManagement-0035
cb_id: 40610546
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: OfferService Start After Provider Registration
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0002
- SRS-SomeIP-RoutingManagement-0075
- SRS-SomeIP-RoutingManagement-0094
- SRS-SomeIP-RoutingManagement-0095
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 준비 완료 후 provider 등록 이벤트를 수신하면 OfferService를 개시하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 준비 완료 전에 provider 등록 이벤트를 수신하면 OfferService를 개시하지 않아야 한다.

## Notes


