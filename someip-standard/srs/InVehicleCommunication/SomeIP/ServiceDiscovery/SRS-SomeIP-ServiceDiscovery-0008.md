---
uid: SRS-UID-c370f3e3e3fe
id: SRS-SomeIP-ServiceDiscovery-0008
cb_id: 40438670
domain: someip
parent: SRS-UID-88c1c630dd53
title: Resource Shortage Notification on Offer Limit
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0006
- SRS-SomeIP-ServiceDiscovery-0007
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider의 Service Offer instance 상한 초과로 신규 Offer 요청이 거부된 경우, 거부된 Offer 요청 1건마다 거부된 Offer 요청의 service interface 식별 정보와 Service Offer instance 상한 초과 사유를 포함한 리소스 부족 통지를 application에 1회 전송하여야 한다.

## Notes
