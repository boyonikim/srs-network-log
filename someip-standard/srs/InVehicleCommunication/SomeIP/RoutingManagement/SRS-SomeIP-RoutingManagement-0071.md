---
uid: SRS-UID-aa9f58d2c76e
id: SRS-SomeIP-RoutingManagement-0071
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Large Payload Transport Policy
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
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 재등록 및 service discovery 재개 시 각 service 또는 Method에 대해 transport policy를 적용할 때 오류 복구에 대한 hard latency 제약이 없고 SOME/IP payload size가 표준 Ethernet MTU 1500B에서 IP/UDP/SOME/IP header overhead를 제외한 1400 bytes를 초과하는 경우 TCP를 선택하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 오류 복구에 대한 hard latency 제약이 있어 SOME/IP payload size가 1400 bytes를 초과하더라도 UDP 사용이 필수이면 UDP를 선택하고, 이 경로에서 payload를 UDP MTU 기준으로 SOME/IP-TP segmentation 및 reassembly를 적용하여 전송하여야 한다.

## Notes


