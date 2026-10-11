---
uid: SRS-UID-11770ac5f01f
id: SRS-SomeIP-ServiceDiscovery-0017
cb_id: 40438675
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Discovery Restart on OfferService Expiry
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0014
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 OfferService SD entry의 TTL 만료를 감지하면 해당 service의 제공 유효기간이 종료된 것으로 판단하고, Initial Wait Phase부터 service discovery를 재개하여야 한다.

## Notes
