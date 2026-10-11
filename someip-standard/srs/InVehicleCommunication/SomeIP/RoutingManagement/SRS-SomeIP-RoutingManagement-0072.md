---
uid: SRS-UID-1b035ba15cdc
id: SRS-SomeIP-RoutingManagement-0072
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Event Notification UDP Transport Policy
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

SOME/IP Routing Management 소프트웨어는 재등록 및 service discovery 재개 시 각 service 또는 Method에 대해 transport policy를 적용할 때, 프로젝트 설정으로 고정 주기 반복 전송하도록 구성된 Event/notification이면서 delivery requirement가 best-effort(유실 허용)이고 SOME/IP payload size가 표준 Ethernet MTU 1500B에서 IP/UDP/SOME/IP header overhead를 제외한 1400 bytes 이하인 경우 UDP를 선택하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 해당 Event/notification의 delivery requirement 설정값 또는 payload size 설정값이 프로젝트 설정에 정의되어 있지 않으면 transport policy 평가 실패로 처리하여야 하며, 두 설정값이 모두 정의될 때까지 해당 Event/notification의 transport 선택을 완료한 것으로 처리하지 않아야 한다.

## Notes


