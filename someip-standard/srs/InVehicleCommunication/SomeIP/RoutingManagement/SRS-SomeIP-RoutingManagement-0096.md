---
uid: SRS-UID-91ee417deb54
id: SRS-SomeIP-RoutingManagement-0096
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: FindService Repetition Until Max Reached or Offer Received
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter:
- uid: SRS-UID-f422d5d47636
  cb_id: 40438673
related_items:
- SRS-SomeIP-RoutingManagement-0036
- SRS-SomeIP-ServiceDiscovery-0011
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 최초 FindService 전송 후 해당 service의 OfferService를 수신하지 못하면 {P_SD_FindRepetitionMax}에 도달할 때까지 {P_SD_FindRepetitionBaseDelay}로 FindService를 재전송하여야 하며, {P_SD_FindRepetitionMax}에 도달하거나 해당 service의 OfferService를 수신하면 재전송을 중단하여야 한다.

## Notes

FindService 최초 전송 트리거는 SRS-SomeIP-RoutingManagement-0036이 규정한다. 재전송 간격 공식 자체는 SRS-SomeIP-ServiceDiscovery-0011이 소유한다 — 이 item은 그 공식을 사용해 "언제 멈추는가"(횟수 도달 또는 Offer 수신)를 추가로 규정하며, 0011에는 없는 RoutingManagement 고유의 종료 조건이라 중복이 아니다.
