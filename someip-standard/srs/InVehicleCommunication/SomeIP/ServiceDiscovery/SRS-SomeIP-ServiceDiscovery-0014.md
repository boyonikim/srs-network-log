---
uid: SRS-UID-ea1cd336f630
id: SRS-SomeIP-ServiceDiscovery-0014
cb_id: 38285353
domain: someip
parent: SRS-UID-88c1c630dd53
title: ServiceNotSeen Observation State on OfferService Expiry
status: Reviewed
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

SOME/IP Service Discovery 기능은 consumer가 OfferService SD entry의 TTL 만료를 감지하면 해당 service의 SD 관측 상태를 ServiceNotSeen으로 설정하여야 한다.

※ 예외 규칙: SOME/IP Service Discovery 기능은 해당 service의 OfferService SD entry TTL 만료를 감지하지 않은 경우 해당 service의 SD 관측 상태를 ServiceNotSeen으로 설정하지 않아야 한다.

## Notes
