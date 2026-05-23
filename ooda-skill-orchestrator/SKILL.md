---
name: ooda-skill-orchestrator
description: >-
  Capability-awareness layer for the OODA decision loop. Use it at the start of
  and throughout any multi-step problem to (1) inventory the skills, tools, and
  connectors actually available right now, (2) map them to the OODA phase where
  they help (Observe / Orient / Decide / Act) and pick the best-fit one, and
  (3) spot capability gaps and offer to research, build, and retain a new or
  improved skill when that would genuinely accelerate the work. Reach for it even
  when the user never says "skill" or "OODA" — if the ask is "what can you do
  here," "use your tools/skills for this," "is there a skill for this," "what are
  you missing," "build/make a skill for this," "set me up to do X repeatedly," or
  "get better at X," this applies. Pairs with ooda-decision-loop (the framework)
  and ooda-find-fix-finish (execution). Includes a fast mode and strict
  no-hallucination rules for capability claims — never assert a skill or tool you
  have not verified exists.
---

# OODA Skill Orchestrator

A loop is only as good as the capabilities you bring to each turn of it. This
skill keeps you honest and current about what you can actually do — so you stop
under-using skills you have, stop pretending to have skills you don't, and turn
real, recurring gaps into durable new capabilities.

## Loop control — do this first, every time

Before starting capability inventory, **always ask the user:**

> "How many OODA loops should I orchestrate? (default: 2)"

Wait for the answer (or use 2 if unspecified). At the start of **each loop**,
re-run the capability inventory — do not assume the same skills available in loop
1 are the only options in loop 2. New skills may have been built or invoked, and
the relevant phase may have changed.

**Re-inventory on each loop.** Specifically:

- Did the previous loop's Act step surface a **new capability need**? If so,
  run the gap-analysis (Step 3) again now, before picking a tool for this loop.
- Did the previous loop **change what phase we're in**? A loop that starts in
  Observe/Orient often ends up in Act; the next loop may start in Observe again
  with new information — re-map capabilities for that phase.
- Did any skill get invoked in the last loop that produced output worth
  re-examining before picking the next capability? Treat that output as an
  Observe input for this loop.

Emit a capability-read header at the start of each loop:

```
CAPABILITY READ — Loop N / TOTAL  (phase: <current OODA phase>)
```

It sits alongside `ooda-decision-loop`: run the loop, and at each phase consult
this skill to bring the right capability to bear.

## The prime directive (read first): ground every capability claim

The most damaging failure here is hallucinating a capability — telling the user
"I'll use my X skill" or "I have a connector for Y" when you don't. Reasoning your
way to "there's probably a skill for this" is exactly how that error happens; more
deliberation tends to *increase* confident invention, not reduce it.

So: **a capability is real only if it appears in a verified source — the
`available_skills` list in your context, the result of a skill/plugin/tool listing
call, or a tool you can actually see in your tool list.** If it isn't there, it
doesn't exist for this task. Say "I don't have a skill for that (yet)" rather than
implying one. Never describe the output of a skill or tool you haven't actually
run.

## Step 1 — Inventory what you actually have

Build a short, current capability catalog from verified sources, in this order:

1. **In-context skills.** Read the `available_skills` / skill list already present
   in your context. This is authoritative for this session.
2. **Listing tools, if present.** If the environment exposes a skill/plugin lister
   (e.g., a `list_skills`, `list_plugins`, or equivalent tool), call it to confirm
   and fill gaps. Use a `suggest_skills` / `search_plugins`-type tool only to
   discover *installable* options when you've already found a gap (Step 3) — don't
   present uninstalled options as if they're available now.
3. **Tools & connectors.** Note non-skill capabilities too: file tools, code
   execution, web search/fetch, and any connected MCPs (Slack, Gmail, data
   warehouses, etc.). These matter as much as skills.

Keep the catalog compact: name + one-line "what it's for." Don't dump full
descriptions into the conversation; you're building a working index, not reciting.

## Step 2 — Map capabilities to OODA phases, then pick

Different phases need different capabilities. Pre-filter by phase before choosing —
selection accuracy drops when you weigh every capability against every task at
once, and skills with similar descriptions are easy to confuse.

| OODA phase | Capabilities that help | Examples of fit |
|---|---|---|
| **Observe** | Gather current, honest inputs | web search/fetch, data/SQL, connectors (Slack, email, drive), file readers |
| **Orient** | Make sense, analyze, pressure-test | research/analysis skills, data viz, critique/red-team, domain skills |
| **Decide** | Structure the choice | decision frameworks, calculators/models, risk or scoring aids |
| **Act** | Execute and instrument | doc/deck generation, messaging/automation, deploy/format, ooda-find-fix-finish |

Selection rules: choose by what the description says it's *for*, not by a keyword
match; if two skills look similar, name the distinction out loud and pick the
closer fit; if a domain skill exists for the situation (e.g., a company-specific
playbook), prefer it over a generic one. If nothing fits, that's a gap — go to
Step 3.

## Step 3 — Detect gaps and decide build vs. one-off

