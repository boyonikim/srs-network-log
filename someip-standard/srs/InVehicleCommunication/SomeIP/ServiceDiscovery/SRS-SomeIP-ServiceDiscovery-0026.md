---
uid: SRS-UID-94c434942d7e
id: SRS-SomeIP-ServiceDiscovery-0026
cb_id: 40438677
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Discovery Restart on StopOfferService
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0014
- SRS-SomeIP-ServiceDiscovery-0023
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 ServiceReady 상태의 service에 대해 service provider로부터 StopOfferService를 수신하면 Initial Wait Phase부터 service discovery를 재개하여야 한다.

## Notes
