# Felt layered design intelligence starter artifacts

This bundle is a first-pass decomposition of representative guidance from the Hummingbird and Automation Nexus or Syntara UI skills. It demonstrates the proposed outputs of FELTRFE-75, FELTRFE-43, and FELTRFE-19.

> **Status:** Discussion starter. The classifications, patterns, and rules require review with Felt and the contributing product teams before they become design-system policy.

## Contents

- `instruction-inventory.md` classifies 25 representative instructions by source, ownership, portability, enforcement approach, and candidate Felt pattern.
- `pattern-definitions.yaml` shows the FELTRFE-75 source-of-truth format for five candidate patterns.
- `agent-guidance.yaml` shows the concise, task-relevant guidance FELTRFE-43 could deliver through MCP or a thin skill.
- `semantic-rules.yaml` shows the FELTRFE-19 rule and diagnostic model.
- `product-overlays.yaml` shows how Syntara and Hummingbird can map shared Felt patterns to different implementations.

## Source material

- [Hummingbird: outline-first-ui](https://gitlab.com/redhat/hummingbird/tools/-/tree/main/.cursor/skills/outline-first-ui?ref_type=heads)
- [Hummingbird: visible-scaffolding](https://gitlab.com/redhat/hummingbird/tools/-/tree/main/.cursor/skills/visible-scaffolding?ref_type=heads)
- [Automation Nexus: frontend-patternfly-ux (legacy)](https://github.com/automation-nexus/nexus-combined/blob/devel/.claude/skills/frontend-patternfly-ux/SKILL.md)
- [Syntara: frontend-patternfly-ux](https://github.com/syntara-orchestration/syntara/blob/devel/.claude/skills/frontend-patternfly-ux/SKILL.md)

These links identify the source material reviewed for this starter bundle. The repository does not redistribute those source skills.

## RFE ownership

| RFE | Owns |
|---|---|
| FELTRFE-75 | Pattern schema, canonical definitions, identifiers, provenance, product-overlay contract, governance, and seed catalog |
| FELTRFE-43 | Intent-based retrieval, concise agent guidance, generated prompt fragments, workflow-helper integration, and agent evaluations |
| FELTRFE-19 | Executable constraints, validation adapters, structured diagnostics, fixtures, severity, and false-positive measurement |

## Interpretation boundary

The source skills are evidence, not automatically authoritative cross-product policy. A rule becomes a Felt rule only after cross-product review. Product wrapper names, repository paths, hooks, constants, and workflow-specific exceptions remain product-owned.

## Recommended review sequence

1. Review the classifications in `instruction-inventory.md` with the source-product teams.
2. Approve, revise, or reject the five candidate patterns.
3. Confirm which rules are requirements, recommendations, or examples.
4. Test the product overlays against real Syntara and Hummingbird code.
5. Select a small set of deterministic FELTRFE-19 validators.
6. Run paired agent tasks before and after FELTRFE-43 guidance is available.

## Contributing

Use pull requests to propose changes. Preserve stable pattern and rule identifiers once consumers begin using them. A proposal should identify its source, owner, applicability, validation approach, and whether it belongs in shared Felt guidance or a product overlay.
