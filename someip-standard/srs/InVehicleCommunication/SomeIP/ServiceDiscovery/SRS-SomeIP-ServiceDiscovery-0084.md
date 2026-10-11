---
uid: SRS-UID-c8d5b734d77c
id: SRS-SomeIP-ServiceDiscovery-0084
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: OfferService SD Entry Wire Format
status: Draft
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

SOME/IP Service Discovery 기능은 OfferService entry의 Service ID, Instance ID, TTL 필드를 SOME/IP PRS의 big-endian byte order와 alignment padding 없는 byte-tightly-packed 해석 규칙에 따라 송수신하여야 한다. 이 규칙을 만족하지 않는 OfferService entry는 유효한 SD entry로 해석하거나 처리하여서는 안 된다.

## Notes


