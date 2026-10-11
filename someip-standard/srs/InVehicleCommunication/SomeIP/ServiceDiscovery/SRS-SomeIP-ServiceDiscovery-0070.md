---
uid: SRS-UID-666ae4d649c7
id: SRS-SomeIP-ServiceDiscovery-0070
cb_id: 40594165
domain: someip
parent: SRS-UID-88c1c630dd53
title: OfferService Transmission Suppression
status: Draft
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

SOME/IP Service Discovery 기능은 동시 활성 Service Offer instance 수가 {P_SD_MaxOfferInstances}에 도달하여 신규 Offer 요청을 거부한 경우 해당 service에 대한 OfferService를 전송하지 아니하여야 한다.

## Notes
