# Felt layered design intelligence starter artifacts

This repository is a working starter architecture for converting product UI skills into shared Felt design intelligence, task-specific agent guidance, product overlays, and executable semantic validation. It demonstrates the proposed outputs of FELTRFE-75, FELTRFE-43, and FELTRFE-19.

> **Status:** Discussion starter. The classifications, patterns, and rules require review with Felt and the contributing product teams before they become design-system policy.

## Contents

- `comprehensive-rule-catalog.md` preserves 161 normalized Ansible/Syntara and Hummingbird rules, provenance, proposed layers, and AI Helpers coverage.
- `rule-disposition.md` assigns every catalog rule to canonical seed, cross-product review, AI-helper workflow, PatternFly reference, product overlay, or split treatment.
- `pattern-definitions.yaml` defines eight proposed FELTRFE-75 canonical pattern families and five workflow families.
- `agent-guidance.yaml` defines the FELTRFE-43 retrieval contract, workflow guidance, and task-specific templates.
- `semantic-rules.yaml` defines 35 proposed FELTRFE-19 validation contracts with validators and remediation.
- `product-overlays.yaml` maps shared patterns and workflows to Syntara and Hummingbird implementations and exceptions.
- `evaluations/representative-rule-set.md` preserves the original 25-rule pilot as a stable, non-authoritative evaluation fixture.

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

1. Review proposed decisions in `rule-disposition.md` with Felt, Ansible/Syntara, Hummingbird, PatternFly, and AI Helpers owners.
2. Mark each canonical candidate as a requirement, recommendation, example, exception, deferred rule, or rejected rule.
3. Approve or revise the eight initial pattern families and their applicability inputs.
4. Test the product overlays against real Syntara and Hummingbird code without moving wrapper names into Felt.
5. Implement a small deterministic subset of the 35 semantic contracts and measure false positives.
6. Run the representative evaluation set before and after FELTRFE-43 retrieval is available.

## Contributing

Use pull requests to propose changes. Preserve stable pattern and rule identifiers once consumers begin using them. A proposal should identify its source, owner, applicability, validation approach, and whether it belongs in shared Felt guidance or a product overlay.
