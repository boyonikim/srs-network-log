---
uid: SRS-UID-c376cb3c50b1
id: SRS-SomeIP-RoutingManagement-0078
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Unexpected Signal Handling During Service Registration
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0003
spec_pattern_type: exception_fault
evidence:
- ref: EV-004
  source: SRC-001
  location: '/home/worker/.copilot/session-state/40fe21ee-d57c-4557-b2df-1f36bfc324ce/files/routing-management-unexpected-signal-split-source.md#requirement-2-service-registration;
    cited source: /home/worker/workspace/someip-standard/srs/InVehicleCommunication/SomeIP/RoutingManagement/SRS-SomeIP-RoutingManagement-0003.md,
    former Description exception rule'
  version: null
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: null
---
## Description

서비스 등록 처리 중 준비 완료 신호 이외의 신호가 수신되면 SOME/IP Routing Management 소프트웨어는 현재 서비스 등록 상태를 변경하지 않고 경고를 기록하여야 한다.

## Notes

