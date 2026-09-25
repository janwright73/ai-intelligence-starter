# Ansible and Hummingbird comprehensive rule catalog

## Review scope

Reviewed on 2026-09-25:

- Current Ansible/Syntara [`frontend-patternfly-ux`](https://github.com/syntara-orchestration/syntara/blob/devel/.claude/skills/frontend-patternfly-ux/SKILL.md), commit `cf9dc06`.
- Legacy Automation Nexus [`frontend-patternfly-ux`](https://github.com/automation-nexus/nexus-combined/blob/devel/.claude/skills/frontend-patternfly-ux/SKILL.md), commit `eab245b`, used as provenance for rules carried into Syntara.
- Hummingbird [`outline-first-ui`](https://gitlab.com/redhat/hummingbird/tools/-/tree/main/.cursor/skills/outline-first-ui), commit `7bccf40`.
- Hummingbird [`visible-scaffolding`](https://gitlab.com/redhat/hummingbird/tools/-/tree/main/.cursor/skills/visible-scaffolding), commit `7bccf40`.

This is a normalized rule catalog, not a copy of the source skills. Repeated checklist items, examples, component paths, API endpoints, exact copy strings, and restatements were consolidated into one rule. Product implementation details remain traceable through the source section.

## Classification

| Layer | Meaning |
|---|---|
| Felt candidate | Cross-product UX intent or behavior to review for a FELTRFE-75 canonical record |
| AI-helper workflow | A repeatable agent planning, retrieval, implementation, or verification step |
| PatternFly reference | Current PF component API, token, variant, or documented composition; retrieve rather than duplicate |
| Product overlay | Product wrappers, architecture, routes, terminology, exceptions, or implementation mappings |
| Mixed | Portable intent plus product-specific realization |

Priority indicates the recommended next action: `seed` for the first Felt catalog, `evaluate` for cross-product comparison, `helper` for AI Helpers, `overlay` for product ownership, and `reference` for PatternFly retrieval.

## Ansible/Syntara rules

### Design-system use and component selection

| Rule ID | Normalized rule | Layer | Priority | Source section |
|---|---|---|---|---|
| ANS-DS-001 | Use PatternFly as the default component, pattern, accessibility, layout, and theming foundation. | PatternFly reference | reference | Design System |
| ANS-DS-002 | Before creating custom UI, search current PatternFly components, variants, tokens, and examples. | AI-helper workflow | helper | PatternFly gaps |
| ANS-DS-003 | A suspected PatternFly gap must be reviewed with UX before a custom solution is accepted. | AI-helper workflow | helper | PatternFly gaps |
| ANS-DS-004 | Confirmed gaps should be raised upstream; temporary overrides need provenance, ownership, an issue, and a removal path. | Mixed | evaluate | PatternFly gaps |
| ANS-DS-005 | Prefer standardized compositions over feature-specific combinations of atomic components. | Felt candidate | evaluate | Opinionated implementation |
| ANS-DS-006 | Use established `Syn*` wrappers instead of reconstructing the same composition from raw PatternFly components. | Product overlay | overlay | `Syn` prefix convention |
| ANS-DS-007 | Do not introduce a custom one-off when an existing PatternFly or product primitive can be extended. | AI-helper workflow | helper | Addressing gaps |
| ANS-DS-008 | Use current library documentation before writing React, Zod, Zustand, or other library-dependent code. | AI-helper workflow | helper | Skill preamble |

### Navigation, page structure, and composition

| Rule ID | Normalized rule | Layer | Priority | Source section |
|---|---|---|---|---|
| ANS-NAV-001 | Navigation items with children expose a flyout; items without children navigate directly and show a label tooltip. | Product overlay | overlay | Side Navigation Structure |
| ANS-NAV-002 | Selecting a flyout child closes the flyout immediately; pointer movement between trigger and flyout must not cause flicker. | Felt candidate | evaluate | Side Navigation behavior |
| ANS-NAV-003 | Every page uses one consistent hierarchy: app shell, navigation, page wrapper, page header, content panel, main content, and contextual footer. | Mixed | evaluate | Page Layout |
| ANS-NAV-004 | Preserve the page shell and page identity when showing loading, error, or empty content. | Felt candidate | seed | Page Layout Archetypes |
| ANS-NAV-005 | Choose a canonical page archetype—list, detail, form, error-in-panel, or stacked panels—before composing the page. | Felt candidate | evaluate | Page Layout Archetypes |
| ANS-NAV-006 | Use a shared full-height content stack so nested scroll regions resolve height correctly. | Product overlay | overlay | Panel Content Stack |
| ANS-NAV-007 | Stack sibling panels through the product stack primitive; clip or scroll inside panels, not on an ancestor that would cut off elevation. | Product overlay | overlay | Stacked Panels |
| ANS-NAV-008 | Page headers contain the page title and primary actions; the title matches the navigation label and uses one semantic page title. | Felt candidate | evaluate | Page Header Structure |
| ANS-NAV-009 | Breadcrumbs represent actual accessible navigation and must not point to routes the user cannot open. | Felt candidate | seed | Breadcrumbs; Permission Gating |
| ANS-NAV-010 | Tabs represent peer views; use stable URLs and validate the active tab against the set currently available to the user. | Mixed | evaluate | Tabs |

### Lists, tables, filters, details, and forms

| Rule ID | Normalized rule | Layer | Priority | Source section |
|---|---|---|---|---|
| ANS-DATA-001 | A list surface uses one shared composition for query state, toolbar, table, empty states, and pagination. | Mixed | evaluate | `SynListPanel` |
| ANS-DATA-002 | Disable list filters and controls during refetch while preserving existing content and announcing the update to assistive technology. | Felt candidate | seed | `SynListPanelToolbar` |
| ANS-DATA-003 | Show filters when data exists or filters are active; hide them only for a truly empty first-use state. | Felt candidate | evaluate | Empty States |
| ANS-DATA-004 | Distinguish first-use empty, filtered-empty, service error, invalid identifier, not found, access denied, configuration-required, and success states. | Felt candidate | seed | Empty States |
| ANS-DATA-005 | A filtered-empty state offers a clear-filters recovery action; a service error offers retry; an invalid or missing resource offers navigation back. | Felt candidate | seed | Empty States |
| ANS-DATA-006 | Avoid duplicate primary CTAs: when the empty state owns the create/configure action, hide the equivalent page-header action. | Felt candidate | evaluate | Empty States |
| ANS-DATA-007 | Empty-state size, heading level, status, and icon semantics follow the containing surface rather than being selected ad hoc. | PatternFly reference | reference | Empty State variants |
| ANS-DATA-008 | Tables use semantic column headers, a standardized scroll container, and pagination controls that communicate boundaries. | Mixed | evaluate | Table Component; Page Checklist |
| ANS-DATA-009 | Dense/compact table treatment is reserved for supplementary constrained data, not the default primary list. | Product overlay | overlay | Table Component |
| ANS-DATA-010 | Created/modified information uses one consistent user-and-time presentation across list and detail contexts. | Product overlay | overlay | Table Component; Details |
| ANS-DATA-011 | Details use description-list semantics; identifiers and statuses are styled according to meaning, not simply decorated as labels. | Felt candidate | evaluate | Details Component; Labels |
| ANS-DATA-012 | Structured scripts, JSON, and logs use a reusable code surface with copy, expansion, formatting, and appropriate scrolling. | Product overlay | overlay | Details Component |
| ANS-DATA-013 | A reference to a deleted resource is plain text, not a dead link, and includes an explanatory deleted indicator. | Felt candidate | evaluate | Deleted-Entity Reference Indicator |
| ANS-DATA-014 | Structured-data panels offer only applicable schema, table, and JSON views; hide the view switcher when there is no data. | Mixed | evaluate | Data Panel View Modes |
| ANS-FORM-001 | Choose full-page forms for complex or multi-step work and modals for short, context-preserving edits. | Felt candidate | evaluate | CRUD Patterns |
| ANS-FORM-002 | Full-page forms use one column, a readable maximum width, explicit labels, and product-standard validation. | Mixed | evaluate | Form Component |
| ANS-FORM-003 | Save and Cancel for a full-page form live in a pinned content-panel footer, not the page header, unless a documented surface exception applies. | Felt candidate | evaluate | Sticky Form Footer |
| ANS-FORM-004 | Cancel is visually secondary and returns to the correct origin without pretending to save. | Felt candidate | evaluate | Sticky Form Footer; Wizards |
| ANS-FORM-005 | Complex edits track dirty state, warn before abandoning changes, and expose progress while saving. | Felt candidate | evaluate | Update/Edit; Unsaved Changes |
| ANS-FORM-006 | A multi-step wizard prevents invalid forward navigation, resets dependent selections when upstream choices change, and keeps terminology consistent across action, progress, success, and error text. | Felt candidate | evaluate | Full-Page Wizard |
| ANS-FORM-007 | Inline editing is reserved for small, comprehensible changes; complex changes get a dedicated edit surface. | Felt candidate | evaluate | Update/Edit patterns |
| ANS-FORM-008 | Validation messages remain associated with their controls and are announced accessibly. | Felt candidate | seed | Forms & Error Handling |

### Actions, confirmation, feedback, and status

| Rule ID | Normalized rule | Layer | Priority | Source section |
|---|---|---|---|---|
| ANS-ACT-001 | Confirmation burden is proportional to reversibility, consequence, dependency impact, and scope. | Felt candidate | seed | Confirmation severity model |
| ANS-ACT-002 | A reversible state change uses standard confirmation; a reversible but risky action uses danger treatment without acknowledgement; permanent deletion requires explicit acknowledgement. | Felt candidate | seed | Confirmation severity model |
| ANS-ACT-003 | Permanent deletion names the resource, explains irreversibility, uses danger treatment, and disables confirmation until acknowledgement. | Felt candidate | seed | Delete patterns |
| ANS-ACT-004 | If deletion cascades to other records, enumerate the records or resource types that will also be deleted. | Felt candidate | seed | Cascade Delete |
| ANS-ACT-005 | If deletion leaves dependent resources broken, enumerate the affected resources and explain the consequence. | Felt candidate | seed | Ripple Effect Delete |
| ANS-ACT-006 | When dependency counts cannot load, degrade to a clear generic warning rather than silently omitting risk or blocking the action indefinitely. | Felt candidate | seed | Delete dependency guidance |
| ANS-ACT-007 | Dependency visibility should exist before the destructive moment, such as through a usage view, not only inside the confirmation dialog. | Felt candidate | evaluate | Delete dependency guidance |
| ANS-ACT-008 | One shared confirmation composition owns copy and structure for the same destructive action across list and detail surfaces. | AI-helper workflow | helper | Shared dialog components |
| ANS-ACT-009 | Post-action behavior preserves context when possible, removes or updates stale data, navigates only when necessary, and confirms success. | Felt candidate | seed | Post-delete/disable behavior |
| ANS-ACT-010 | Remove, unassign, cancel, and stop normally use danger confirmation without destructive acknowledgement. | Felt candidate | evaluate | Reversible action confirmation |
| ANS-ACT-011 | Global destructive actions require more confirmation than user- or resource-scoped actions. | Felt candidate | seed | Scoped Destructive Actions |
| ANS-ACT-012 | Disable is not equivalent to delete: disabling may require standard confirmation and dependency explanation; enabling normally takes effect immediately. | Felt candidate | seed | Disable pattern |
| ANS-ACT-013 | Do not over-confirm safe, expected, reversible operations such as duplication or enablement. | Felt candidate | seed | Duplicate; Disable |
| ANS-ACT-014 | A slow one-shot action may fire immediately when confirmation would add no value, but must self-disable, show progress, and provide success/error feedback. | Felt candidate | seed | Cancel run |
| ANS-ACT-015 | Button order and hierarchy are consistent within each context: page header, modal, full-page form, or toolbar. | Felt candidate | evaluate | Button Placement Rules |
| ANS-ACT-016 | A modal that protects a security-critical deadline or one-time secret cannot be dismissed until the user takes an explicit safe action. | Felt candidate | evaluate | Non-Dismissible Modal |
| ANS-ACT-017 | Unsaved-change confirmation appears only when meaningful changes exist and offers a clear stay/leave decision. | Felt candidate | evaluate | Unsaved-Changes Confirmation |
| ANS-ACT-018 | Async/background changes expose progress and final status without requiring a page refresh. | Felt candidate | seed | Feedback & Notifications |
| ANS-ACT-019 | Success feedback is proportional and non-duplicative; a visible state transition can replace a toast when it already communicates success. | Felt candidate | evaluate | Success Feedback; Save Behavior |
| ANS-ACT-020 | Status labels communicate semantic state consistently and do not use color as the only differentiator. | Felt candidate | evaluate | Statuses and Labels |

### Permissions and guarded experiences

| Rule ID | Normalized rule | Layer | Priority | Source section |
|---|---|---|---|---|
| ANS-PERM-001 | Permission handling distinguishes no-read, read-only, and read-write experiences. | Felt candidate | seed | Permission Tiers |
| ANS-PERM-002 | Default to deny while permissions are unresolved so protected content never flashes before access is confirmed. | Felt candidate | seed | Permission Hook; Hide-Until-Confirmed |
| ANS-PERM-003 | Hide navigation and tabs the user cannot read; direct navigation renders an access-denied state rather than protected content. | Felt candidate | seed | Navigation and Tab Gating |
| ANS-PERM-004 | A read-only experience preserves readable content while clearly removing or disabling mutation affordances. | Felt candidate | seed | Permission Tiers; Read-Only Mode |
| ANS-PERM-005 | Disabled protected actions remain focusable when an explanatory tooltip is necessary, and their handlers are removed as defense in depth. | Felt candidate | seed | Action Gating |
| ANS-PERM-006 | Hide an unauthorized empty-state primary action rather than exposing a CTA that only fails later. | Felt candidate | seed | Empty-State Actions |
| ANS-PERM-007 | Permission-aware links are actionable only when the user can complete the destination flow; otherwise provide non-actionable guidance. | Felt candidate | seed | Inline permission branching |
| ANS-PERM-008 | Parent navigation groups disappear when no permitted child remains. | Felt candidate | evaluate | Navigation Gating |
| ANS-PERM-009 | If the active tab becomes unavailable, redirect to the first permitted tab. | Felt candidate | evaluate | Tab Gating |
| ANS-PERM-010 | Mutation routes verify permission with explicit checking, error, denied, and allowed states. | Felt candidate | seed | ProtectedRoute |
| ANS-PERM-011 | Permission explanations state the blocked action, required policy or role, and a realistic way to request access. | Felt candidate | evaluate | Permission Tooltip Format |
| ANS-PERM-012 | Business quotas and limits use the same accessible disabled-with-explanation pattern as permission gating, while keeping the reason distinct. | Felt candidate | evaluate | Action Gating |
| ANS-PERM-013 | Breadcrumb segments are hidden or rendered as text when their parent route is inaccessible. | Felt candidate | seed | Breadcrumbs Must Not Link |
| ANS-PERM-014 | Product permission checks are encapsulated in domain-level hooks so all surfaces apply the same policy. | Product overlay | overlay | Permission Hook Pattern |

### Workflow-builder behavior

| Rule ID | Normalized rule | Layer | Priority | Source section |
|---|---|---|---|---|
| ANS-WF-001 | Keep frequent primary builder actions visible and group secondary views/actions in a structured overflow menu. | Felt candidate | evaluate | Builder Toolbar Hierarchy |
| ANS-WF-002 | Destructive overflow actions appear last and are visually identified as dangerous. | Felt candidate | evaluate | Builder Toolbar Hierarchy |
| ANS-WF-003 | Save, publish, and run are distinct lifecycle actions with distinct status and validation consequences. | Product overlay | overlay | Publish Lifecycle |
| ANS-WF-004 | Save communicates dirty, saving, and last-saved state; avoid redundant success feedback when clearing dirty state already confirms completion. | Felt candidate | evaluate | Save Behavior |
| ANS-WF-005 | Unsaved state is visible outside the canvas, including a browser-title indicator, and clears when state returns to clean. | Felt candidate | evaluate | Save Behavior |
| ANS-WF-006 | Navigable history rows are real links that preserve modified-click and new-tab behavior. | Felt candidate | seed | Run History Panel |
| ANS-WF-007 | Nested controls inside a navigable row remain independently operable without breaking row navigation. | Felt candidate | seed | Run History Panel |
| ANS-WF-008 | Historical versions are read-only, clearly labeled, and mutually exclusive with conflicting side panels. | Product overlay | overlay | Version History |
| ANS-WF-009 | Hide actions that are meaningless in the current onboarding state and reveal them when the prerequisite exists. | Felt candidate | evaluate | Add Step |
| ANS-WF-010 | An immediate action that may be surprising can offer a user-scoped “do not show again” preference without changing the underlying action. | Felt candidate | evaluate | Run Workflow |
| ANS-WF-011 | Canceling an active run is an explicit exception: no confirmation, visible only when cancellable, and protected against duplicate requests. | Product overlay | overlay | Cancel run |
| ANS-WF-012 | Validation errors and warnings have different consequences: errors block publish; warnings remain visible but do not block. | Mixed | seed | Validation Severity |
| ANS-WF-013 | Verification results appear at both aggregate and affected-object levels, and links take users directly to the object needing correction. | Felt candidate | evaluate | Verify Workflow |
| ANS-WF-014 | Publishing always verifies first and explains why publishing is disabled. | Product overlay | overlay | Verify-then-publish |
| ANS-WF-015 | A canvas that cannot function below a supported viewport shows a useful guarded state rather than a broken compressed interface. | Felt candidate | evaluate | Canvas Controls |

### Accessibility, content, styling, and verification

| Rule ID | Normalized rule | Layer | Priority | Source section |
|---|---|---|---|---|
| ANS-AX-001 | Headings are sequential, landmarks identify major regions, and every routed page has one meaningful dynamic browser title. | Felt candidate | seed | Semantic HTML & Page Structure |
| ANS-AX-002 | Every interactive element is keyboard operable, including custom canvas interactions. | Felt candidate | seed | Keyboard Navigation |
| ANS-AX-003 | A tooltip attached to non-interactive content needs a keyboard-focusable host. | Felt candidate | seed | Keyboard Navigation |
| ANS-AX-004 | Preserve a visible focus indicator with sufficient contrast. | Felt candidate | seed | Keyboard Navigation |
| ANS-AX-005 | Route changes move focus to the new main content; dialogs trap focus and return it to their trigger. | Felt candidate | seed | Routing and Modals |
| ANS-AX-006 | Dynamic updates use appropriate live regions, and stateful controls expose current ARIA state. | Felt candidate | seed | Dynamic Content |
| ANS-AX-007 | Every input has an explicit label; errors use `aria-invalid` and are associated with their messages. | Felt candidate | seed | Forms & Error Handling |
| ANS-AX-008 | Meet WCAG contrast requirements and never convey meaning by color alone. | Felt candidate | seed | Color and Contrast |
| ANS-AX-009 | Informative images have concise alternatives; decorative images/icons are hidden from assistive technology. | Felt candidate | seed | Alternative Text |
| ANS-AX-010 | Accessibility validation combines automated checks, manual keyboard operation, and screen-reader testing. | AI-helper workflow | helper | Testing & Validation |
| ANS-CONT-001 | Use sentence case by default, title case only where prescribed, and preserve user-entered casing. | Product overlay | overlay | Content Rules |
| ANS-CONT-002 | Use semantic PatternFly typography components for text rather than raw generic elements used only for styling. | PatternFly reference | reference | No Raw HTML |
| ANS-CONT-003 | Names, statuses, identifiers, and metadata use components according to semantics, not decoration. | Felt candidate | evaluate | Details; Labels |
| ANS-STYLE-001 | Apply styling in this order: PatternFly props/variants, semantic tokens, scoped CSS modules, then dynamic inline style. | AI-helper workflow | helper | Styling Priority |
| ANS-STYLE-002 | Never add global unscoped selectors for elements or PatternFly internals. | Product overlay | overlay | No Global CSS |
| ANS-STYLE-003 | Use semantic tokens instead of hard-coded spacing, color, border, and sizing values. | PatternFly reference | reference | Semantic Tokens |
| ANS-STYLE-004 | A proposed global override must follow the documented PatternFly gap and temporary-exception process. | AI-helper workflow | helper | Global Style Exception |
| ANS-VERIFY-001 | Verify UI in the running application; source inspection and type checking are insufficient. | AI-helper workflow | helper | Chrome DevTools MCP |
| ANS-VERIFY-002 | Inspect DOM structure, computed tokens, layout, console output, network behavior, and accessibility state. | AI-helper workflow | helper | Chrome DevTools MCP |
| ANS-VERIFY-003 | Exercise loading, error, empty, ready, modal, and permission states rather than validating only the happy path. | AI-helper workflow | helper | UI Verification Checklist |
| ANS-VERIFY-004 | Review shared compositions in realistic Storybook stories and in supported themes before sign-off. | AI-helper workflow | helper | Storybook Workflow |

## Hummingbird outline-first rules

| Rule ID | Normalized rule | Layer | Priority | Source section |
|---|---|---|---|---|
| HOF-001 | The component return reads top-to-bottom like the rendered document outline. | AI-helper workflow | helper | Return-as-spec |
| HOF-002 | Use one visible scaffold and one return; compute flags and hydration above it and render structure below it. | AI-helper workflow | helper | One scaffold, one return |
| HOF-003 | Keep structural conditionals visible in the return instead of hiding whole sections in variables or duplicate branches. | AI-helper workflow | helper | One scaffold; Hydration slots |
| HOF-004 | A user-facing section has one concern-aligned file that owns its outline. | Product overlay | overlay | Concern-aligned files |
| HOF-005 | Shell files mount content but do not own section outlines; app chrome, reusable kits, widgets, and page documents live in their designated layers. | Product overlay | overlay | Concern-aligned files |
| HOF-006 | File and export names describe the user-visible concern, not a widget, shell, historical placement, or first consumer. | AI-helper workflow | helper | Concern-aligned files |
| HOF-007 | Section components use established shared context rather than prop-drilling internal data through shells. | Product overlay | overlay | Data access |
| HOF-008 | A tab shell owns one `hb-content` root; section files return only the document outline within it. | Product overlay | overlay | Tab content contract |
| HOF-009 | Scroll/focus landmarks belong to semantic sections in the content file, not the shared shell wrapper. | Felt candidate | evaluate | Tab content contract |
| HOF-010 | Repeated document spacing comes from the shared content-root system; one-off view composition may use visible local layout. | Product overlay | overlay | Tab content contract |
| HOF-011 | Loading, error, empty, and ready branches remain explicit outline conditionals. | Felt candidate | seed | Async outline |
| HOF-012 | Keep stable section identity visible while its async body loads. | Felt candidate | seed | Async outline |
| HOF-013 | Share repeated loading/error chrome as a primitive, but keep domain-specific empty meaning and visible conditionals local. | Mixed | seed | Async outline |
| HOF-014 | Search existing PatternFly, product primitives, sections, shells, and hooks before adding a file or component. | AI-helper workflow | helper | Abstraction threshold |
| HOF-015 | Extend existing capability non-destructively; create a new top-level module only after evidence, dry-run, and review consensus. | AI-helper workflow | helper | Abstraction threshold |
| HOF-016 | Extract an abstraction after at least two structurally equivalent uses and only when no existing primitive can absorb it. | AI-helper workflow | helper | Abstraction threshold |
| HOF-017 | Subtract PatternFly-owned props before defining product-owned data or component APIs. | AI-helper workflow | helper | PF subtract |
| HOF-018 | Public components and page compositions expose and forward root `className` and CSS-variable-safe `style`; named props own real presentation variants. | Product overlay | overlay | Class/style extension |
| HOF-019 | Comments explain rationale, constraints, PatternFly gaps, or planned rehomes—not the obvious next line. | AI-helper workflow | helper | Comments |
| HOF-020 | Refactors follow propose, dry-run, human review, relevance check, reuse search, change, semantic verification, and rendered validation. | AI-helper workflow | helper | Refactor workflow |
| HOF-021 | Validate type checking, targeted tests, and live presentation; do not approve architecture from code shape alone. | AI-helper workflow | helper | Refactor workflow; Review checklist |

## Hummingbird visible-scaffolding rules

| Rule ID | Normalized rule | Layer | Priority | Source section |
|---|---|---|---|---|
| HVS-001 | Begin with a dry-run inventory and relevance ruling before changing architecture. | AI-helper workflow | helper | Process |
| HVS-002 | Define completion at two levels: each safe change is validated, and the wider cleanup is checked for remaining drift and contract breaks. | AI-helper workflow | helper | Definition of done |
| HVS-003 | Use Git-aware moves and removals so architectural history remains reviewable. | AI-helper workflow | helper | Change process |
| HVS-004 | Distinguish app shell, reusable kit, primitive, and page composition; do not move behavior between layers merely to satisfy a folder pattern. | Product overlay | overlay | UI layers |
| HVS-005 | Page documents live with their page entry; ask what the repeated entity is instead of inventing a generic feature layer. | Product overlay | overlay | Page documents |
| HVS-006 | Namespace once-per-app shell, reusable product kit, vendor, and page exports consistently and do not wrap PatternFly simply to rename it. | Product overlay | overlay | Namespace prefixes |
| HVS-007 | Name reusable kit files type-first and scope-to-focus, so sibling relationships remain discoverable. | AI-helper workflow | helper | Kit naming |
| HVS-008 | Merge siblings that differ only superficially; keep separate implementations only when their contracts or behavior genuinely differ. | AI-helper workflow | helper | Kit siblings |
| HVS-009 | Fix a repeated defect at its owning root while preserving behavior that already works. | AI-helper workflow | helper | Root fix |
| HVS-010 | Similar drawers share one open/hydrate contract and shell; content identity and body vary through data or composition, not parallel drawer architectures. | Product overlay | overlay | One drawer |
| HVS-011 | Similar surfaces use one implementation for rendering, landmarks, and navigation behavior to prevent drift. | AI-helper workflow | helper | Alike surfaces |
| HVS-012 | Mount stable scaffolding with the surface; interaction hydrates or activates it rather than injecting an entirely new structure into the DOM. | Felt candidate | evaluate | No transition from non-existence |
| HVS-013 | A table/list view remains visibly a table/list in its page return rather than being hidden behind a one-call-site composition. | AI-helper workflow | helper | Table in a view |
| HVS-014 | Before adding a capability, search the full repository and extend the existing owner when possible. | AI-helper workflow | helper | CHECK FIRST |
| HVS-015 | Do not introduce a wrapper until the existing parent is proven unable to own refs, classes, data attributes, or behavior. | AI-helper workflow | helper | Existing parent |
| HVS-016 | Every public component/config accepts optional `className` and CSS-variable-safe `style`, merges them on the root host, and forwards them through page compositions. | Product overlay | overlay | Class/style extension |
| HVS-017 | Product-owned visual modes use named props on the component that owns the chrome; call sites do not leak known BEM modifier strings. | Product overlay | overlay | Class/style extension |
| HVS-018 | Compare a proposed product type with current PatternFly props and own only the fields left after subtraction. | AI-helper workflow | helper | Subtract PatternFly |
| HVS-019 | Name a type, helper, or composition for the thing it represents, not its first source, layout, or consumer. | AI-helper workflow | helper | Name the thing |
| HVS-020 | A page-local configured composition does not become a reusable kit peer until a second real consumer demonstrates the shared contract. | AI-helper workflow | helper | Name the thing; Kit vs page |
| HVS-021 | Shell vocabulary such as panel, drawer, or tab is reserved for actual shell implementations that pass relevance and rendered-presentation checks. | Product overlay | overlay | Shell vocabulary collisions |
| HVS-022 | Do not create content-router files merely to fill shell header/body slots; they can duplicate document titles and obscure ownership. | Product overlay | overlay | Shell vocabulary collisions |
| HVS-023 | Variables may hydrate visible slots, but must not hide sections, duplicate scaffolds, or replace explicit semantic markup with parser-driven structure. | AI-helper workflow | helper | What may be a variable |
| HVS-024 | Parse external content into data, then render explicit semantic elements; runtime parsers do not own known page structure. | Felt candidate | evaluate | Parser as structure |
| HVS-025 | Share repeated widgets and status chrome, not section outlines or shell slot routers. | AI-helper workflow | helper | Misunderstood DRY |
| HVS-026 | When the document already owns its title, keep shell chrome close-only or untitled rather than displaying the same title twice. | Felt candidate | seed | Forced head and body |
| HVS-027 | One shared content root owns tab/drawer content; prose and preambles stay inside it, not in shell props or sibling wrappers. | Product overlay | overlay | `hb-content` root |
| HVS-028 | Programmatic tab navigation activates the destination before measuring and scrolling to its landmark. | Felt candidate | evaluate | Landmark navigation |
| HVS-029 | Loading, error, empty, and ready remain visible branches under the content root; stable title/preamble stays visible when identity is known. | Felt candidate | seed | Async states |
| HVS-030 | Validate the running interface after architectural changes, including whole-surface effects, heading duplication, focus/ARIA, deep links, and async states. | AI-helper workflow | helper | Enterprise checklist |

## UXD AI Helpers integration and coverage

Reviewed against [`rh-uxd/ai-helpers`](https://github.com/rh-uxd/ai-helpers) at commit [`35c3069`](https://github.com/rh-uxd/ai-helpers/commit/35c3069) on 2026-09-25.

Coverage uses the same model as `instruction-inventory.md`:

- **Direct** — an existing skill substantially implements or validates the rule family.
- **Partial** — a useful generator, workflow, or validator exists, but the exact Felt behavior or product mapping is absent.
- **Gap** — no existing AI Helper meaningfully implements or validates the rule family.

Coverage does not transfer ownership to AI Helpers. FELTRFE-75 remains the source for canonical patterns and applicability, FELTRFE-43 supplies agent guidance, FELTRFE-19 supplies executable validation contracts, and product teams own overlays and explicit exceptions. AI Helpers is the delivery, orchestration, generation, and evaluation layer.

### Relevant existing AI Helper files

| Skill | Current contribution to the layered approach |
|---|---|
| [`pf-component-reuse-check`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-react/skills/pf-component-reuse-check/SKILL.md) | Searches current PatternFly documentation, identifies overlapping custom components, proposes reuse, and builds to verify replacements. |
| [`pf-component-check`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-react/skills/pf-component-check/SKILL.md) | Audits PatternFly nesting, wrapper hierarchies, and structural composition. |
| [`pf-state-audit`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-code-review/skills/pf-state-audit/SKILL.md) | Audits loading, error, empty, and unauthorized states in data-dependent UI. |
| [`pf-table-gen`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-react/skills/pf-table-gen/SKILL.md) | Generates PatternFly tables with sorting, filtering, pagination, expansion, and empty-state composition. |
| [`pf-form-gen`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-react/skills/pf-form-gen/SKILL.md) | Generates accessible PatternFly forms, validation, action groups, and async submission states. |
| [`pf-test-gen`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-react/skills/pf-test-gen/SKILL.md) | Generates tests for conditional states, async behavior, interactions, callbacks, prop forwarding, and accessible APIs. |
| [`pf-a11y-audit`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-a11y/skills/pf-a11y-audit/SKILL.md) | Performs static WCAG, semantic markup, accessible-name, and ARIA review. |
| [`pf-a11y-test-gen`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-a11y/skills/pf-a11y-test-gen/SKILL.md) | Generates persistent axe, keyboard, ARIA, and focus-management tests. |
| [`pf-a11y-keyboard`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-a11y/skills/pf-a11y-keyboard/SKILL.md) | Tests keyboard navigation and focus behavior in a running interface. |
| [`pf-catalog-interaction-patterns`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-design-guide/skills/pf-catalog-interaction-patterns/SKILL.md) | Finds PatternFly components by click, hover, keyboard, and drag interaction behavior. |
| [`pf-screenshot-mapping`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-design-guide/skills/pf-screenshot-mapping/SKILL.md) | Maps a screen to PatternFly structure and identifies component, composition, and documentation gaps. |
| [`pf-css-token-check`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-design-audit/skills/pf-css-token-check/SKILL.md) | Detects hard-coded styling values and recommends semantic PatternFly tokens. |
| [`pf-content-review`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-workshop/skills/pf-content-review/SKILL.md) | Reviews copy against PatternFly and Red Hat voice-and-tone guidance. |
| [`pf-adversarial-review`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-code-review/skills/pf-adversarial-review/SKILL.md) | Probes missing states, boundary conditions, unsafe prop combinations, and defensive behavior. |
| [`pf-review`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/patternfly/pf-code-review/skills/pf-review/SKILL.md) | Orchestrates PatternFly compliance checks and deduplicates findings into a prioritized report. |
| [`uxd-design-handoff`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/uxd-design/skills/uxd-design-handoff/SKILL.md) | Produces component maps, state matrices, interaction specifications, accessibility notes, and testable acceptance criteria. |
| [`uxd-prototype-create`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/uxd-prototype/skills/uxd-prototype-create/SKILL.md) | Plans and builds prototypes with journeys and alternate loading, empty, error, and edge-case scenarios. |
| [`uxd-prototype-evaluate`](https://github.com/rh-uxd/ai-helpers/blob/main/plugins/uxd-prototype/skills/uxd-prototype-evaluate/SKILL.md) | Evaluates a rendered prototype, supports product overlays, exercises journeys, and produces screenshot-backed evidence. |

### Ansible/Syntara rule crosswalk

| Catalog rules | Coverage | Existing AI Helper support | Remaining Felt or product work |
|---|---|---|---|
| `ANS-DS-001`, `ANS-DS-008` | Partial | `pf-component-reuse-check`, `pf-component-check`, `pf-screenshot-mapping`, and PatternFly MCP retrieval use current PF information. | Establish one Felt retrieval contract so all skills obtain applicable canonical patterns as well as PF APIs. |
| `ANS-DS-002`–`004`, `ANS-DS-007` | Direct | `pf-component-reuse-check` supplies search-before-create; `pf-screenshot-mapping` identifies structural gaps; `pf-review` supports verification. | Add UX escalation, temporary-override metadata, upstream issue linkage, and resolution-state handling. |
| `ANS-DS-005`–`006` | Partial | Reuse and structural checks favor existing components and compositions. | Felt defines portable composition intent; Syntara supplies the `Syn*` mapping through a product overlay. |
| `ANS-NAV-001`–`002` | Partial | `pf-catalog-interaction-patterns` and `pf-a11y-keyboard` cover interaction selection and live keyboard behavior. | Encode exact flyout timing, closing, hover, and product navigation behavior in the overlay. |
| `ANS-NAV-003`–`010` | Partial | `pf-component-check`, `pf-screenshot-mapping`, `pf-state-audit`, and accessibility skills cover structure, shell persistence, states, headings, tabs, and navigation semantics. | Add canonical page-archetype, title-ownership, accessible-route, and tab-availability rules; map them to `Syn*`. |
| `ANS-DATA-001`–`003` | Partial | `pf-table-gen`, `pf-state-audit`, and `pf-test-gen` cover tables, filters, states, async behavior, and tests. | Define refetch behavior, content preservation, state announcements, and product list-panel mapping. |
| `ANS-DATA-004`–`007` | Direct | `pf-state-audit`, `uxd-design-handoff`, and `pf-test-gen` cover loading, error, empty, unauthorized, recovery, and conditional rendering. | Expand from the current four-state model to Felt applicability variants such as filtered-empty, first-use, configuration-required, and not-found. |
| `ANS-DATA-008`–`010` | Direct | `pf-table-gen`, `pf-component-check`, and `pf-test-gen` generate and validate semantic table composition, pagination, variants, and behavior. | Product overlay supplies compact-table policy and timestamp/user presentation. |
| `ANS-DATA-011`–`014` | Partial | Structural, accessibility, interaction, and test skills cover semantics and rendering. | Add semantic metadata-vs-status guidance, deleted-reference behavior, code-surface mapping, and structured-data view applicability. |
| `ANS-FORM-001`–`004` | Partial | `pf-form-gen`, `pf-component-check`, and `uxd-design-handoff` support form structure, action groups, and handoff criteria. | Define cross-product placement criteria and overlay mappings for sticky panel footers and documented exceptions. |
| `ANS-FORM-005`–`008` | Direct | `pf-form-gen`, `pf-test-gen`, `pf-a11y-audit`, and `pf-a11y-test-gen` cover validation, async submission, labels, error association, and tests. | Add abandonment/dirty-state and dependent-step semantics where they are not product-specific. |
| `ANS-ACT-001`–`008` | Partial | UX heuristic evaluation, `uxd-design-handoff`, and general test/a11y skills can detect missing confirmation and produce acceptance criteria. | Create the Felt destructive-action record and validators for reversibility, acknowledgement, cascade, ripple effects, dependencies, and shared composition. |
| `ANS-ACT-009`–`020` | Partial | `uxd-prototype-create`, `uxd-prototype-evaluate`, `pf-test-gen`, and `pf-adversarial-review` can model and verify outcomes, progress, disabled states, and feedback. | Encode confirmation tiers, scope escalation, over-confirmation prohibitions, non-dismissible exceptions, and proportional feedback as Felt rules. |
| `ANS-PERM-001`–`014` | Partial | `pf-state-audit` recognizes unauthorized states; accessibility and test skills validate disabled controls, names, focus, and conditional output. | Add a permission-aware validator for hide-until-confirmed, route/tab/breadcrumb gating, handler removal, accessible explanations, and product permission-hook mappings. |
| `ANS-WF-001`–`005` | Partial | `uxd-design-handoff`, `uxd-prototype-create`, and `uxd-prototype-evaluate` can specify and inspect hierarchy, status, lifecycle, and feedback. | Syntara owns the workflow lifecycle; Felt may retain dirty-state and nonredundant-feedback behavior. |
| `ANS-WF-006`–`007` | Partial | `pf-a11y-audit`, `pf-a11y-keyboard`, `pf-a11y-test-gen`, and interaction lookup cover link and nested-control semantics generally. | Add browser tests for real anchors, modified/middle click, overlays, and independent nested targets. |
| `ANS-WF-008`–`011` | Gap | Prototype skills can exercise these journeys but do not define the product behavior. | Keep version history, onboarding, run preference, and cancel-run exception in the Syntara overlay; expose only any approved general pattern. |
| `ANS-WF-012`–`014` | Partial | Form, state, test, adversarial-review, and prototype-evaluation skills can represent severities and verify blocked/enabled outcomes. | Add stable Felt validation-severity rule IDs, publish applicability, remediation links, and diagnostic output. |
| `ANS-WF-015` | Partial | `uxd-prototype-evaluate` can test supported viewport scenarios in a running prototype. | Product overlay defines the threshold; Felt defines the usable guarded-state expectation. |
| `ANS-AX-001`–`009` | Direct | `pf-a11y-audit`, `pf-a11y-test-gen`, and `pf-a11y-keyboard` cover structure, headings, names, keyboard use, focus, ARIA, labeling, contrast-related checks, and alternatives. | Connect findings to Felt rule IDs and preserve product-specific focus utilities in the overlay. |
| `ANS-AX-010` | Direct | The three accessibility skills explicitly combine static audit, persistent tests, and live keyboard evaluation. | Add screen-reader evidence expectations and evaluation fixtures where automation is insufficient. |
| `ANS-CONT-001`–`003` | Partial | `pf-content-review`, accessibility review, and component mapping cover voice/tone and semantic component use. | Product overlay owns terminology/casing exceptions; Felt may define semantic status-vs-metadata guidance. |
| `ANS-STYLE-001`–`004` | Direct | `pf-css-token-check`, `pf-component-reuse-check`, and `pf-review` detect hard-coded values, favor PF APIs, and audit compliance. | Product overlay owns approved exception tracking; PatternFly MCP remains the live API/token source. |
| `ANS-VERIFY-001`–`004` | Direct | `pf-review`, `pf-a11y-keyboard`, `uxd-prototype-evaluate`, and generated tests supply code, browser, interaction, and evidence checks. | Standardize minimum Felt evidence and diagnostics for required state coverage and semantic rules. |

### Hummingbird outline-first rule crosswalk

| Catalog rules | Coverage | Existing AI Helper support | Remaining Felt or product work |
|---|---|---|---|
| `HOF-001`–`003` | Gap | Existing skills can test output but do not enforce return-as-spec, one scaffold, or visible structural conditionals. | Add an outline-first authoring helper or static analysis rule; keep framework-specific exceptions explicit. |
| `HOF-004`–`010` | Gap | `pf-component-check` covers PatternFly component structure, not Hummingbird file ownership, shell boundaries, context usage, or `hb-content`. | Hummingbird supplies these mappings as a product architecture overlay. |
| `HOF-011`–`013` | Direct | `pf-state-audit`, `uxd-design-handoff`, `pf-test-gen`, and prototype skills cover explicit async states and state evidence. | Add stable identity, shared-chrome/domain-empty distinctions, and Felt state IDs. |
| `HOF-014`–`017` | Direct | `pf-component-reuse-check` implements search-before-create and PF schema comparison. | Extend its search order to product primitives/sections and formalize the abstraction threshold and PF-prop subtraction result. |
| `HOF-018` | Partial | `pf-test-gen` tests `className` merging and spread-prop forwarding for component libraries. | Add CSS-variable-safe `style` forwarding and Hummingbird public-composition applicability in the product overlay. |
| `HOF-019` | Gap | No current skill reviews comments specifically for rationale, constraints, or planned rehomes. | Add focused engineering-review guidance if UXD wants this convention across products. |
| `HOF-020`–`021` | Direct | `pf-review`, `pf-test-gen`, `pf-a11y-keyboard`, and `uxd-prototype-evaluate` support staged verification and rendered evidence. | Add the Hummingbird relevance/dry-run sequence as an optional product workflow overlay. |

### Hummingbird visible-scaffolding rule crosswalk

| Catalog rules | Coverage | Existing AI Helper support | Remaining Felt or product work |
|---|---|---|---|
| `HVS-001`–`011` | Partial | Reuse, structure, review, and rendered-evaluation skills support inventory, root fixes, deduplication, and verification in general. | Hummingbird must supply its file layers, naming, namespace, drawer, relevance, and Git-move conventions. |
| `HVS-012` | Partial | Prototype and accessibility skills can inspect mounted structure, transitions, and focus behavior. | Define when stable scaffolding is a cross-product behavior versus a product architecture rule. |
| `HVS-013` | Gap | No current AI Helper enforces visible table/list scaffolding or rejects one-call-site ghost compositions. | Add to an outline-first/visible-scaffolding workflow helper if adopted across teams. |
| `HVS-014`–`015` | Direct | `pf-component-reuse-check` searches before creation and challenges unnecessary custom components; structural review helps identify excess wrappers. | Extend it to prove whether an existing product parent can absorb refs, data attributes, and behavior. |
| `HVS-016`–`017` | Partial | `pf-test-gen` tests `className` and root prop forwarding; structural review can inspect ownership. | Add `style` forwarding, named-variant ownership, and BEM-leak checks through the Hummingbird overlay or a general component-API rule. |
| `HVS-018` | Direct | `pf-component-reuse-check` consults current PF documentation and compares intended roles/APIs. | Emit a structured PF-owned/product-owned field comparison and stable diagnostic. |
| `HVS-019`–`020` | Gap | No current skill evaluates first-consumer coupling or the second-consumer threshold for names and compositions. | Add general engineering naming/abstraction guidance or retain it in the Hummingbird overlay. |
| `HVS-021`–`022` | Gap | Generic structural and accessibility audits may reveal symptoms but do not understand Hummingbird shell vocabulary or slot routers. | Hummingbird overlay defines shell vocabulary, relevance, and prohibited router patterns. |
| `HVS-023`–`025` | Gap | Current helpers do not distinguish hydration variables from hidden page structure or parser-owned structure. | Add outline-first static/evaluation checks if this becomes a reusable UXD engineering convention. |
| `HVS-026` | Partial | Accessibility skills validate headings and accessible names. | Add composed-surface title ownership and rendered duplicate-title detection as a Felt rule. |
| `HVS-027`–`029` | Partial | State, accessibility, test, and prototype skills validate roots, landmarks, state branches, and live behavior generally. | Hummingbird maps `hb-content` and scrolling; Felt defines stable identity, landmark sequencing, and async-state intent. |
| `HVS-030` | Direct | `pf-review`, accessibility skills, tests, and `uxd-prototype-evaluate` collectively support whole-surface rendered validation. | Standardize the required evidence package and attach Felt diagnostic IDs. |

### Integration implications

The existing skills already provide most of the mechanics needed to deliver the layered system. The main gaps are not additional broad mega-skills; they are shared design-intelligence inputs and a few focused validators:

1. **Felt retrieval adapter** — lets AI Helpers retrieve applicable FELTRFE-75 records, FELTRFE-43 guidance, rule IDs, and product-overlay mappings.
2. **Destructive-action validator** — covers `ANS-ACT-*` confirmation tiers, dependencies, reversibility, scope, and exceptions.
3. **Permission-aware validator** — covers `ANS-PERM-*`, especially hide-until-confirmed and inaccessible navigation.
4. **Interaction-semantics validator** — covers real-link rows, modified clicks, nested controls, landmark sequencing, and title ownership.
5. **Outline/scaffolding helper** — optional engineering workflow for `HOF-001`–`010` and `HVS-013`, `HVS-023`–`025`; initially delivered as a Hummingbird overlay until another product validates it.
6. **Structured diagnostics** — existing audits should return FELTRFE-19 rule IDs, severity, evidence, and remediation rather than isolated prose findings.

## Consolidated findings

The review yields **161 normalized, source-traceable rules**:

- 110 from the current Ansible/Syntara skill.
- 21 from Hummingbird `outline-first-ui`.
- 30 from Hummingbird `visible-scaffolding`.

Cross-source duplicates and near-duplicates remain in the source-specific tables so provenance is not lost. The pattern and workflow families below group those overlaps into proposed shared concepts without prematurely declaring them identical.

### Recommended first canonical pattern families

| Pattern family | Representative rules |
|---|---|
| Asynchronous content and stable identity | `ANS-DATA-002`–`006`, `HOF-011`–`013`, `HVS-029` |
| Destructive and consequential actions | `ANS-ACT-001`–`019` |
| Permission-aware content and navigation | `ANS-PERM-001`–`014` |
| Navigable rows and nested controls | `ANS-WF-006`–`007` |
| Composed-surface title ownership | `ANS-AX-001`, `HVS-026`–`027` |
| Form action placement and abandonment | `ANS-FORM-003`–`006`, `ANS-ACT-017` |
| Validation severity and remediation | `ANS-WF-012`–`014` |
| Post-action feedback | `ANS-ACT-009`, `018`–`019` |

### Recommended AI-helper workflow families

| Workflow family | Representative rules |
|---|---|
| Retrieve before creating | `ANS-DS-002`–`004`, `HOF-014`–`017`, `HVS-014`–`020` |
| Outline-first implementation | `HOF-001`–`003`, `HVS-013`, `HVS-023`–`025` |
| Architectural relevance and ownership | `HOF-004`–`010`, `HVS-001`–`011`, `HVS-021`–`022` |
| Render and validate | `ANS-VERIFY-001`–`004`, `HOF-020`–`021`, `HVS-030` |
| Accessibility validation | `ANS-AX-010` plus the `ANS-AX-*` behavioral requirements |

## Proposed next refinement

For each `seed` and `evaluate` Felt candidate:

1. Compare the rule across at least two product teams.
2. Decide whether it is a requirement, recommendation, product example, or exception.
3. Assign a stable Felt pattern and semantic rule ID.
4. Define applicability inputs and false-positive boundaries.
5. Link the product implementation mapping rather than embedding wrapper names centrally.
6. Add positive, negative, and exception fixtures for agent and validator evaluations.
