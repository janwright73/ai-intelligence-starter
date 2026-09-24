# Representative UI skill instruction inventory

## Classification model

| Classification | Meaning |
|---|---|
| PatternFly reference | Current component APIs, props, tokens, or supported variants that should be retrieved from PatternFly rather than copied into Felt |
| Felt candidate | Cross-product UX intent that may belong in a canonical Felt pattern after review |
| Workflow helper | A repeatable agent workflow such as inspect, reuse, render, test, or validate |
| Product overlay | Local wrappers, architecture, naming, paths, hooks, constants, terminology, or deliberate exceptions |

Enforcement values are `deterministic`, `partially deterministic`, `evaluation`, and `human review`.

## Syntara current skill

Source: `syntara-orchestration/syntara`, `.claude/skills/frontend-patternfly-ux/SKILL.md`, devel branch.

| ID | Representative instruction | Classification | Proposed owner | Candidate pattern or artifact | Enforcement | Reasoning |
|---|---|---|---|---|---|---|
| SYN-01 | Check PatternFly first, raise confirmed gaps with UX, engage PatternFly, track temporary overrides, and resolve upstream. | Workflow helper | UXD AI Helpers with product participation | `patternfly-gap-workflow` | Partially deterministic | The decision workflow is reusable; issue labels and liaison details remain local. |
| SYN-02 | Use `Syn*` wrappers instead of raw PatternFly components for established Syntara compositions. | Product overlay | Syntara | Syntara component mapping | Deterministic | Wrapper selection is repository-specific and should not become central Felt policy. |
| SYN-03 | List, detail, form, error, and stacked-panel pages use prescribed page archetypes. | Mixed: Felt candidate plus product overlay | Felt defines archetype intent; Syntara maps it | `page-archetype` | Partially deterministic | Stable page identity and state placement may generalize; `SynPage` and `SynPanel` do not. |
| SYN-04 | `SynListPanelView` represents loading, refetching, empty, filtered-empty, and ready states declaratively. | Mixed | Felt plus Syntara | `asynchronous-content` | Partially deterministic | The state model is portable; the component and prop names are local. |
| SYN-05 | Form Save and Cancel actions live in a pinned panel footer rather than the page header, with documented exceptions. | Felt candidate plus product overlay | Joint review | `form-action-placement` | Evaluation or human review | Action persistence and proximity may generalize, while layout components and exceptions are product-specific. |
| SYN-06 | Protected tabs and controls remain hidden until permission resolution confirms access. | Felt candidate | Felt | `permission-aware-content` | Partially deterministic | Prevents a flash of unauthorized content and applies beyond Syntara. |
| SYN-07 | Breadcrumbs must not link to parent routes the user cannot access. | Felt candidate | Felt | `permission-aware-navigation` | Partially deterministic | Link availability should match effective authorization. |
| SYN-08 | Run-history rows use real link semantics so modified and middle clicks work; nested controls remain independently interactive. | Felt candidate | Felt | `navigable-row` | Deterministic plus rendered checks | The semantic requirement is portable; `HistoryListItemLink` remains local. |
| SYN-09 | Validation errors block publish, warnings do not, and both remain visible during save with different feedback variants. | Mixed | Product policy informed by Felt | `validation-severity` | Deterministic | The severity vocabulary may be shared, but blocking consequences are product policy. |
| SYN-10 | Canceling a running execution fires immediately without confirmation and self-disables while cancellation is pending. | Product exception with possible pattern candidate | Syntara; joint review for generalization | `slow-one-shot-action` | Deterministic | It is an intentional exception to generic confirmation guidance and needs explicit applicability metadata. |

## Automation Nexus legacy skill

Source: `automation-nexus/nexus-combined`, `.claude/skills/frontend-patternfly-ux/SKILL.md`, devel branch. The repository is archived and serves as provenance for the current Syntara guidance.

| ID | Representative instruction | Classification | Proposed owner | Candidate pattern or artifact | Enforcement | Reasoning |
|---|---|---|---|---|---|---|
| NEX-01 | Irreversible deletion uses a warning title, consequence explanation, acknowledgement checkbox, danger action, and secondary cancel action. | Felt candidate | Felt | `destructive-action` irreversible variant | Partially deterministic | The interaction contract is broadly reusable. |
| NEX-02 | Reversible pause or stop actions use confirmation without destructive acknowledgement. | Felt candidate | Felt | `destructive-action` reversible variant | Partially deterministic | Reversibility should change the confirmation tier. |
| NEX-03 | Confirmation severity increases from resource to user to global scope. | Felt candidate | Felt | `destructive-action` scope model | Evaluation plus deterministic mappings | The decision model is portable even when product language differs. |
| NEX-04 | After deletion, remove the item from the current list, return to the appropriate surface, and provide success feedback. | Mixed | Felt guidance plus product overlay | `post-action-feedback` | Partially deterministic | Feedback is reusable; route and cache behavior remain product-owned. |
| NEX-05 | Reuse a shared confirmation component rather than building separate dialogs for each destructive action. | Workflow helper plus product overlay | Product teams, supported by UXD helper | Reuse-before-create workflow | Deterministic repository analysis | Felt can recommend reuse but cannot prescribe a product wrapper. |

