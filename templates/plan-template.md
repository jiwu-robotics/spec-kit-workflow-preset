{CORE_TEMPLATE}

## X0 Feature Plan Control

### Feature Goal And Exclusions

- **Goal**: [Feature outcome.]
- **Exclusions**: [Explicit non-goals.]
- **Planned M + U**: [Module/capability + design object.]
- **Repository Topology**: [Core-required source/test directory topology only.]

### Upstream References

- **Spec**: [path + revision]
- **Consumed Spec SHA-256**: [sha256:<64 lowercase hexadecimal characters>]
- **Spec Source Contract**: [Applicable local SRC refs and blockers; locators remain opaque.]
- **Architecture Revision**: [revision]
- **Applicable Architecture IDs**: [BND/CON/DEC/CST/GAP refs]

The Spec digest is local freshness evidence. It does not certify an external
source, revision, locator, or baseline. The same digest is recorded in
`ui-ux-design.md` when X2-B is active.

### Active Lane Matrix

| Lane | Applicability | Source refs | Declared outputs | Dependencies | Internal gate |
|---|---|---|---|---|---|
| X2-A Domain/Object/Interface | Required / N/A: reason / Blocked: ID | [refs] | [paths] | [lane refs] | X2A_DESIGN_READY |
| X2-B UI/UX Delivery | Required / N/A: reason / Blocked: ID | [SRC + UX or UI/VIS/RST/PXR/PXT/PEX/ADP refs; explicit non_graphical for terminal/report UX] | [paths] | [lane refs] | X2B_UIUX_READY |
| X2-C Test & Acceptance | Required / N/A: reason / Blocked: ID | [refs] | [paths] | [lane refs] | X2C_TEST_DESIGN_READY |

An N/A X2-B decision records both the scoped `spec.md` section/ref and the
concrete reason that no applicable UX/UI contract ref exists. Applicable UX
terminal/report delivery activates X2-B using existing `general-ui` /
`X2B-UI-*` mappings with explicit `delivery_kind: non_graphical`, matching UX
UIF ownership, and no Canonical/visual bindings. Graphical delivery remains
the default; explicit UI/VIS N/A exclusions stay unmapped.

### Stage-Owned Artifact Decisions

| Artifact | Owning stage | Applicability | Readiness evidence / root blocker |
|---|---|---|---|
| Test Conditions and selected technique children | X2-C | Required / N/A: reason / Blocked: ID | [Independent X2C_TEST_DESIGN_READY design evidence.] |
| quickstart.md | X3 | Required / N/A: reason / Blocked: ID | [X3_VALIDATION_PATHS_READY path evidence or explicit rooted dependency block.] |
| test-readiness.md | X4 final derivation | Required / N/A: reason / Blocked: ID | [Closed TC/VAL rows or explicit rooted block in X2_RECONCILIATION_READY.] |

X2-C Required/READY does not force later quickstart or final readiness to be
Required before their gates close. Preserve independently complete design;
later blocked artifacts retain their real stage owner and reference the
registered root blocker rather than adopting its ownership.

### Cross-Lane Dependency Register

| ID | Producer | Consumer | Required contract/decision | Status/blocker |
|---|---|---|---|---|

### Internal Gate Summary

| Gate | READY / BLOCKED / N/A | Evidence / blocker |
|---|---|---|
| X0_CONTROL_READY | [status] | [ref] |
| X1_DECISIONS_READY | [status] | [ref] |
| X2A_DESIGN_READY | [status] | [ref] |
| X2B_UIUX_READY | [status] | [ref] |
| X2C_TEST_DESIGN_READY | [status] | [ref] |
| X2_RECONCILIATION_READY | [status] | [inventory/findings/blocker refs] |
| X3_VALIDATION_PATHS_READY | [status] | [ref] |

Each status is derived from the cited evidence. File existence alone is not
evidence. A missing or invalid evidence cell means the Gate is not ready.

### X2 Cross-Lane Reconciliation

| Ref / mapping | Producer / owner | Consumers | Resolved target | Drift / ownership finding | Status / blocker |
|---|---|---|---|---|---|
| [DEC/X2B/UIF/TC/VAL/design ref] | [lane + artifact] | [lane artifacts] | [stable ID/path] | [none or finding] | [READY/BLOCKED: ID] |

### Root Blocker Ownership

| Blocker ID | Original owning lane | Root evidence | Dependent artifacts / gates | Dependency / propagation evidence |
|---|---|---|---|---|
| [stable root ID] | [actual root owner] | [artifact/ref] | [artifact + BLOCKED gate citing the same ID] | [dependency/reconciliation refs] |

Register every propagated root in reconciliation `blocker_owners`; dependent
gate records include `status`, `evidence`, and `blockers`. A blocked quickstart
requires explicit X3 gate evidence; blocked final readiness requires explicit
reconciliation gate evidence. No hidden/unregistered blocker, root-owner
reassignment, or premature final READY is allowed.

### Resume Checkpoint

- **Current local Spec SHA-256**: [sha256:<digest>]
- **Recorded X0 / UI-UX Spec SHA-256**: [digests or N/A for inactive X2-B]
- **First unclosed/affected Gate**: [Gate ID]
- **Verified artifacts preserved**: [paths + evidence refs]
- **Changed inputs/refs**: [refs or none]
- **Downstream Gates/reconciliation to rerun**: [Gate IDs]

If the current digest differs from either recorded digest, treat the Spec input
as changed even when stable IDs are unchanged. Invalidate affected X2-B,
reconciliation, X4, and `PLAN_OUTPUT_READY` evidence before rebuilding.

## Artifact Navigation

- Shared decisions: `./research.md`
- Domain model: `./data-model.md`
- Object responsibilities: `./class-diagram.md`
- Interface contracts: `./contracts/`
- Cross-boundary sequences: `./contracts/sequences.md`
- UI/UX delivery design: `./ui-ux-design.md`
- UI interaction contracts: `./contracts/uif/`
- Test Conditions: `./contracts/test/test-conditions.json`
- Optional technique contracts: `./contracts/bdd/`, `./contracts/behavior/`
- Validation paths: `./quickstart.md`
- Test readiness: `./test-readiness.md`

Remove links for explicitly N/A artifacts; do not leave broken placeholders.

## X4 Design Object Derivation Index

| Source refs | Architecture refs | M | U / design object | Data-model ref | Class ref | Interface/sequence refs | Blocker |
|---|---|---|---|---|---|---|---|

No task IDs, exact per-task paths, or implementation order belong here.

## X4 Closeout Summary

- **Design Readiness**: [READY/BLOCKED + index link]
- **UI/UX Delivery Readiness**: [READY/BLOCKED/N/A + link/reason]
- **Test Readiness**: [READY/BLOCKED/N/A + link/reason]
- **X3 Validation Paths**: [READY/BLOCKED/N/A]
- **Blockers by lane**: [IDs]
- **PLAN_OUTPUT_READY**: READY | BLOCKED

`PLAN_OUTPUT_READY` is derived from the Internal Gate Summary, reconciliation,
conditional artifact decisions, readiness products, resolved refs, and
placeholders. All applicable outputs and readiness rows must close before
READY. Valid rooted propagation preserves blocked-state evidence only; it
does not close an output or invalidate independent X2-C design. Do not mark
READY from file presence or prose summary alone.
