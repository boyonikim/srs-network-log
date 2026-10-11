---
uid: SRS-UID-dc0e1afba953
id: SRS-SomeIP-ServiceDiscovery-0024
cb_id: 40438680
domain: someip
parent: SRS-UID-88c1c630dd53
title: Unavailability Handling on StopOfferService
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 service provider로부터 StopOfferService를 수신하면 해당 service의 consumer 가용성 상태를 ServiceNotAvailable로 전이하여야 한다.

## Notes
