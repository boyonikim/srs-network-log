{
  "output_path": "/home/worker/workspace/someip-standard/.srs-run/staging/RUN-a2edfd568f63/review-domain.review.json",
  "schema_validation": "PASS against contracts/review-submission.schema.json",
  "scope": "44 RoutingManagement leaf items (role:target, subject_type:leaf, evaluation_scope:self, 33 fresh CHK rules each: SOMEIP-CHK-001..032,035) + 1 module-scope group target (SOMEIP-CHK-033,034 over all 44 member items). 15 ServiceDiscovery leaves used read-only as role:context for cross-module comparison, no independent verdict produced for them.",
  "decision_counts": {
    "total": 1454,
    "PASS": 1453,
    "FAIL": 1,
    "BLOCKED": 0
  },
  "execution_status": "SUCCEEDED",
  "fail_finding": "SRS-SomeIP-RoutingManagement-0088 (Registration Rejection Error Response), SOMEIP-CHK-028 (application_interface / error code propagation), severity MAJOR, reason_code content_defect, actionability edit. The item returns a wire-level SOME/IP error Return Code (defined only for SOME/IP Message Type REQUEST/RESPONSE/ERROR headers per SOMEIP-K-0039#C4 and SOMEIP-K-0014#C3, R24-11) as the return value of an internal, non-wire 'registration request API' between the local application and the RoutingManagement middleware. This conflates a wire-protocol field with a local interface's error contract.",
  "knowledge_evidence_files": [
    "evidence/sd-offer-phases.json (SOMEIP-SD-SPEC R22-11: Initial Wait/Repetition/Main phase parameters, StopOffer/subscription deletion on link-down, Subscribe/Ack/Nack semantics)",
    "evidence/transport-mtu.json (SOMEIP-PROTOCOL-SPEC R24-11: SOME/IP header size, UDP recommended payload 0..1400B, SOME/IP-TP segment/header format)",
    "evidence/return-code-scope.json (SOMEIP-PROTOCOL-SPEC R24-11: Return Code scope limited to Method Request/Response/Error message headers)",
    "evidence/find-repetition.json (NEEDS_SCOPE; not used as grounding for any decision, retained for completeness)"
  ],
  "key_grounded_pass_areas": [
    "SD Initial Wait/Repetition/Main phase parameter naming distributed correctly across items 0075/0094/0095 with explicit cross-references",
    "Subscribe TTL/Ack/Nack/retry fully specified in item 0086",
    "Graceful vs ungraceful Unsubscribe/StopOffer paths correctly and mutually-exclusively distributed across items 0017/0058/0062/0092/0093",
    "Transport selection (TCP/UDP, 1400B threshold, SOME/IP-TP segmentation) in items 0048/0071/0072/0073 matches protocol evidence",
    "No vsomeip API leakage or implementation-mechanism (layering/CHK-035) findings across any of the 44 items",
    "No semantic-duplication (CHK-033) or Method/Field conflation (CHK-034) found across the 44-item module after cross-comparison of visually similar item pairs (all distinguished by explicit, documented trigger/condition differences)"
  ],
  "not_in_scope_noted": "Item 0036's Notes cross-reference a non-existent UID (SRS-UID-d6ff734e0cea) for FindService retry; this is a dangling-reference defect outside the SOME/IP domain checklist (RE-axis concern, not a CHK-NNN rule) and was not scored here, consistent with the task's domain-only mandate."
}