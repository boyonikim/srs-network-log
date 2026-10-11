---
uid: SRS-UID-5fc43d086f0b
id: SRS-SomeIP-RoutingManagement-0079
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: EventGroup Subscription Re-registration After Abnormal Termination
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0087
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 비정상 종료 후 재시작 완료 시, 재연결하는 local application으로부터 재수신되는 EventGroup 구독 요청을 신규 EventGroup 구독 요청으로 수용하여 SubscribeEventgroup 절차를 개시하여야 한다.

## Notes
