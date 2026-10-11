---
uid: SRS-UID-5bda6a079cf0
id: SRS-SomeIP-RoutingManagement-0094
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: OfferService Repetition Phase Retry
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter:
- uid: SRS-UID-c7c211a83191
  cb_id: 40438666
related_items:
- SRS-SomeIP-RoutingManagement-0017
- SRS-SomeIP-RoutingManagement-0035
- SRS-SomeIP-RoutingManagement-0075
- SRS-SomeIP-RoutingManagement-0095
- SRS-SomeIP-ServiceDiscovery-0004
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 OfferService 개시 후 Initial Wait Phase를 거쳐, {P_SD_RepetitionMax}에 도달할 때까지 {P_SD_RepetitionBaseDelay}로 매회 지연을 배가시키며 Repetition Phase의 OfferService를 재전송하여야 한다.

## Notes

OfferService 개시 트리거 자체는 SRS-SomeIP-RoutingManagement-0035가 규정한다. Initial Wait Phase 진입 시점의 지연 산정은 SRS-SomeIP-RoutingManagement-0075가 규정하며, 이 item은 Initial Wait Phase 종료 이후 Repetition Phase의 재전송만 책임진다. Repetition Phase 종료 후 Main Phase 주기 전송은 SRS-SomeIP-RoutingManagement-0095가 규정한다. Ethernet fault로 인한 OfferService 중단(StopOffer)은 SRS-SomeIP-RoutingManagement-0017/0092/0093 계열이 규정하며 이 Repetition Phase 재전송을 인터럽트할 수 있다. {P_SD_RepetitionBaseDelay}/{P_SD_RepetitionMax}는 SRS-SomeIP-ServiceDiscovery-0004가 소유한 파라미터다.