At each phase, ask: *is there a recurring sub-task where I have no good capability,
or only a weak/close one?* Then apply a real bar before proposing to build —
making a skill has a cost, and an overfit, single-use "skill" is clutter that
makes future selection worse.

**Build (or enhance) only if all of these hold:**

- **Recurrence:** the task will come up again, not just this once.
- **Generalization:** the solution works across different inputs, not just today's
  numbers/names.
- **Verifiability:** you can state how you'd know the skill works (a check, a test,
  a clear output spec).
- **Clean interface:** it has well-defined inputs and outputs and a crisp,
  distinctive description (descriptions are what make a skill get picked later).

If any fails, **solve it one-off** this time and move on. Enhance an existing skill
rather than create a near-duplicate whenever possible — duplicates degrade
selection for everyone.

## Step 4 — Offer, research, build, retain

When a gap clears the bar, **offer it; don't silently build.** Briefly tell the
user what's missing, what the skill would do, and why it would speed up the loop.

On approval:

1. **Research first.** A skill worth keeping must be insightful and non-obvious,
   not a thin wrapper around what you already know. Do real research (web + any
   relevant sources), find the genuinely useful procedure/heuristics, and cite it.
   If you can't find solid grounding, say so rather than padding with generic
   filler — a shallow skill is worse than none.
2. **Build with `skill-creator`.** Use the `skill-creator` skill to author it
   properly: a strong, distinctive `description` (this drives triggering), a lean
   SKILL.md with progressive disclosure to reference files, the "why" explained
   rather than rigid MUSTs, and a verification step.
3. **Verify before retaining.** Confirm it does what it claims (run its script,
   dry-run its procedure, or have a fresh reviewer check it). Don't add an
   unverified skill to the library.
4. **Retain it.** Package it (skill-creator's packager produces a `.skill`) and
   save it where the user keeps skills, then point them to it.

## Fast mode

Trigger fast mode when the user says "fast/quick," when the task is small or
time-boxed, or when you're mid-loop and just need the right capability *now*.

In one sentence: inventory from the in-context list (one listing call at most),
pick the obvious best-fit for the current phase, and defer gap-hunting unless it's
blocking — but never name a skill or tool you haven't verified.

- **Inventory:** trust the in-context `available_skills` list plus at most one
  listing call. Skip exhaustive plugin/connector discovery.
- **Selection:** pick the obvious best-fit for the current phase and move; don't
  agonize over near-ties — name your pick and proceed.
- **Gaps:** defer gap-hunting and skill-building unless a gap is *blocking* the
  task right now. Note deferred gaps in one line for later.
- **What fast mode never trades away:** truth about capabilities. Do **not** invent
  a skill/tool to save time. If you're unsure something exists, treat it as not
  available and say so. Speed comes from doing less searching, never from
  asserting more than you've verified.

## Anti-hallucination guardrails (always on)

- A capability claim must trace to a verified list/tool result. No source → no
  claim.
- "I could build/enhance a skill for this" is allowed (it's a proposal); "I have a
  skill for this" requires it to be in the verified catalog.
- Never fabricate a skill's output — run it or don't cite its result.
- When proposing a new skill, don't fabricate the research behind it; flag
  anything you couldn't verify.
- Distinguish, in your own words, available now vs. installable vs. would-need-
  building. Don't blur them.

## Output template

```
CAPABILITY READ (for: <task / current OODA phase>)
- Have & fit: <skill/tool> — <why it fits this phase>   [verified: in-context list / list call]
- Best pick now: <the one you'll use> + one-line why
- Weak/near-miss: <close-but-not-great capability>, if any
- Gaps: <recurring need with no good capability>, or "none blocking"
- Proposal (only if a gap clears the bar): build/enhance <name> — would do <X>,
  accelerates <phase> by <Y>; needs research on <Z>. Offer to proceed.
```

## Worked example (compressed)

*User: "Help me figure out why Q3 churn spiked and what to do — and set me up to
do this kind of analysis regularly."*

- **Inventory (verified):** in-context list shows data/SQL + viz + a decision
  framework; connectors include the warehouse and Slack. No "churn-analysis"
  skill exists — checked the list, not assumed.
- **Map:** Observe → SQL + warehouse connector; Orient → viz + statistical
  analysis; Decide → ooda-decision-loop; Act → Slack to share, doc-gen for the
  write-up.
- **Gap + bar:** "churn root-cause analysis" recurs (yes), generalizes across
  quarters/segments (yes), verifiable (define the output: drivers ranked with
  evidence), clean interface (inputs: date range, segment). Clears the bar →
  offer to build a `churn-root-cause` skill, after researching credible churn-
  decomposition methods. Don't build it silently.
- **Fast-mode variant:** skip the build offer for now; just run the analysis with
  existing data+viz skills, and note "gap: a reusable churn skill would help" in
  one line.

## Reference files

- `references/capability-mapping.md` — fuller guidance on enumerating capabilities,
  mapping them to phases, and selecting well when you have many (why too many
  options hurt, why descriptions decide selection). Read for a thorough inventory.
- `references/building-skills.md` — the build-vs-one-off bar in depth, the
  research requirement, using `skill-creator`, retention, and the canonical
  sources behind this skill. Read before proposing or building a new skill.
