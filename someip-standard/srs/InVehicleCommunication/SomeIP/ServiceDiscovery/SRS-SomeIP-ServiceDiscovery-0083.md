---
uid: SRS-UID-52b56b33d16b
id: SRS-SomeIP-ServiceDiscovery-0083
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: SOME/IP Service Discovery SD Entry Wire Format
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: data_logic
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 SubscribeEventGroup entry의 Service ID, Instance ID, EventGroup ID, TTL 필드를 SOME/IP PRS의 big-endian byte order로 수신 및 해석하고 각 필드 사이에 alignment padding이 없는 byte-tightly-packed 값으로 해석하여야 한다.
SOME/IP Service Discovery 기능은 OfferService, FindService, StopOfferService 및 StopSubscribeEventGroup을 포함하여 송수신하는 모든 SD entry의 동일 타입 Service ID, Instance ID, EventGroup ID 및 TTL 필드에 동일한 byte order 및 padding 규칙을 적용하여야 한다.
SOME/IP Service Discovery 기능은 해당 byte order 및 padding 규칙을 만족하지 않는 SD entry를 유효한 SD entry로 해석하거나 처리하여서는 안 된다.

## Notes

