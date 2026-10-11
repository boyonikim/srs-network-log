---
uid: SRS-UID-f49e08b0fe13
id: SRS-SomeIP-RoutingManagement-0091
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Registration Failure Notification
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter:
- uid: SRS-UID-936d288733a4
  cb_id: 38285338
related_items:
- SRS-SomeIP-RoutingManagement-0002
- SRS-SomeIP-RoutingManagement-0078
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 {P_RM_ServiceRegister_Timeout}ms 이내에 service 등록이 완료되지 않으면 service 등록 실패로 판정하여 application에 통지하여야 한다.

## Notes

