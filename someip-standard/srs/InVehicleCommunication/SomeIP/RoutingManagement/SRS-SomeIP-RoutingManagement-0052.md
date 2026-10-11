---
uid: SRS-UID-b766bcfe942a
id: SRS-SomeIP-RoutingManagement-0052
cb_id: 40610552
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Unavailability Handling Failure
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0016
- SRS-SomeIP-RoutingManagement-0057
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 Service Unavailable 상태 통지 또는 해당 service 내부 상태 전환이 각 요구사항의 시간 제한 내에 완료되지 않으면, application에 처리 실패를 통지하고 해당 service를 Service Unavailable 상태로 유지하여야 한다.

## Notes

Service Unavailable 상태 통지는 SRS-SomeIP-RoutingManagement-0016에서, service 내부 상태 전환은 SRS-SomeIP-RoutingManagement-0057에서 규정한다.
