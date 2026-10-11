---
uid: SRS-UID-b5eb729c532c
id: SRS-SomeIP-RoutingManagement-0077
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Unexpected Signal Handling During Initialization Readiness Check
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0002
spec_pattern_type: exception_fault
evidence:
- ref: EV-002
  source: SRC-001
  location: '/home/worker/.copilot/session-state/40fe21ee-d57c-4557-b2df-1f36bfc324ce/files/routing-management-unexpected-signal-split-source.md#requirement-1-initialization-readiness-check;
    cited source: /home/worker/workspace/someip-standard/srs/InVehicleCommunication/SomeIP/RoutingManagement/SRS-SomeIP-RoutingManagement-0002.md,
    former Description exception rule'
  version: null
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: null
---
## Description

초기화 준비 상태 확인 중 서비스 등록 테이블 초기화 완료, SD 상태 머신 초기화 완료 및 통신 채널 확립 완료 이외의 준비 상태 이벤트가 수신되면 SOME/IP Routing Management 소프트웨어는 현재 준비 상태 처리 상태를 변경하지 않고 경고를 기록하여야 한다.

## Notes
