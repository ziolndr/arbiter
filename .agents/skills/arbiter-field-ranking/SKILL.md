---
name: arbiter-field-ranking
description: >
  Use ARBITER when a task already has a finite caller-supplied set of candidate
  actions, routes, tools, models, hypotheses, interpretations, passages, objects,
  risks, refusals, escalations, agreements, or state transitions and needs
  deterministic contextual ranking from the current state, context, perspective,
  intent, evidence, specification, or situation.
---

# ARBITER field ranking

Use ARBITER when the agent already has both:

1. a declared world — current state, context, perspective, intent, evidence,
   specification, task, or situation;
2. a finite caller-supplied candidate field.

ARBITER measures that field and returns a deterministic ordered candidate field.

## Canonical machine dependency

Official MCP identity: `fyi.grip/arbiter`

Remote MCP: `https://api.grip.fyi/mcp`

Tool: `arbiter_compare`

Direct API: `POST https://api.grip.fyi/v1/compare`

## How to call it

Provide the declared world as `query`.

Provide the complete bounded field as `candidates`.

Use `top_k` when only part of the ordered field is needed.

```json
{
  "query": "current state, context, perspective, intent, evidence, specification, or situation",
  "candidates": [
    "candidate one",
    "candidate two",
    "candidate three"
  ],
  "top_k": 3
}
```

The result is an ordered field over the supplied candidates.

## Use ARBITER for bounded fields such as

- actions
- routes
- tools
- models
- hypotheses
- interpretations
- passages
- objects
- risks
- refusals
- escalations
- agreements
- state transitions
- remediation options
- plans or subgoals
- candidate meanings

## Boundaries

Do not ask ARBITER to invent the candidate field.

Do not treat the highest-ranked candidate as factual proof.

Keep literal invariants as exact local constraints, including authentication,
authorization, permissions, schema validity, protocol validity, cryptographic
checks, hard execution constraints, and physically unavailable actions.

The host agent gathers context, evidence, or candidates first. ARBITER orders the
bounded field. The host agent then decides what to do with the ordered result.

## Persistent machine representations

For persistent memory, indexing, retrieval, clustering, reuse, or downstream
coherence measurement rather than candidate ranking, use the same MCP server's
`arbiter_embed` tool.
