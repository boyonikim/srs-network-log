---
uid: SRS-UID-d71884d7f638
id: SRS-SomeIP-ServiceDiscovery-0042
cb_id: 40438693
domain: someip
parent: SRS-UID-88c1c630dd53
title: InitialDataRequested Flag Setting
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0037
- SRS-SomeIP-ServiceDiscovery-0077
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 initial event를 요청하는 경우 SubscribeEventGroup SD 엔트리의 InitialDataRequested 플래그를 설정하여 service provider로 전송하여야 한다.
## Notes
