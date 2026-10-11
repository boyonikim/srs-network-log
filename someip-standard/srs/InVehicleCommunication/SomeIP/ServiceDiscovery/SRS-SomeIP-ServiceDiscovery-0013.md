---
uid: SRS-UID-51822acf0467
id: SRS-SomeIP-ServiceDiscovery-0013
cb_id: 38285352
domain: someip
parent: SRS-UID-88c1c630dd53
title: ServiceReady Transition
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

SOME/IP Service Discovery 기능은 consumer가 진행 중인 Service Find 절차와 관계없이 service provider로부터 TTL이 0보다 큰 유효한 OfferService entry를 수신하면 해당 service를 ServiceReady 상태로 설정하여야 한다.

SOME/IP Service Discovery 기능은 service provider의 유효한 OfferService entry를 수신하지 않은 경우 또는 TTL이 0x000000인 StopOfferService entry를 수신한 경우 해당 entry 수신을 이유로 해당 service를 ServiceReady 상태로 설정하지 않아야 한다.

## Notes
