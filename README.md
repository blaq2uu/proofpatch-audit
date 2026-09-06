# ProofPatch Independent Audit Evidence

Independent audit evidence publisher for ProofPatch consensus-gated GenLayer upgrades.

## Purpose

This repository publishes independent machine-readable security audit evidence consumed by the deployed `ProofPatchGovernor`.

This repository is intentionally owned by a GitHub publisher distinct from the protected application source publisher.

## Registered authority

When the Bradbury target policy is registered, this repository is intended to use:

- authority identifier: `blaq2uu/proofpatch-audit`
- raw GitHub prefix: `https://raw.githubusercontent.com/blaq2uu/proofpatch-audit/`

The on-chain ProofPatch policy is the authoritative registration record.

## Immutable evidence rule

Every audit evidence URL supplied to ProofPatch must contain an exact 40-character Git commit SHA.

Branch URLs such as `main` must never be used as proposal evidence.

Valid form:

```text
https://raw.githubusercontent.com/blaq2uu/proofpatch-audit/<40-hex-commit>/evidence/<record>.json
```

Audit records are append-only reviewer artifacts.

If an audit record needs correction:

1. create a new record;
2. use a new evidence ID;
3. commit it;
4. reference that exact immutable commit.

Do not reuse an evidence ID already consumed by a ProofPatch proposal.

## Audit evidence contract

The deployed governor expects schema:

```text
proofpatch-evidence-v1
```

with evidence kind:

```text
audit
```

Every record binds:

- protected target address;
- parent source SHA-256;
- candidate source SHA-256;
- ProofPatch policy fingerprint;
- registered audit issuer;
- unique evidence ID;
- publication timestamp;
- expiry timestamp;
- verdict `PASS`;
- `independent_review: true`.

## Independence rule

Do not publish `verdict: "PASS"` or `independent_review: true` unless the reviewer independently inspected the exact candidate source and relevant ProofPatch policy/security constraints.

The repository owner should not accept write access from the protected application's source publisher for audit evidence authoring.

## Publication discipline

Do not publish a passing audit evidence record until:

- the exact candidate bytes are frozen;
- the exact candidate SHA-256 is known;
- the current parent SHA-256 is known;
- the target policy fingerprint is known;
- the candidate has actually been independently reviewed;
- the timestamps describe the real audit publication window.

There is deliberately no fabricated PASS evidence in this repository.
