---
uid: SRS-UID-2352d34613f6
id: SRS-SomeIP-RoutingManagement-0002
cb_id: 38285337
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: SD Initiation Prohibition Before Internal State Ready
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0077
- SRS-UID-55f4f1b550fd
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---

## Description

SOME/IP Routing Management 소프트웨어는 자신의 서비스 등록 테이블 초기화, SD 상태 머신 초기화, 통신 채널 확립 및 EventGroup 구독 목록 초기화가 모두 완료되기 전에는 서비스 등록 또는 Service Discovery 관련 동작(OfferService, FindService, SubscribeEventgroup 및 StopSubscribeEventgroup)을 수행하지 않아야 한다.

## Notes
