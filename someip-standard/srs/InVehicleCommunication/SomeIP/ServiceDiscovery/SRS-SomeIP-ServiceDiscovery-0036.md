---
uid: SRS-UID-98d5248d0e89
id: SRS-SomeIP-ServiceDiscovery-0036
cb_id: 40438686
domain: someip
parent: SRS-UID-88c1c630dd53
title: Resource Shortage Notification on Subscriber Limit
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0034
- SRS-SomeIP-ServiceDiscovery-0035
- SRS-SomeIP-ServiceDiscovery-0002
- SRS-SomeIP-ServiceDiscovery-0008
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 동시 subscriber(consumer) 수 상한 초과로 SubscribeEventGroupNack을 반환한 경우 거부된 요청의 Service ID, Instance ID, EventGroup ID와 거부 사유가 동시 subscriber(consumer) 수 상한 초과임을 포함하는 리소스 부족 통지를 해당 SubscribeEventGroupNack을 전송한 요청마다 1회 application에 전송하여야 한다.

## Notes
