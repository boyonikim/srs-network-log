---
uid: SRS-UID-091ea2afaa97
id: SRS-SomeIP-ServiceDiscovery-0054
cb_id: 40438689
domain: someip
parent: SRS-UID-88c1c630dd53
title: OfferService Availability Preservation
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0051
- SRS-SomeIP-ServiceDiscovery-0052
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 관리하는 모든 subscriber(consumer)의 EventGroup subscription이 해제된 경우에도 해당 service의 OfferService 제공 상태를 유지하여야 한다.

## Notes
