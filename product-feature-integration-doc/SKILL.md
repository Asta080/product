---
name: product-feature-integration-doc
description: Analyze vague product delivery tasks together with existing specifications, checklists, integration proposals, new requirements, and product decisions; abstract the desired outcome, current state, gaps, deliverables, and rollout stages; identify conflicts and classify capabilities as unchanged, modified, added, removed, or out of scope; then create or update concise Markdown feature specifications, delivery plans, and development handoff documents. Use when Codex needs to turn a request such as planning optimization and product implementation into a reusable delivery workflow, consolidate product documents, merge an integration plan into a specification, compare current behavior with planned behavior, clarify development scope, or revise documents after product decisions.
---

# Product Feature Integration Documents

Create product documents that distinguish current facts from planned changes and give product, design, engineering, and QA one consistent implementation baseline.

## Start with the delivery abstraction

When the request is vague (for example, “plan the follow-up optimization and product rollout”), do not jump straight to a next-step list. First convert the request into five anchors:

1. **Outcome** — what observable user, product, and project results should exist when the work is complete;
2. **Current state** — what is already live and retained, live but changing, planned but missing, explicitly excluded, or unresolved;
3. **Gap** — what is missing between the current state and the desired outcome;
4. **Deliverables** — which artifacts close each gap;
5. **Stages** — the order in which decisions, design, implementation, validation, release, and learning close those gaps.

Scan the gap across seven dimensions: value, scope, rules, experience, capability, collaboration, and verification. Use this compact mapping:

| Gap | Typical product artifact |
|---|---|
| Value or direction unclear | Outcome statement and success measures |
| Scope or current behavior unclear | Scope table and unchanged/modified/added/removed/out-of-scope matrix |
| Rules or state transitions unclear | Flow, state model, edge-case and failure rules |
| Experience unclear | High-fidelity interactive prototype and state coverage |
| Capability or dependency unclear | Technical boundary, compatibility matrix, and ownership table |
| Team understanding inconsistent | Review-ready specification and development handoff |
| Completion or launch confidence unclear | Checklist, acceptance criteria, regression baseline, metrics, and rollback conditions |

Only after these anchors are clear, convert stages into concrete actions. Every stage must state: the problem it closes, the artifact or decision it produces, who must confirm it, and the evidence that marks completion.

For unfamiliar domains, use the three-question abstraction loop on each concrete issue:

1. What immediate problem is this issue solving?
2. Which of the seven dimensions does it belong to?
3. Would the same class of problem appear in another feature?

Use the higher-level answer to check for sibling cases before solving only the isolated event.

## Select the deliverable

- Use `assets/feature-spec-template.md` when the audience needs the complete feature: context, scope, integration, detailed rules, system requirements, acceptance, and open decisions.
- Use `assets/development-handoff-template.md` when engineering primarily needs the delta: unchanged, modified, added, removed, out of scope, conflicts, dependencies, and decisions.
- When asked to update an existing document, preserve its useful structure and terminology instead of forcing the template verbatim.
- When both are useful, create the complete specification first and derive the shorter handoff from it.

## Workflow

### 1. Establish sources and current truth

Read every supplied specification, checklist, integration proposal, decision note, and relevant current-state document before drafting.

Separate statements into:

- verified current behavior;
- planned behavior;
- user-confirmed decisions;
- assumptions or unresolved decisions.

Treat the user's explicit correction about current behavior as authoritative unless it conflicts with a newer supplied source. Never infer that a capability is new merely because it is emphasized in the new plan.

### 2. Build the change model

Classify every material capability:

| Classification | Meaning |
|---|---|
| Unchanged | Current behavior remains; include it in regression coverage |
| Modified | Capability remains, but its rule, state, interaction, ownership, or data behavior changes |
| Added | Capability or user-visible/system behavior does not exist in the verified current state |
| Removed | Current or legacy behavior must no longer exist because it conflicts with the target definition |
| Out of scope | Explicitly excluded from this delivery; do not treat it as deleted unless it currently exists and removal is intended |

