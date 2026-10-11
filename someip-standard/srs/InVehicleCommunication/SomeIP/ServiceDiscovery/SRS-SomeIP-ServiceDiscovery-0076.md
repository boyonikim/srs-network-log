---
uid: SRS-UID-969365985a84
id: SRS-SomeIP-ServiceDiscovery-0076
cb_id: 40594163
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Unavailable Notification after Resubscription Exhaustion
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0063
- SRS-SomeIP-ServiceDiscovery-0002
- SRS-SomeIP-ServiceDiscovery-0045
- SRS-SomeIP-ServiceDiscovery-0015
- SRS-SomeIP-ServiceDiscovery-0024
- SRS-SomeIP-ServiceDiscovery-0054
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 EventGroup 재구독의 최초 전송 및 허용된 모든 재전송에 대한 응답 대기 시간이 만료될 때까지 SubscribeEventGroupAck 또는 SubscribeEventGroupNack을 수신하지 못하고 더 이상 허용된 재전송 횟수가 남아 있지 않아 해당 EventGroup subscription을 종료한 경우, consumer application에 해당 EventGroup의 재구독 실패에 대한 Service Unavailable을 통지하여야 한다.
SOME/IP Service Discovery 기능은 해당 service의 유효한 OfferService가 유지되는 경우 EventGroup 재구독 실패 및 subscription 종료만을 이유로 해당 service의 consumer 가용성 상태를 ServiceNotAvailable로 전이하여서는 안 된다.

## Notes
