---
uid: SRS-UID-6016d0c9380c
id: SRS-SomeIP-ServiceDiscovery-0007
cb_id: 40438669
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Offer Request Rejection
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_MaxOfferInstances
  type: uint16
  range: 1~256
  unit: count
  default: '64'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0006
- SRS-SomeIP-ServiceDiscovery-0068
- SRS-SomeIP-ServiceDiscovery-0069
- SRS-SomeIP-ServiceDiscovery-0070
- SRS-SomeIP-ServiceDiscovery-0071
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 동시 활성 Service Offer instance 수가 {P_SD_MaxOfferInstances}에 도달한 상태에서 service provider의 신규 Offer 요청이 발생하면 해당 요청을 거부하여야 한다.

## Notes
