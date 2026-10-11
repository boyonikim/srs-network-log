---
uid: SRS-UID-33562625217f
id: SRS-SomeIP-ServiceDiscovery-0019
cb_id: 38285359
domain: someip
parent: SRS-UID-88c1c630dd53
title: StopOfferService on Provider Unavailability
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 application으로부터 해당 service의 제공 중지 요청을 수신하거나 해당 service를 제공하는 application의 종료를 감지한 경우, TTL을 0으로 설정한 OfferService entry(StopOfferService)를 해당 service의 SD multicast endpoint로 전송하여야 한다.

※ 예외 규칙: SOME/IP Service Discovery 기능은 service provider가 해당 service의 OfferService를 제공 중이지 않은 상태에서 제공 중지 요청 또는 application 종료를 감지한 경우 StopOfferService를 전송하지 않아야 한다.

## Notes
