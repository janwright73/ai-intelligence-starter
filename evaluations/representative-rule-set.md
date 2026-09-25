# Representative 25-rule evaluation set

This fixture preserves the original pilot sample used to test the layered architecture. It is not an active rule inventory; authoritative provenance and disposition live in `comprehensive-rule-catalog.md` and `rule-disposition.md`.

## Intended use

- Compare agent output before and after Felt guidance retrieval.
- Verify that product overlays are selected without leaking wrapper names into canonical guidance.
- Test that semantic validators return stable rule IDs and remediation.
- Retain the same sample across architecture iterations so results remain comparable.

## Sample rules

| Pilot ID | Original representative instruction | Original classification | Expected artifact or pattern |
|---|---|---|---|
| `SYN-01` | Check PatternFly first, raise confirmed gaps with UX, engage PatternFly, track temporary overrides, and resolve upstream. | Workflow helper | `patternfly-gap-workflow` |
| `SYN-02` | Use `Syn*` wrappers instead of raw PatternFly components for established Syntara compositions. | Product overlay | Syntara component mapping |
| `SYN-03` | List, detail, form, error, and stacked-panel pages use prescribed page archetypes. | Mixed: Felt candidate plus product overlay | `page-archetype` |
| `SYN-04` | `SynListPanelView` represents loading, refetching, empty, filtered-empty, and ready states declaratively. | Mixed | `asynchronous-content` |
| `SYN-05` | Form Save and Cancel actions live in a pinned panel footer rather than the page header, with documented exceptions. | Felt candidate plus product overlay | `form-action-placement` |
| `SYN-06` | Protected tabs and controls remain hidden until permission resolution confirms access. | Felt candidate | `permission-aware-content` |
| `SYN-07` | Breadcrumbs must not link to parent routes the user cannot access. | Felt candidate | `permission-aware-navigation` |
| `SYN-08` | Run-history rows use real link semantics so modified and middle clicks work; nested controls remain independently interactive. | Felt candidate | `navigable-row` |
| `SYN-09` | Validation errors block publish, warnings do not, and both remain visible during save with different feedback variants. | Mixed | `validation-severity` |
| `SYN-10` | Canceling a running execution fires immediately without confirmation and self-disables while cancellation is pending. | Product exception with possible pattern candidate | `slow-one-shot-action` |
| `NEX-01` | Irreversible deletion uses a warning title, consequence explanation, acknowledgement checkbox, danger action, and secondary cancel action. | Felt candidate | `destructive-action` irreversible variant |
| `NEX-02` | Reversible pause or stop actions use confirmation without destructive acknowledgement. | Felt candidate | `destructive-action` reversible variant |
| `NEX-03` | Confirmation severity increases from resource to user to global scope. | Felt candidate | `destructive-action` scope model |
| `NEX-04` | After deletion, remove the item from the current list, return to the appropriate surface, and provide success feedback. | Mixed | `post-action-feedback` |
| `NEX-05` | Reuse a shared confirmation component rather than building separate dialogs for each destructive action. | Workflow helper plus product overlay | Reuse-before-create workflow |
| `HOF-01` | Use one visible scaffold and one return; keep structural conditionals readable instead of assembling whole sections in variables. | Workflow helper | `outline-first-authoring` |
| `HOF-02` | A user-facing section is owned by one concern-aligned file; shell components mount sections without owning their outlines. | Product architecture principle | Hummingbird overlay |
| `HOF-03` | Loading, error, empty, and ready branches remain explicit; stable section identity may remain visible while data loads. | Felt candidate | `asynchronous-content` |
| `HOF-04` | Section components read shared state from context when already inside a provider rather than prop-drilling internal data. | Product engineering guidance | Local architecture guidance |
| `HOF-05` | Search for an existing PatternFly component, primitive, or section before creating a new abstraction; extract only after repeated structure is demonstrated. | Workflow helper | `reuse-before-create` |
| `HVS-01` | Public components and page compositions accept and forward `className` and CSS-variable-safe `style` to their root host. | Product component API policy | Hummingbird overlay |
| `HVS-02` | When a product type resembles PatternFly props, subtract the PatternFly-owned fields and own only the remaining product data. | Workflow helper | `patternfly-prop-reuse` |
| `HVS-03` | Name a reusable type or helper for what it is, not for its first consumer. | Engineering guidance | Naming guidance |
| `HVS-04` | Shell chrome and document content must not display duplicate titles; use one visible title and a clear accessible naming strategy. | Felt candidate | `composed-surface-heading` |
| `HVS-05` | Validate presentation in the running UI; type checking and apparently correct code structure are insufficient. | Workflow helper | `render-and-validate` |

## Evaluation contract

For each scenario, record:

1. Patterns and rule IDs retrieved.
2. PatternFly references consulted.
3. Product overlay mappings or exceptions applied.
4. Generated implementation or design decision.
5. Validator results with evidence, severity, and remediation.
6. Human rating for correctness, relevance, duplication, and product fit.

A passing run must keep central Felt guidance free of product wrapper names while still applying those wrappers through the selected overlay.

