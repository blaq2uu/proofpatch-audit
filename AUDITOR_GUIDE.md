# Independent Reviewer Guide

This repository is the independent audit publisher for ProofPatch.

## What this framework is

This commit should initialize the audit publisher only. It is NOT an audit approval and must not contain a passing evidence JSON file.

## What to review later

When a ProofPatch upgrade proposal is ready, the reviewer should independently inspect:

1. the exact current/parent source;
2. the exact candidate source bytes;
3. the candidate SHA-256;
4. persistent storage compatibility;
5. owner/user rights;
6. privilege escalation or alternate admin paths;
7. preservation of ProofPatch as the only upgrade authority;
8. consensus-binding semantics;
9. evidence trust boundaries;
10. finality safety;
11. liveness and recovery semantics;
12. hidden value-transfer or mutation paths;
13. the registered ProofPatch security constitution.

## Evidence authoring rule

Only after the independent review is complete should the reviewer create a new file under `evidence/`.

The evidence object must match:

`schema/proofpatch-audit-evidence-v1.schema.json`

The reviewer must use the real:

- target address;
- parent SHA-256;
- candidate SHA-256;
- policy fingerprint;
- publication timestamp;
- expiry timestamp;
- unique evidence ID.

Then commit the evidence and provide the exact 40-character commit SHA.

ProofPatch must reference the immutable raw GitHub URL at that commit, never `main`.

## Critical independence requirement

Do not accept or publish a PASS statement supplied by the application owner without doing the review yourself.

`independent_review: true` is a factual attestation by the independent reviewer.