## Hummingbird outline-first-ui

Source: `redhat/hummingbird/tools`, `.cursor/skills/outline-first-ui/SKILL.md`.

| ID | Representative instruction | Classification | Proposed owner | Candidate pattern or artifact | Enforcement | Reasoning |
|---|---|---|---|---|---|---|
| HOF-01 | Use one visible scaffold and one return; keep structural conditionals readable instead of assembling whole sections in variables. | Workflow helper | Hummingbird initially; evaluate for UXD helper | `outline-first-authoring` | Static analysis plus human review | This is primarily a maintainability workflow, not cross-product UX intent. |
| HOF-02 | A user-facing section is owned by one concern-aligned file; shell components mount sections without owning their outlines. | Product architecture principle | Hummingbird | Hummingbird overlay | Static analysis | File ownership and naming are product architecture. |
| HOF-03 | Loading, error, empty, and ready branches remain explicit; stable section identity may remain visible while data loads. | Felt candidate | Felt | `asynchronous-content` | Partially deterministic | The state model and stable identity are portable. |
| HOF-04 | Section components read shared state from context when already inside a provider rather than prop-drilling internal data. | Product engineering guidance | Hummingbird or general engineering skill | Local architecture guidance | Static analysis with limitations | This is React architecture, not Felt design intent. |
| HOF-05 | Search for an existing PatternFly component, primitive, or section before creating a new abstraction; extract only after repeated structure is demonstrated. | Workflow helper | UXD AI Helpers | `reuse-before-create` | Repository search plus evaluation | This is a strong cross-product agent workflow but not a pattern record. |

## Hummingbird visible-scaffolding

Source: `redhat/hummingbird/tools`, `.cursor/skills/visible-scaffolding/SKILL.md`.

| ID | Representative instruction | Classification | Proposed owner | Candidate pattern or artifact | Enforcement | Reasoning |
|---|---|---|---|---|---|---|
| HVS-01 | Public components and page compositions accept and forward `className` and CSS-variable-safe `style` to their root host. | Product component API policy | Hummingbird | Hummingbird overlay | Deterministic | Extension policy is repository-specific even if other products may adopt it. |
| HVS-02 | When a product type resembles PatternFly props, subtract the PatternFly-owned fields and own only the remaining product data. | Workflow helper | UXD AI Helpers with PatternFly MCP | `patternfly-prop-reuse` | Static analysis plus review | Agents need current PF schemas plus a reuse workflow. |
| HVS-03 | Name a reusable type or helper for what it is, not for its first consumer. | Engineering guidance | Product teams or general engineering skill | Naming guidance | Human review | Valuable, but not a Felt UX behavior rule. |
| HVS-04 | Shell chrome and document content must not display duplicate titles; use one visible title and a clear accessible naming strategy. | Felt candidate | Felt | `composed-surface-heading` | Rendered DOM plus accessibility audit | This is a visible, cross-product UX and accessibility requirement. |
| HVS-05 | Validate presentation in the running UI; type checking and apparently correct code structure are insufficient. | Workflow helper | UXD AI Helpers | `render-and-validate` | Workflow enforcement | This belongs in the implementation and audit workflow. |

## Inventory findings

### Strong initial Felt candidates

1. `asynchronous-content` — supported independently by Hummingbird and Syntara.
2. `destructive-action` — deeply specified in Nexus and evolved in Syntara.
3. `permission-aware-content` — strong behavioral and accessibility rationale in Syntara.
4. `composed-surface-heading` — concrete rendered failure identified by Hummingbird.
5. `navigable-row` — semantic behavior with clear accessibility and browser expectations.

### Strong UXD AI Helper candidates

- Check PatternFly and existing repository capabilities before creating new components.
- Apply the relevant Felt pattern and product overlay.
- Keep UI states explicit during implementation.
- Render and inspect the completed interface.
- Run semantic and product validation.

### Guidance that should remain product-owned

- `Syn*`, `Nx*`, and Hummingbird wrapper names.
- `hb-content` and Syntara layout classes.
- Product folder structures and file naming.
- Local hooks, route conventions, endpoints, constants, and labels.
- Product-specific action exceptions and validation consequences.

