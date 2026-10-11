---
uid: SRS-UID-19fd93417d1b
id: SRS-SomeIP-ServiceDiscovery-0015
cb_id: 38223769
domain: someip
parent: SRS-UID-88c1c630dd53
title: Consumer Availability State on OfferService Expiry
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

SOME/IP Service Discovery 기능은 consumer가 OfferService SD entry의 TTL 만료를 감지하면 해당 service의 consumer 가용성 상태를 ServiceNotAvailable로 전이하여야 한다.

※ 예외 규칙: SOME/IP Service Discovery 기능은 consumer가 해당 OfferService SD entry의 TTL 만료 전에 동일 service의 유효한 OfferService를 수신한 경우 해당 service의 consumer 가용성 상태를 ServiceNotAvailable로 전이하지 않아야 한다.

## Notes
