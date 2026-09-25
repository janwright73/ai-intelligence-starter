# Rule disposition record

This file records the proposed disposition of every normalized rule in `comprehensive-rule-catalog.md`. It is a governance artifact: the catalog preserves evidence, while this record decides which layer should own the rule. All decisions remain `proposed` until reviewed by Felt and the contributing product teams.

## Dispositions

| Disposition | Meaning |
|---|---|
| `canonical-seed` | Include in the initial FELTRFE-75 pattern catalog. |
| `candidate-review` | Compare across products before promotion to Felt. |
| `ai-helper-workflow` | Deliver as an agent planning, retrieval, implementation, or verification workflow. |
| `patternfly-reference` | Retrieve current PatternFly API or design guidance; do not duplicate it in Felt. |
| `product-overlay` | Keep the rule and implementation mapping under product ownership. |
| `split-canonical-overlay` | Felt owns portable intent; the product owns its mapping or exception. |
| `split-review` | A mixed rule needs review before separating portable intent from implementation. |

## Complete rule map

| Rule ID | Normalized rule | Proposed disposition | Target owner/artifact | Decision status |
|---|---|---|---|---|
| `ANS-DS-001` | Use PatternFly as the default component, pattern, accessibility, layout, and theming foundation. | `patternfly-reference` | PatternFly MCP and current documentation | proposed |
| `ANS-DS-002` | Before creating custom UI, search current PatternFly components, variants, tokens, and examples. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `ANS-DS-003` | A suspected PatternFly gap must be reviewed with UX before a custom solution is accepted. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `ANS-DS-004` | Confirmed gaps should be raised upstream; temporary overrides need provenance, ownership, an issue, and a removal path. | `split-review` | Felt and product co-review | proposed |
| `ANS-DS-005` | Prefer standardized compositions over feature-specific combinations of atomic components. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-DS-006` | Use established `Syn*` wrappers instead of reconstructing the same composition from raw PatternFly components. | `product-overlay` | Syntara overlay | proposed |
| `ANS-DS-007` | Do not introduce a custom one-off when an existing PatternFly or product primitive can be extended. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `ANS-DS-008` | Use current library documentation before writing React, Zod, Zustand, or other library-dependent code. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `ANS-NAV-001` | Navigation items with children expose a flyout; items without children navigate directly and show a label tooltip. | `product-overlay` | Syntara overlay | proposed |
| `ANS-NAV-002` | Selecting a flyout child closes the flyout immediately; pointer movement between trigger and flyout must not cause flicker. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-NAV-003` | Every page uses one consistent hierarchy: app shell, navigation, page wrapper, page header, content panel, main content, and contextual footer. | `split-review` | Felt and product co-review | proposed |
| `ANS-NAV-004` | Preserve the page shell and page identity when showing loading, error, or empty content. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-NAV-005` | Choose a canonical page archetype—list, detail, form, error-in-panel, or stacked panels—before composing the page. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-NAV-006` | Use a shared full-height content stack so nested scroll regions resolve height correctly. | `product-overlay` | Syntara overlay | proposed |
| `ANS-NAV-007` | Stack sibling panels through the product stack primitive; clip or scroll inside panels, not on an ancestor that would cut off elevation. | `product-overlay` | Syntara overlay | proposed |
| `ANS-NAV-008` | Page headers contain the page title and primary actions; the title matches the navigation label and uses one semantic page title. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-NAV-009` | Breadcrumbs represent actual accessible navigation and must not point to routes the user cannot open. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-NAV-010` | Tabs represent peer views; use stable URLs and validate the active tab against the set currently available to the user. | `split-review` | Felt and product co-review | proposed |
| `ANS-DATA-001` | A list surface uses one shared composition for query state, toolbar, table, empty states, and pagination. | `split-review` | Felt and product co-review | proposed |
| `ANS-DATA-002` | Disable list filters and controls during refetch while preserving existing content and announcing the update to assistive technology. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-DATA-003` | Show filters when data exists or filters are active; hide them only for a truly empty first-use state. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-DATA-004` | Distinguish first-use empty, filtered-empty, service error, invalid identifier, not found, access denied, configuration-required, and success states. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-DATA-005` | A filtered-empty state offers a clear-filters recovery action; a service error offers retry; an invalid or missing resource offers navigation back. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-DATA-006` | Avoid duplicate primary CTAs: when the empty state owns the create/configure action, hide the equivalent page-header action. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-DATA-007` | Empty-state size, heading level, status, and icon semantics follow the containing surface rather than being selected ad hoc. | `patternfly-reference` | PatternFly MCP and current documentation | proposed |
| `ANS-DATA-008` | Tables use semantic column headers, a standardized scroll container, and pagination controls that communicate boundaries. | `split-review` | Felt and product co-review | proposed |
| `ANS-DATA-009` | Dense/compact table treatment is reserved for supplementary constrained data, not the default primary list. | `product-overlay` | Syntara overlay | proposed |
| `ANS-DATA-010` | Created/modified information uses one consistent user-and-time presentation across list and detail contexts. | `product-overlay` | Syntara overlay | proposed |
| `ANS-DATA-011` | Details use description-list semantics; identifiers and statuses are styled according to meaning, not simply decorated as labels. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-DATA-012` | Structured scripts, JSON, and logs use a reusable code surface with copy, expansion, formatting, and appropriate scrolling. | `product-overlay` | Syntara overlay | proposed |
| `ANS-DATA-013` | A reference to a deleted resource is plain text, not a dead link, and includes an explanatory deleted indicator. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-DATA-014` | Structured-data panels offer only applicable schema, table, and JSON views; hide the view switcher when there is no data. | `split-review` | Felt and product co-review | proposed |
| `ANS-FORM-001` | Choose full-page forms for complex or multi-step work and modals for short, context-preserving edits. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-FORM-002` | Full-page forms use one column, a readable maximum width, explicit labels, and product-standard validation. | `split-review` | Felt and product co-review | proposed |
| `ANS-FORM-003` | Save and Cancel for a full-page form live in a pinned content-panel footer, not the page header, unless a documented surface exception applies. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-FORM-004` | Cancel is visually secondary and returns to the correct origin without pretending to save. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-FORM-005` | Complex edits track dirty state, warn before abandoning changes, and expose progress while saving. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-FORM-006` | A multi-step wizard prevents invalid forward navigation, resets dependent selections when upstream choices change, and keeps terminology consistent across action, progress, success, and error text. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-FORM-007` | Inline editing is reserved for small, comprehensible changes; complex changes get a dedicated edit surface. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-FORM-008` | Validation messages remain associated with their controls and are announced accessibly. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-001` | Confirmation burden is proportional to reversibility, consequence, dependency impact, and scope. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-002` | A reversible state change uses standard confirmation; a reversible but risky action uses danger treatment without acknowledgement; permanent deletion requires explicit acknowledgement. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-003` | Permanent deletion names the resource, explains irreversibility, uses danger treatment, and disables confirmation until acknowledgement. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-004` | If deletion cascades to other records, enumerate the records or resource types that will also be deleted. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-005` | If deletion leaves dependent resources broken, enumerate the affected resources and explain the consequence. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-006` | When dependency counts cannot load, degrade to a clear generic warning rather than silently omitting risk or blocking the action indefinitely. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-007` | Dependency visibility should exist before the destructive moment, such as through a usage view, not only inside the confirmation dialog. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-ACT-008` | One shared confirmation composition owns copy and structure for the same destructive action across list and detail surfaces. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `ANS-ACT-009` | Post-action behavior preserves context when possible, removes or updates stale data, navigates only when necessary, and confirms success. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-010` | Remove, unassign, cancel, and stop normally use danger confirmation without destructive acknowledgement. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-ACT-011` | Global destructive actions require more confirmation than user- or resource-scoped actions. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-012` | Disable is not equivalent to delete: disabling may require standard confirmation and dependency explanation; enabling normally takes effect immediately. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-013` | Do not over-confirm safe, expected, reversible operations such as duplication or enablement. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-014` | A slow one-shot action may fire immediately when confirmation would add no value, but must self-disable, show progress, and provide success/error feedback. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-015` | Button order and hierarchy are consistent within each context: page header, modal, full-page form, or toolbar. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-ACT-016` | A modal that protects a security-critical deadline or one-time secret cannot be dismissed until the user takes an explicit safe action. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-ACT-017` | Unsaved-change confirmation appears only when meaningful changes exist and offers a clear stay/leave decision. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-ACT-018` | Async/background changes expose progress and final status without requiring a page refresh. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-ACT-019` | Success feedback is proportional and non-duplicative; a visible state transition can replace a toast when it already communicates success. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-ACT-020` | Status labels communicate semantic state consistently and do not use color as the only differentiator. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-PERM-001` | Permission handling distinguishes no-read, read-only, and read-write experiences. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-PERM-002` | Default to deny while permissions are unresolved so protected content never flashes before access is confirmed. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-PERM-003` | Hide navigation and tabs the user cannot read; direct navigation renders an access-denied state rather than protected content. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-PERM-004` | A read-only experience preserves readable content while clearly removing or disabling mutation affordances. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-PERM-005` | Disabled protected actions remain focusable when an explanatory tooltip is necessary, and their handlers are removed as defense in depth. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-PERM-006` | Hide an unauthorized empty-state primary action rather than exposing a CTA that only fails later. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-PERM-007` | Permission-aware links are actionable only when the user can complete the destination flow; otherwise provide non-actionable guidance. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-PERM-008` | Parent navigation groups disappear when no permitted child remains. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-PERM-009` | If the active tab becomes unavailable, redirect to the first permitted tab. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-PERM-010` | Mutation routes verify permission with explicit checking, error, denied, and allowed states. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-PERM-011` | Permission explanations state the blocked action, required policy or role, and a realistic way to request access. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-PERM-012` | Business quotas and limits use the same accessible disabled-with-explanation pattern as permission gating, while keeping the reason distinct. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-PERM-013` | Breadcrumb segments are hidden or rendered as text when their parent route is inaccessible. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-PERM-014` | Product permission checks are encapsulated in domain-level hooks so all surfaces apply the same policy. | `product-overlay` | Syntara overlay | proposed |
| `ANS-WF-001` | Keep frequent primary builder actions visible and group secondary views/actions in a structured overflow menu. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-WF-002` | Destructive overflow actions appear last and are visually identified as dangerous. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-WF-003` | Save, publish, and run are distinct lifecycle actions with distinct status and validation consequences. | `product-overlay` | Syntara overlay | proposed |
| `ANS-WF-004` | Save communicates dirty, saving, and last-saved state; avoid redundant success feedback when clearing dirty state already confirms completion. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-WF-005` | Unsaved state is visible outside the canvas, including a browser-title indicator, and clears when state returns to clean. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-WF-006` | Navigable history rows are real links that preserve modified-click and new-tab behavior. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-WF-007` | Nested controls inside a navigable row remain independently operable without breaking row navigation. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-WF-008` | Historical versions are read-only, clearly labeled, and mutually exclusive with conflicting side panels. | `product-overlay` | Syntara overlay | proposed |
| `ANS-WF-009` | Hide actions that are meaningless in the current onboarding state and reveal them when the prerequisite exists. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-WF-010` | An immediate action that may be surprising can offer a user-scoped “do not show again” preference without changing the underlying action. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-WF-011` | Canceling an active run is an explicit exception: no confirmation, visible only when cancellable, and protected against duplicate requests. | `product-overlay` | Syntara overlay | proposed |
| `ANS-WF-012` | Validation errors and warnings have different consequences: errors block publish; warnings remain visible but do not block. | `split-canonical-overlay` | Felt canonical record plus product overlay | proposed |
| `ANS-WF-013` | Verification results appear at both aggregate and affected-object levels, and links take users directly to the object needing correction. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-WF-014` | Publishing always verifies first and explains why publishing is disabled. | `product-overlay` | Syntara overlay | proposed |
| `ANS-WF-015` | A canvas that cannot function below a supported viewport shows a useful guarded state rather than a broken compressed interface. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-AX-001` | Headings are sequential, landmarks identify major regions, and every routed page has one meaningful dynamic browser title. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-AX-002` | Every interactive element is keyboard operable, including custom canvas interactions. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-AX-003` | A tooltip attached to non-interactive content needs a keyboard-focusable host. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-AX-004` | Preserve a visible focus indicator with sufficient contrast. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-AX-005` | Route changes move focus to the new main content; dialogs trap focus and return it to their trigger. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-AX-006` | Dynamic updates use appropriate live regions, and stateful controls expose current ARIA state. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-AX-007` | Every input has an explicit label; errors use `aria-invalid` and are associated with their messages. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-AX-008` | Meet WCAG contrast requirements and never convey meaning by color alone. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-AX-009` | Informative images have concise alternatives; decorative images/icons are hidden from assistive technology. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `ANS-AX-010` | Accessibility validation combines automated checks, manual keyboard operation, and screen-reader testing. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `ANS-CONT-001` | Use sentence case by default, title case only where prescribed, and preserve user-entered casing. | `product-overlay` | Syntara overlay | proposed |
| `ANS-CONT-002` | Use semantic PatternFly typography components for text rather than raw generic elements used only for styling. | `patternfly-reference` | PatternFly MCP and current documentation | proposed |
| `ANS-CONT-003` | Names, statuses, identifiers, and metadata use components according to semantics, not decoration. | `candidate-review` | Felt cross-product review queue | proposed |
| `ANS-STYLE-001` | Apply styling in this order: PatternFly props/variants, semantic tokens, scoped CSS modules, then dynamic inline style. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `ANS-STYLE-002` | Never add global unscoped selectors for elements or PatternFly internals. | `product-overlay` | Syntara overlay | proposed |
| `ANS-STYLE-003` | Use semantic tokens instead of hard-coded spacing, color, border, and sizing values. | `patternfly-reference` | PatternFly MCP and current documentation | proposed |
| `ANS-STYLE-004` | A proposed global override must follow the documented PatternFly gap and temporary-exception process. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `ANS-VERIFY-001` | Verify UI in the running application; source inspection and type checking are insufficient. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `ANS-VERIFY-002` | Inspect DOM structure, computed tokens, layout, console output, network behavior, and accessibility state. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `ANS-VERIFY-003` | Exercise loading, error, empty, ready, modal, and permission states rather than validating only the happy path. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `ANS-VERIFY-004` | Review shared compositions in realistic Storybook stories and in supported themes before sign-off. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HOF-001` | The component return reads top-to-bottom like the rendered document outline. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HOF-002` | Use one visible scaffold and one return; compute flags and hydration above it and render structure below it. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HOF-003` | Keep structural conditionals visible in the return instead of hiding whole sections in variables or duplicate branches. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HOF-004` | A user-facing section has one concern-aligned file that owns its outline. | `product-overlay` | Hummingbird overlay | proposed |
| `HOF-005` | Shell files mount content but do not own section outlines; app chrome, reusable kits, widgets, and page documents live in their designated layers. | `product-overlay` | Hummingbird overlay | proposed |
| `HOF-006` | File and export names describe the user-visible concern, not a widget, shell, historical placement, or first consumer. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HOF-007` | Section components use established shared context rather than prop-drilling internal data through shells. | `product-overlay` | Hummingbird overlay | proposed |
| `HOF-008` | A tab shell owns one `hb-content` root; section files return only the document outline within it. | `product-overlay` | Hummingbird overlay | proposed |
| `HOF-009` | Scroll/focus landmarks belong to semantic sections in the content file, not the shared shell wrapper. | `candidate-review` | Felt cross-product review queue | proposed |
| `HOF-010` | Repeated document spacing comes from the shared content-root system; one-off view composition may use visible local layout. | `product-overlay` | Hummingbird overlay | proposed |
| `HOF-011` | Loading, error, empty, and ready branches remain explicit outline conditionals. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `HOF-012` | Keep stable section identity visible while its async body loads. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `HOF-013` | Share repeated loading/error chrome as a primitive, but keep domain-specific empty meaning and visible conditionals local. | `split-canonical-overlay` | Felt canonical record plus product overlay | proposed |
| `HOF-014` | Search existing PatternFly, product primitives, sections, shells, and hooks before adding a file or component. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HOF-015` | Extend existing capability non-destructively; create a new top-level module only after evidence, dry-run, and review consensus. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HOF-016` | Extract an abstraction after at least two structurally equivalent uses and only when no existing primitive can absorb it. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HOF-017` | Subtract PatternFly-owned props before defining product-owned data or component APIs. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HOF-018` | Public components and page compositions expose and forward root `className` and CSS-variable-safe `style`; named props own real presentation variants. | `product-overlay` | Hummingbird overlay | proposed |
| `HOF-019` | Comments explain rationale, constraints, PatternFly gaps, or planned rehomes—not the obvious next line. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HOF-020` | Refactors follow propose, dry-run, human review, relevance check, reuse search, change, semantic verification, and rendered validation. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HOF-021` | Validate type checking, targeted tests, and live presentation; do not approve architecture from code shape alone. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-001` | Begin with a dry-run inventory and relevance ruling before changing architecture. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-002` | Define completion at two levels: each safe change is validated, and the wider cleanup is checked for remaining drift and contract breaks. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-003` | Use Git-aware moves and removals so architectural history remains reviewable. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-004` | Distinguish app shell, reusable kit, primitive, and page composition; do not move behavior between layers merely to satisfy a folder pattern. | `product-overlay` | Hummingbird overlay | proposed |
| `HVS-005` | Page documents live with their page entry; ask what the repeated entity is instead of inventing a generic feature layer. | `product-overlay` | Hummingbird overlay | proposed |
| `HVS-006` | Namespace once-per-app shell, reusable product kit, vendor, and page exports consistently and do not wrap PatternFly simply to rename it. | `product-overlay` | Hummingbird overlay | proposed |
| `HVS-007` | Name reusable kit files type-first and scope-to-focus, so sibling relationships remain discoverable. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-008` | Merge siblings that differ only superficially; keep separate implementations only when their contracts or behavior genuinely differ. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-009` | Fix a repeated defect at its owning root while preserving behavior that already works. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-010` | Similar drawers share one open/hydrate contract and shell; content identity and body vary through data or composition, not parallel drawer architectures. | `product-overlay` | Hummingbird overlay | proposed |
| `HVS-011` | Similar surfaces use one implementation for rendering, landmarks, and navigation behavior to prevent drift. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-012` | Mount stable scaffolding with the surface; interaction hydrates or activates it rather than injecting an entirely new structure into the DOM. | `candidate-review` | Felt cross-product review queue | proposed |
| `HVS-013` | A table/list view remains visibly a table/list in its page return rather than being hidden behind a one-call-site composition. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-014` | Before adding a capability, search the full repository and extend the existing owner when possible. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-015` | Do not introduce a wrapper until the existing parent is proven unable to own refs, classes, data attributes, or behavior. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-016` | Every public component/config accepts optional `className` and CSS-variable-safe `style`, merges them on the root host, and forwards them through page compositions. | `product-overlay` | Hummingbird overlay | proposed |
| `HVS-017` | Product-owned visual modes use named props on the component that owns the chrome; call sites do not leak known BEM modifier strings. | `product-overlay` | Hummingbird overlay | proposed |
| `HVS-018` | Compare a proposed product type with current PatternFly props and own only the fields left after subtraction. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-019` | Name a type, helper, or composition for the thing it represents, not its first source, layout, or consumer. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-020` | A page-local configured composition does not become a reusable kit peer until a second real consumer demonstrates the shared contract. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-021` | Shell vocabulary such as panel, drawer, or tab is reserved for actual shell implementations that pass relevance and rendered-presentation checks. | `product-overlay` | Hummingbird overlay | proposed |
| `HVS-022` | Do not create content-router files merely to fill shell header/body slots; they can duplicate document titles and obscure ownership. | `product-overlay` | Hummingbird overlay | proposed |
| `HVS-023` | Variables may hydrate visible slots, but must not hide sections, duplicate scaffolds, or replace explicit semantic markup with parser-driven structure. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-024` | Parse external content into data, then render explicit semantic elements; runtime parsers do not own known page structure. | `candidate-review` | Felt cross-product review queue | proposed |
| `HVS-025` | Share repeated widgets and status chrome, not section outlines or shell slot routers. | `ai-helper-workflow` | UXD AI Helpers | proposed |
| `HVS-026` | When the document already owns its title, keep shell chrome close-only or untitled rather than displaying the same title twice. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `HVS-027` | One shared content root owns tab/drawer content; prose and preambles stay inside it, not in shell props or sibling wrappers. | `product-overlay` | Hummingbird overlay | proposed |
| `HVS-028` | Programmatic tab navigation activates the destination before measuring and scrolling to its landmark. | `candidate-review` | Felt cross-product review queue | proposed |
| `HVS-029` | Loading, error, empty, and ready remain visible branches under the content root; stable title/preamble stays visible when identity is known. | `canonical-seed` | FELTRFE-75 canonical catalog | proposed |
| `HVS-030` | Validate the running interface after architectural changes, including whole-surface effects, heading duplication, focus/ARIA, deep links, and async states. | `ai-helper-workflow` | UXD AI Helpers | proposed |

## Decision workflow

1. Review `canonical-seed` and `split-canonical-overlay` rules first.
2. Assign each accepted rule to one of the eight initial pattern families.
3. Mark the rule as requirement, recommendation, example, or documented exception.
4. Add stable semantic rule IDs only for accepted requirements with testable outcomes.
5. Keep wrapper names, repository architecture, routes, and product exceptions in overlays.
6. Record rejected or deferred decisions here instead of deleting their catalog provenance.

