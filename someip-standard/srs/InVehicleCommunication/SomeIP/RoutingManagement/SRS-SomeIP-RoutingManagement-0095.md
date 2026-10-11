---
uid: SRS-UID-67d6428f1fae
id: SRS-SomeIP-RoutingManagement-0095
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: OfferService Main Phase Cyclic Offer
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter:
- uid: SRS-UID-74abb389f183
  cb_id: 40438667
related_items:
- SRS-SomeIP-RoutingManagement-0017
- SRS-SomeIP-RoutingManagement-0035
- SRS-SomeIP-RoutingManagement-0094
- SRS-SomeIP-ServiceDiscovery-0005
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 Repetition Phase 종료 후 {P_SD_CyclicOfferDelay} 주기로 Main Phase의 OfferService 주기적 전송을 유지하여야 한다.

## Notes

Repetition Phase 재전송은 SRS-SomeIP-RoutingManagement-0094가 규정한다. Ethernet fault로 인한 OfferService 중단(StopOffer)은 SRS-SomeIP-RoutingManagement-0017/0092/0093 계열이 규정하며 이 Main Phase 주기 전송을 인터럽트할 수 있다. {P_SD_CyclicOfferDelay}는 SRS-SomeIP-ServiceDiscovery-0005가 소유한 파라미터다.
