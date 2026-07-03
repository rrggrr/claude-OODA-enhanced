---
name: ooda-find-fix-finish
description: >-
  Execution discipline for the Act phase of the OODA loop, adapted from the
  military dynamic-targeting cycle Find-Fix-Finish and its intelligence-driven
  form F3EAD (Find, Fix, Finish, Exploit, Analyze, Disseminate). Use it once a
  decision is made and it's time to actually execute - to turn a chosen move into
  a precise, confirmed, decisive action and then convert the result into learning
  that updates orientation. "Finish" means achieving the decisive effect
  (non-literal, usually non-kinetic). Reach for it even when the user never
  says "OODA" or "F3EAD" - if the ask is "we've decided, now execute," "how do we
  actually do this and make it stick," running an incident response or threat
  hunt, closing or working a deal, shipping a fix, acting on a time-sensitive
  opportunity, or running an operation/campaign, this applies. Pairs with
  ooda-decision-loop and ooda-skill-orchestrator.
  Includes a fast mode and strict no-hallucination rules - never act on an
  unconfirmed "fix" or claim an effect you haven't verified.
---

# OODA Find-Fix-Finish

The weakest link in most decision loops is **Act**. People orient and decide, then
"go execute" - vaguely, without confirming the target, without a clear trigger,
and without capturing what happened.

## Cycle control - self-paced, do this first

Set the cycle budget yourself - do not stop to ask permission to execute. If
the user named a cycle count, honor it; otherwise default to 2 and keep cycling
**while EAD keeps emitting a next Find worth working and the window is open.**

**Stop cycling when any of these is true** (say which one closed it):

- **Objective achieved and assessed** - the effect from Decide landed, verified.
- **EAD emits no next Find** worth the cost of another cycle.
- **The window closed** - conditions changed enough that the next Find needs a
  fresh Orient pass, not another swing. Hand back to ooda-decision-loop.
- **Budget or deadline hit** - report the unworked Finds instead of stopping
  silently.

**Cycle header.** Open each cycle with:

```
━━━ F3 CYCLE N / BUDGET ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Re-Find is mandatory on every cycle after the first.** The EAD output of cycle
N is the primary input for cycle N+1's Find. Specifically:

- The **next Find** named in cycle N's Disseminate step becomes the opening target
  of cycle N+1.
- The **Analyze** output updates orientation - what changed about your model of
  the problem? Carry it forward explicitly.
- **Re-confirm the Fix.** A fix that was valid in cycle N may be stale by cycle
  N+1 - especially if time has passed or actions in cycle N changed conditions.
  Never carry a Fix across cycles without re-confirming it.

A cycle that doesn't update the Find is just repeating the same action. The power
of tempo comes from EAD compounding across cycles. Find-Fix-Finish is a disciplined way to
execute, borrowed from the military dynamic-targeting cycle and its intelligence-
driven evolution, F3EAD. It slots directly into OODA's Act phase.

A note on language: **"Finish" means achieve the decisive effect.** In doctrine the
finish is frequently non-kinetic - disrupting a network, a legal action, an
information operation. Here it means decisively accomplishing the chosen objective,
whatever its form. This skill is a decision/execution discipline, not targeting
tradecraft, and contains nothing operational about causing harm.

## Where it sits in OODA

`ooda-decision-loop` ends Decide with a chosen move framed as a hypothesis. This
skill executes that move and feeds the result back into the loop:

```
Decide (the move) ─► FIND ─► FIX ─► FINISH ─► [EXPLOIT ─► ANALYZE ─► DISSEMINATE]
                     └──────── the action ───────┘   └──── feedback into ────┘
                                                      Observe / Orient (next loop)