For conflicts, record current behavior, target behavior, resolution, and affected teams or modules. If evidence is insufficient to classify an item, ask the user. If the user is also uncertain, leave the decision visibly blank and add it to the open-decision table.

### 3. Resolve duplication and contradictions

- Keep each authoritative rule in one primary section; use short cross-references elsewhere.
- Prefer the newest explicit product decision over earlier proposals and update every dependent section.
- Remove resolved items from the open-decision table.
- Keep unresolved values blank; do not invent product parameters, defaults, thresholds, compatibility matrices, copy, layout, or motion.
- Distinguish business behavior from implementation detail. Include interfaces and ownership only when they clarify delivery boundaries.
- Let high-fidelity prototypes own layout, visual styling, motion, and control-state details; let the document own rules, states, conditions, scope, and failure behavior.

### 4. Draft the document

Lead with the outcome and development delta. Use compact tables for comparisons and mappings. Keep prose concise, comprehensive, and testable.

For a full feature specification, normally organize:

1. overview and objectives;
2. product scope and principles;
3. page or system integration;
4. functional requirements;
5. data and system requirements;
6. acceptance and regression;
7. open decisions and review record.

For a development handoff, normally organize:

1. delivery objective;
2. change classification and conflict summary;
3. unchanged;
4. modified;
5. added;
6. removed;
7. out of scope;
8. team handoff and prototype coverage;
9. open decisions and sign-off.

Do not repeat the complete original specification in a handoff document. Link or reference the authoritative specification for detailed rules.

### 5. Apply subsequent decisions consistently

When the user supplies a new decision:

1. locate every affected statement;
2. update the classification, current/target comparison, detailed rule, acceptance impact, and team handoff;
3. remove or revise conflicting old language;
4. remove the item from open decisions if fully resolved;
5. preserve unrelated content.

### 6. Version and validate

- Preserve input files by default and write a new version unless the user explicitly requests in-place editing.
- Use the source document's version convention when one exists; otherwise use a clear next version.
- Verify heading hierarchy, numbering, cross-references, terminology, classification consistency, unresolved blanks, and absence of stale decisions.
- Confirm that project-specific names, rules, and parameters appear only when supplied for the active project, never because they were embedded in this skill.

## Delivery planning output

When the user asks for a rollout or implementation plan rather than a specification, use this compact structure before producing detailed tasks:

```markdown
# [Feature] Delivery Plan

## Outcome
- User result:
- Product result:
- Project result:

## Current state
- Retain:
- Modify:
- Add:
- Remove:
- Out of scope:
- Open decisions:

## Gaps
| Dimension | Gap | Impact if unresolved |
|---|---|---|
| Value / scope / rules / experience / capability / collaboration / verification | [Gap] | [Impact] |

## Key deliverables
| Deliverable | Gap closed | Owner | Confirmers | Definition of done |
|---|---|---|---|---|

## Stages
| Stage | Problem closed | Output | Dependencies | Completion evidence |
|---|---|---|---|---|

## Risks and decisions
| Question or risk | Impact | Decision owner | Due date | Result |
|---|---|---|---|---|

## Launch and learning
- Acceptance:
- Regression:
- Rollout:
- Metrics:
- Rollback:
```

Keep this plan at the outcome-and-deliverable level unless the user asks for an execution task list. When tasks are requested, derive them from the stages and preserve the link to the artifact or decision each task closes.

## Quality checks

Before delivery, confirm:

- every planned item is classified exactly once at the summary level;
- existing capabilities are not presented as new;
- “removed” and “out of scope” are not conflated;
- conflicts have explicit resolutions or visible blanks;
- user decisions are reflected everywhere they affect;
- engineering can identify its work without interpreting product intent;
- design can identify which states and interactions require a prototype;
- QA can identify regression baselines and changed acceptance behavior;
- the document is concise and contains no avoidable repetition.
