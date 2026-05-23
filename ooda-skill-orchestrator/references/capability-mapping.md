# Capability Mapping & Selection

Deeper guidance for inventorying what you can do and choosing well when you have
many options. The goal is a fast, accurate match of capability to the current OODA
phase — without inventing capabilities you don't have.

## Enumerate from verified sources only

Order of authority for "what do I have right now":

1. **The in-context skill list** (`available_skills` or equivalent) — authoritative
   for the session.
2. **A listing tool result** — if a `list_skills` / `list_plugins` / tool-list
   call exists, use it to confirm and to catch things not surfaced in context.
3. **Your actual tool list** — file ops, code execution, web search/fetch, and
   connected MCPs (messaging, mail, calendar, storage, data warehouses).

Things that are NOT verification: your memory of "skills like this usually exist,"
a plausible-sounding name, or the fact that the user asked for it. If you can't
point to a source, it isn't available.

Distinguish three states explicitly and never blur them:
- **Available now** — in the verified catalog.
- **Installable** — discoverable via a suggest/search tool but not yet installed
  (only relevant once you've found a gap).
- **Would-need-building** — no existing option; a candidate for Step 4.

## Map to OODA phases

Pre-filtering by phase is not just tidiness — selection accuracy falls when every
capability is weighed against every task simultaneously, and similarly-described
skills get confused. Narrow to the phase first, then choose.

- **Observe** (get current, honest inputs): web search/fetch; data/SQL and
  warehouse connectors; readers for files/docs/PDFs; messaging/mail connectors to
  see what's happening; monitoring/analytics tools.
- **Orient** (sense-make, analyze, pressure-test): research/synthesis skills;
  statistical analysis; data visualization; critique / red-team / review skills;
  domain-specific playbooks; the `ooda-decision-loop` orientation toolkit.
- **Decide** (structure the choice): decision frameworks; calculators and models;
  scoring/prioritization aids; risk assessment.
- **Act** (execute and instrument): document/spreadsheet/deck generation;
  messaging and automation; deployment/formatting; the `ooda-find-fix-finish`
  execution discipline.

A capability can serve more than one phase (a data skill informs both Observe and
Orient). Place it where it's doing work *this* turn.

## Selecting well when you have many options

- **Choose by purpose, not keywords.** Read what a skill is *for*. Keyword overlap
  ("report," "analysis") is a weak signal and a common source of mis-selection.
- **Surface the distinction on near-ties.** If two skills look interchangeable,
  state the difference in one line and pick the closer fit. If you can't tell them
  apart, that's a sign their descriptions overlap — note it as a cleanup gap.
- **Prefer the specific over the generic.** A company- or domain-specific skill
  almost always beats a general one for its domain.
- **Mind the cost of breadth.** More tools/skills in play is not free: it dilutes
  selection accuracy and burns context. Bring the few that fit the phase, not the
  whole shelf.
- **Use sequence inertia.** Within a task, the next useful capability is often
  predictable from the last (gather → analyze → visualize → write up). Don't
  re-derive the whole map every turn; advance along the natural chain and only
  re-inventory when the situation changes.

## When the catalog is the bottleneck

If you keep wishing for a capability across tasks, that's signal — but route it
through the build-vs-one-off bar in `building-skills.md` rather than building
reflexively. And if selection itself is unreliable because many skills have fuzzy,
overlapping descriptions, the highest-leverage fix is usually sharpening
descriptions, not adding more skills.
