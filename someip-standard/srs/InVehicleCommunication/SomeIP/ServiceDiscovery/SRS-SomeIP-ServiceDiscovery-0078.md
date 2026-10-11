---
uid: SRS-UID-fa4a6fbd36fb
id: SRS-SomeIP-ServiceDiscovery-0078
cb_id: 40610562
domain: someip
parent: SRS-UID-88c1c630dd53
title: SD Endpoint Role Selection
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0029
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 SD endpoint를 multicast와 unicast로 구분하여 사용하여야 하며, service discovery announcement에는 multicast endpoint를, directed FindService 및 SubscribeEventgroup에는 unicast endpoint를 사용하여야 한다.

## Notes
