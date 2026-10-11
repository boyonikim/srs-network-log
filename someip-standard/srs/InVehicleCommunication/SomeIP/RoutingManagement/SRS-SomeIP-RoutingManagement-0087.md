---
uid: SRS-UID-354ded1a7d89
id: SRS-SomeIP-RoutingManagement-0087
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: EventGroup Subscription Re-registration Preconditions
status: Draft
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
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 재시작 완료 전이거나 재연결하는 local application으로부터 EventGroup 구독 요청을 수신하지 않은 경우 SubscribeEventGroup 절차를 개시하지 않아야 한다.

## Notes
