---
uid: SRS-UID-82c87ede5c0c
id: SRS-SomeIP-ServiceDiscovery-0072
cb_id: 40594161
domain: someip
parent: SRS-UID-88c1c630dd53
title: OfferService TTL Zero Transmission Prohibition
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service를 제공하는 OfferService entry를 전송할 때 TTL field를 0x000000으로 설정하지 않아야 한다.

## Notes
