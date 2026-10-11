---
uid: SRS-UID-caaf809a23e5
id: SRS-SomeIP-ServiceDiscovery-0085
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: OfferService Response Priority for FindService
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter:
- uid: SRS-UID-f8f5a0fc4391
  cb_id: 40466965
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

SOME/IP Service Discovery 기능은 FindService 수신 시 다음 우선순위로 OfferService 응답을 처리하여야 한다.

1. service provider가 Repetition Phase에서 FindService를 수신하거나, unicast flag가 0으로 설정된 FindService를 수신하거나, 해당 service가 가용 상태가 아니면 OfferService를 전송하지 않아야 한다.
2. service provider가 Main Phase에서 가용 상태인 service에 대해 unicast flag가 1인 FindService를 unicast로 수신하면 지연시간을 적용하지 않고 해당 FindService를 송신한 consumer의 unicast endpoint로 OfferService를 전송하여야 한다.
3. service provider가 Main Phase에서 가용 상태인 service에 대해 unicast flag가 1인 FindService를 multicast endpoint로 수신하면 {P_SD_RequestResponseDelay_Min} 이상 {P_SD_RequestResponseDelay_Max} 이하 범위의 균등 분포 난수로 지연시간을 새로 선택하고, 선택한 시간 동안 대기한 후 해당 FindService를 송신한 consumer의 unicast endpoint로 OfferService를 전송하여야 한다.

※ 예외 규칙: SOME/IP Service Discovery 기능은 FindService를 수신하지 않은 경우 OfferService 응답을 전송하지 않아야 한다.
## Notes


