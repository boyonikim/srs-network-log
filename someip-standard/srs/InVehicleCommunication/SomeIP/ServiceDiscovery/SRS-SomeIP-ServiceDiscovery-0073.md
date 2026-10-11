---
uid: SRS-UID-8abd2df331bd
id: SRS-SomeIP-ServiceDiscovery-0073
cb_id: 40594162
domain: someip
parent: SRS-UID-88c1c630dd53
title: OfferService TTL Zero Reception Interpretation
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: data_logic
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 TTL field가 0x000000인 OfferService entry를 수신하면 해당 entry를 StopOfferService로 해석하여야 한다.

## Notes
