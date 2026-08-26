# BILL 2.0 - Public Architecture and Method Note

This note describes the project at a level appropriate for a public portfolio. The private repository contains the implementation, operational contracts, infrastructure configuration, provider bindings, receipts, test suite, and detailed evidence.

## 1. Product boundary

BILL 2.0 is designed around a strict separation between source facts, deterministic processing, hosted execution, durable state, and presentation.

```text
Governed Sources
    -> normalization / validation
    -> Ledger + domain processing
    -> hosted execution
    -> immutable or durable derived state
    -> controlled read / command boundaries
    -> Product Workbench
```

The UI is intentionally not allowed to become the canonical financial authority. Browser caches and local UI state do not replace durable product state.

## 2. Current capability families

The private system contains capability families for:

- governed financial source intake;
- Ledger and accounting state;
- market evidence and valuation;
- PnL, performance, attribution, and reconciliation;
- historical financial reconstruction;
- hypothetical backtesting;
- governed pre-Ledger intake and merge workflows;
- hosted read and command services;
- durable lifecycle execution and recovery;
- Product and Audit Workbench surfaces.

This public description deliberately avoids live counts, mutable deployment IDs, and other metrics that would become stale in a static portfolio.

## 3. Human-AI development loop

The core development process is incremental:

1. **Define intent** - expected behavior, constraints, boundaries, and acceptance criteria.
2. **AI-assisted implementation** - AI is used heavily for analysis, design, code, refactoring, and documentation.
3. **Challenge the output** - targeted tests, behavioral checks, QA/UAT, regression tests, and operational probes.
4. **Inspect evidence** - logs, durable records, readback, receipts, and reproducible results.
5. **Accept, reject, or refine** - a green command or passing isolated test is not sufficient if behavior diverges from intent.
6. **Externalize learning** - recurring failures are turned into tests, contracts, guardrails, or procedures so the same class of mistake becomes harder to repeat.

This structure also reduces dependence on conversation memory during long-running AI-assisted work. Important state and decisions are preserved as versioned artifacts and machine-readable evidence.

## 4. Machine-readable receipts and evidence

The project treats traceability as a first-class feature rather than an afterthought.

Governed implementation and execution paths produce structured records that can bind:

- logical operation identity;
- time and status;
- input/request digests;
- implementation surface or produced artifacts;
- immutable hashes;
- idempotency and recovery information;
- execution boundaries;
- acceptance/failure state;
- readback and qualification evidence.

The exact private schemas are intentionally not reproduced here. The sanitized examples in `examples/` illustrate the concept without exposing operational details.

## 5. Failure handling philosophy

A recurring rule is:

> A technically green result is not enough.

The project distinguishes at least four questions:

1. Did the implementation or command run?
2. Did the relevant checks pass?
3. Does the evidence describe the expected state?
4. Does the observed behavior actually match the intended behavior?

A mismatch can therefore remain a failure even when individual commands are technically successful.

Likewise, ambiguous remote state does not authorize blind replay. The system favors observation/readback and bounded recovery over repeating uncertain mutations.

## 6. Transferable work demonstrated

Although the domain is financial data, the development process demonstrates broader skills relevant to operations, AI quality, and data work:

- structured problem definition;
- data-quality thinking;
- QA/UAT;
- consistency checking;
- error pattern analysis;
- failure investigation;
- acceptance criteria;
- documentation and handoff;
- workflow design;
- evidence-based decision making;
- process improvement.

## 7. Public/private boundary

The private engineering repository is not public. This portfolio intentionally excludes:

- source code;
- credentials and secrets;
- provider/project identities;
- private service URLs;
- raw financial data;
- production operational receipts;
- infrastructure mutation commands.

The goal is to show **how the project is reasoned about and validated**, without turning a private operational system into a public code dump.