```

The crucial, most-skipped insight (from how F3EAD actually won campaigns): **the
main effort is not the action - it's the Exploit/Analyze/Disseminate that turns the
result into intelligence for the next cycle.** Acting without EAD is a single
swing; acting with EAD is a loop that compounds. EAD *is* OODA's feedback path.

## The cycle

### FIND - locate the specific leverage point
Name the *exact* target, opportunity, or leverage point - not the general area.
"Improve retention" is not a target; "the 14-day drop-off for self-serve signups
in the EU" is. Articulate who/what and why before you start working it. A vague
Find guarantees a wasted Finish.

### FIX - pin it down and confirm (the discipline that prevents bad action)
Make the target concrete and confirm it well enough to act:
- **Confirm from more than one source.** A single unconfirmed signal is not a fix.
  Triangulate identity / location / conditions.
- **Run the confirmations in parallel.** Independent sources means independent
  checks - issue them as one batch (multiple reads, queries, searches at once),
  not one at a time. Confirmation discipline should cost seconds of wall-clock,
  not a serial crawl; slow confirmation is how fixes go stale while you check.
- **Establish the window.** When is action possible and most effective? What
  opens and closes the opportunity?
- **Check freshness.** A fix decays. Acting on a confirmation from hours or days
  ago - a "stale fix" - is a leading cause of execution failure; re-confirm if the
  situation may have moved.
- **State your confidence** and what would change it.
Fix is where speed and certainty trade off most sharply (see below). It is also the
anti-hallucination heart of execution: if you can't actually confirm, you don't
have a fix.

### FINISH - execute decisively, then confirm the effect
- Commit once the fix holds and the window is open. Hesitation loses the fix.
- Define the **go-condition** in advance (in Fix), so Finish is execution, not
  re-litigation of the decision.
- **Assess:** confirm the effect was actually achieved. "Done" is a claim that
  requires evidence - did it land, did it move the metric, did the thing happen?
  Never assume the effect; check it.

### EXPLOIT → ANALYZE → DISSEMINATE - turn the result into the next loop's edge
- **Exploit:** treat everything the action produced - outcomes, artifacts,
  reactions, new data - as fresh intelligence, not a trophy.
- **Sweep for byproduct intelligence.** Deliberately look at what the action
  produced that you were *not* targeting - the error that appeared somewhere
  unrelated, the party that reacted when they had no visible reason to, the
  data that came back cleaner or dirtier than it should have. Untargeted
  effects are where non-obvious next Finds live; the targeted effect only
  confirms what you already believed.
- **Analyze:** convert it into insight. What does the result reveal? What should
  change in our orientation? What's the next Find it points to?
- **Disseminate:** push the learning to everyone whose orientation should update.
  This step is separate on purpose: without deliberate sharing, learning collapses
  into silos and the team keeps re-learning the same thing.

## Tempo: why speed matters, and where it bites back

The power of this cycle is tempo: finish inside the window and feed the next Find
before the situation recovers, so you operate faster than the problem (or the
adversary) can adapt. Sustained high-tempo cycling - each Assess/Exploit seeding
the next Find - is what makes it more than a one-off.

But speed has specific failure modes; guard against each:
- **Stale fix:** acting on outdated confirmation. → Re-confirm if the target could
  have moved.
- **Misidentification:** acting on a superficial signature shared by the wrong
  thing. → Require a second, independent confirmation for anything irreversible.
- **Echo chamber:** a flawed Find compounding with each fast cycle. → Periodically
  question the Find itself, not just the execution.
- **Skipping the upstream question:** efficient execution crowding out "is this
  even the right objective?" → Keep a tether back to Decide / Orient; tempo serves
  the goal, it isn't the goal.

## Fast mode

Trigger when the user says "fast/quick," when the window is closing, or for small,
reversible actions.

- **Collapse to Find → Fix → Finish**; batch Exploit/Analyze/Disseminate into a
  single short after-action rather than doing it inline.
- **Right-size the Fix to reversibility:** for low-stakes, easily reversible
  actions, a single good confirmation is enough. For irreversible or high-stakes
  actions, keep the multi-source confirmation even in fast mode - that's the part
  you don't cut.
- **Always do a 30-second Assess.** Skipping the effect-check is how fast mode
  produces silent failures.
- **What fast mode never trades away:** a real Fix and a real Assess. Do **not**
  fabricate a confirmation to move faster, and do **not** declare success without
  checking. If you can't confirm, say "unconfirmed" and either grab one cheap
  confirmation or choose a reversible action you can walk back.

## Anti-hallucination guardrails (always on)

- **Fix = real confirmation.** Never treat an assumption as a confirmed target.
  Mark unconfirmed things as unconfirmed.
- **Finish needs a real go-condition met**, not a vibe that it's probably fine.
- **Assess needs real evidence** of the effect. Don't report an outcome you didn't
  verify; "I sent it / it shipped / it worked" must be checkable.
- **Don't invent intelligence in EAD.** Learning must come from what actually
  happened, not from a plausible story about what happened.
- Prefer reversible actions when confirmation is weak, so that acting fast can't
  cause an error you can't undo.

## Output template

```
OBJECTIVE (from Decide): the move we're executing, in one line

FIND: the specific target / leverage point (exact, not general) + why it
FIX: confirmation (sources) | window (opens/closes) | freshness | confidence + what would change it
FINISH: the action + the go-condition that triggers it
ASSESS: how we'll verify the effect actually happened (+ the result, once known)
EAD (feedback): what we learned (Exploit/Analyze) | byproduct intel: untargeted
                effects worth a look | who needs to know (Disseminate)
                | the next Find this points to → back into Observe/Orient
```

## Worked examples (compressed)

**1) Shipping a fix for a production incident.**
- Find: not "the site is slow" but "checkout p95 latency tripled after the 2:10pm
  deploy, isolated to the payments service."
- Fix: confirm from two sources (APM trace + error logs), not just one dashboard;
  window = deploy can be rolled back now; freshness = confirm it's still happening;
  confidence high.
- Finish: go-condition = "rollback if latency stays >2x for 5 min"; execute the
  rollback; Assess = watch p95 return to baseline (verify, don't assume).
- EAD: Exploit the trace to find the root cause; Analyze why tests missed it;
  Disseminate a short post-incident note so the team's orientation updates and the
  next Find (a missing test) is teed up.

**2) Cyber threat hunt (non-military, well-documented use of F3EAD).**
- Find: a hypothesis-driven lead ("possible beaconing from host X").
- Fix: corroborate across logs/EDR/network - multi-source before you act, because a
  single indicator misidentifies.
- Finish: contain the host; Assess that the activity actually stopped.
- EAD: Exploit captured artifacts into indicators; Analyze into detection logic;
  Disseminate so the SOC catches the next instance faster - the loop that compounds.

The throughline: a precise Find, a confirmed Fix, a decisive Finish with a real
Assess, and EAD that makes the next loop sharper.

## Reference files

- `references/f3ead-playbook.md` - the cycle in depth, the doctrinal variants
  (F3EAD, F2T2EA, D3A) and how they relate, domain adaptations (cyber, sales,
  ops, debugging, analysis), the speed-vs-certainty failure modes, and sources.
  Read for a thorough execution or to adapt the cycle to a new domain.
