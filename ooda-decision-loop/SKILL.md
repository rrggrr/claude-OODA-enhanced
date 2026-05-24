---
name: ooda-decision-loop
description: >-
  A rigorous decision and problem-solving framework based on John Boyd's real
  OODA loop (Observe–Orient–Decide–Act) — the version where Orientation dominates
  and tempo means creating mismatches, not just moving fast. Use it for any hard,
  ambiguous, or high-stakes decision; a confusing situation that needs
  sense-making before acting; strategy or moves under uncertainty; a competitive
  or adversarial situation; an unfolding incident or crisis; a stuck or stalled
  problem; or a decision that already went wrong and needs a post-mortem. Reach
  for it even when the user never says "OODA" or "framework" — if the ask is
  "help me decide," "figure out what's going on," "what's our move," "we're
  stuck," "pressure-test this plan," or "why did this go sideways," this applies.
  Especially valuable when the situation keeps changing while you decide, when a
  wrong mental model would be costly, or when a faster, better decision cycle is
  a competitive edge.
---

# The OODA Decision Loop

A reusable engine for thinking and acting well under uncertainty — adapted
faithfully from USAF Colonel John Boyd's work, not the airport-bookshop cartoon.

## Loop control — do this first, every time

Before running the loop, **always ask the user:**

> "How many OODA loops should I run? (default: 2)"

Wait for the answer (or proceed with 2 if the user says "default" or doesn't
specify). Then run exactly that many full Observe → Orient → Decide → Act cycles.

**Iteration header.** Open each loop with a one-line banner:

```
━━━ LOOP N / TOTAL ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Re-orientation is mandatory on every loop after the first.** Loop 2+ must not
be a repeat. Before entering Observe, explicitly carry forward from the previous
loop:

- **What changed.** The concrete result of the Act step — new facts, outputs,
  errors, signals.
- **What was wrong in the prior orientation.** Name the assumption or model that
  reality disproved or confirmed.
- **Updated unknowns.** The gaps that survived (or newly appeared). Cheap to
  check now? Check them before Observing again.
- **Next Find.** If ooda-find-fix-finish ran in Act, pick up the next target it
  surfaced in its EAD output.

A loop that does not update orientation is not a loop — it's a repeated action.
Boyd's whole point is that each cycle should leave you more accurately oriented
than before; if the orientation didn't change, skip the loop and just act again.

## The one idea that makes this skill worth using

Most people treat OODA as a four-step checklist: look, think, choose, do, repeat
faster. That is the part Boyd spent the *least* time on. The real loop has three
properties that change how you use it:

1. **Orientation dominates.** The second O — your mental model of the situation,
   shaped by your background, assumptions, prior experience, and the analysis you
   do — silently determines what you even notice, which options occur to you, and
   how you act. Most bad decisions are not bad *choices*; they are good choices
   inside a wrong orientation. So this framework spends most of its energy on
   getting orientation right, and on *suspecting your own orientation first*.

2. **The goal of tempo is mismatch, not speed.** "Operating inside someone's OODA
   loop" does not mean rushing. It means acting in a way that makes the other
   party's picture of reality wrong — generating confusion, hesitation, and
   wasted effort on their side faster than they can correct. Sometimes that means
   moving fast; sometimes it means waiting, feinting, or changing the terms so
   their existing plan no longer fits. Speed for its own sake is a trap.

3. **It's a learning loop, not a pipeline.** Boyd labeled "Decide" as
   *Hypothesis* and "Act" as *Test*. You are running experiments against reality
   and updating, not executing a plan. Skilled operators often skip the explicit
   Decide step entirely (this is "implicit guidance" — see below). The point of
   the loop is to keep your orientation matched to a world that won't hold still.

If you remember nothing else: **fix your orientation, then act in a way that
breaks theirs.**

## When to use this, and when not to

Use it for genuinely uncertain, consequential, or fast-moving problems — strategy,
competitive moves, incidents, ambiguous diagnoses, "we're stuck," and decision
post-mortems.

Don't force it on **clear, well-understood tasks** with a known right answer
(just do the known-good procedure), or on problems whose only difficulty is
computation or fact-lookup. If the situation is *clear*, OODA collapses to "act."
The framework earns its keep precisely when the situation is complicated,
complex, or chaotic — see the Cynefin match in `references/orientation-toolkit.md`.

## How to run the loop

Work through the four phases below, but treat them as a system with feedback, not
a to-do list. The heavy lifting is in Orient. Adjust depth to the stakes: a
two-minute pass for a small call, a full written pass for a big one.

### 1. Observe — get current, honest inputs

Goal: assemble what's actually happening, right now, including the things that
contradict your current story.

- State the **situation and the decision** in one or two plain sentences. What
  must be decided, by when, and what happens if you do nothing?
- List **what's unfolding**: external facts, what others are doing, how the
  environment is changing, and the results of your own recent actions (the
  feedback from your last Act lands here).
- Flag **freshness and gaps**: which observations are stale, secondhand, or
  assumed? What would you *most* want to know that you don't? Cheap observation
  beats expensive guessing — note what's quick to go check.
- Watch for the **expectation gap**: where is reality diverging from what you
  predicted? That gap is the most information-rich thing on the table.

Observation is cheap and being wrong here is recoverable — so err toward
gathering one more real data point before you commit, especially the data point
that could prove you wrong.

### 2. Orient — build (and distrust) the mental model

This is the decisive phase. Goal: form the truest-possible picture *and* expose
where your own picture is most likely fooling you.

Do these, in roughly this order — but first, before evaluating any hypothesis:

- **Write what would change your conclusion.** Before you look at competing
  hypotheses or weigh evidence, write one sentence: "I would conclude the
  opposite if ___." If Orient closes without addressing that sentence, the
  orientation is incomplete. A falsifier written after the evidence is in is
  not a falsifier — it's a rationalization.

- **Name your current orientation out loud.** What story are you telling about
  this situation? What does that story assume? Boyd's point is that this model is
  shaped by your background, your culture/incentives, your prior experience, the
  new information at hand, and the analysis you do — and any of those can mislead.
  Saying it explicitly is what lets you inspect it.
- **Generate competing hypotheses (at least three).** Force a few genuinely
  different explanations of what's going on — not one explanation plus two
  strawmen. Then ask which evidence would *distinguish* them. (Analysis of
  Competing Hypotheses; details in the toolkit reference.)
- **Run a fast premortem.** "It's three months from now and this went badly —
  why?" Premortems surface the failure modes your optimism is hiding.
- **Red-team your own view.** What would a sharp opponent, or your most skeptical
  colleague, attack first? If there's a real adversary or competitor, model
  *their* orientation: what do they believe, and where is it wrong or slow?
- **Steelman the option you're leaning away from.** Before concluding, write
  the strongest possible case for the choice you are currently not favoring.
  Not a strawman — the actual best version of the opposing argument. Red-teaming
  attacks your view from outside; this step forces you to *inhabit* the other
  side. If you can't write it, you don't understand the tradeoff well enough
  to decide.
- **Update like a Bayesian.** Treat new information as evidence that should move
  you, and be honest about evidence that cuts against your favored story
  ("incestuous amplification" — only listening to what confirms you — is Boyd's
  named failure mode).
- **Match the situation type (Cynefin).** Clear → just apply best practice.
  Complicated → analyze / get an expert. Complex → run small safe-to-fail probes
  and watch what emerges (don't over-plan). Chaotic → act to establish basic
  stability first, then re-orient. The right *kind* of loop depends on this.
- When a model feels stuck, **tear it down and rebuild** (Boyd's "destruction and
  creation"): break the situation into pieces and recombine them a different way,
  borrowing structure from an unrelated domain. The toolkit reference has a
  procedure for this.

Output of this phase: a current best read, the top one or two uncertainties that
would change your mind, and an explicit note of *the single assumption most
dangerous to be wrong about*.

For the full mechanics of each tool above, read
`references/orientation-toolkit.md`.

### 3. Decide — commit to a hypothesis (often a test, not a bet-the-farm move)

Goal: choose the next action as the smallest, most reversible move that will
either work or teach you something fast.

- Frame the decision as a **hypothesis**: "We believe X; if we do Y we expect Z."
- Prefer **reversible, observable** moves. What's the cheapest action whose result
  will sharpen your orientation? Favor options that keep future options open.
- State **what would falsify it** — the signal that tells you you're wrong — and
  *when* you'll check.
- **Skip vs. deliberate:** if this is familiar territory and your orientation is
  trustworthy, it's fine to act almost reflexively (implicit guidance). If the
  stakes are high or the situation is novel/complex, slow down and make the
  decision explicit. Knowing which mode you're in is itself a decision.

### 4. Act — test reality, instrument the result, loop

- Take the action — but set it up so you can **see the outcome**. An action you
  can't observe the effect of is a wasted loop.
- Decide *in advance* what observation will pull you back into the loop, and how
  soon. Then actually re-observe; don't fall in love with the plan.
- In competitive settings, ask whether this action **changes the other party's
  situation faster than they can re-orient** — see tempo, below.

## Tempo and competition: operating inside the other loop

When there's an adversary, competitor, or even an indifferent fast-moving market,
the aim is to make *their* orientation wrong. You do that by changing the
situation in ways that are cheap for you and expensive for them to respond to
("fast transients" / asymmetric moves), and by being unpredictable enough that
their model of you stays stale. The win condition is when they start reacting to
a world that no longer exists — hesitating, thrashing, or fighting the last move.

Crucially, this is **not** a license to act hastily. Faster cycling only helps if
each cycle is *better oriented* than theirs; a fast loop running on a wrong model
just reaches the wrong place sooner. When you're behind on orientation, the right
move is often to slow down, gather, and re-orient before re-engaging.

Full treatment, with concrete patterns and examples, in
`references/tempo-and-competition.md`.

**Speed multipliers** — factors that accelerate the loop without degrading orientation:

| Factor | Effect |
|---|---|
| Pre-planned responses (runbooks) | Skip D phase for known scenarios |
| Distributed authority | Parallel loops at different levels simultaneously |
| Sharp mental models | Faster Orient — pattern recognized, not built from scratch |
| Good observability | Faster Observe — data already surfaced, not hunted |
| Practice / drills | Faster Act — execution is muscle memory |

**Speed killers** — where loops stall; diagnose and fix:

| Failure | Symptom | Fix |
|---|---|---|
| Waiting for certainty | Loop stalls at Observe or Orient | Set a decision deadline; act on 70% and instrument |
| Hierarchical approval | Latency spike at Decide | Pre-authorize classes of action; push authority down |
| Information overload | Observe phase never closes | Filter to 3-5 key indicators; ignore the rest |
| Orientation lock | Stuck on one hypothesis | Force two genuine alternatives; run premortem |
| Perfect solution seeking | Decide phase never closes | Prefer reversible moves; commit and observe |
| Single loop | Not cycling | Time-box each phase; Act creates the next Observe |

## The implicit-guidance shortcut (and its trap)

Experts mostly run Observe → Orient → Act, with Decide bypassed: good orientation
fires the right action directly, no deliberation. This is real and powerful — it's
why masters seem fast. The trap is that the *same* shortcut, running on a
biased or outdated orientation, produces confident, fast, wrong action. Rule of
thumb: trust implicit guidance in familiar, stable, low-stakes situations; force
explicit orientation and decision when the situation is novel, the stakes are
high, or you notice your predictions have been off lately.

One additional trigger: if Orient produces a conclusion that conveniently
confirms something you already built, already paid for, or already recommended
— treat that as a yellow flag. Not proof of error, but reason to require one
concrete piece of evidence pointing the other way before closing the loop. The
trap of implicit guidance is not just a stale mental model; it's a mental model
shaped by your own prior investment.

## Team OODA — parallel loops with model tiers

In multi-agent or team contexts, different roles run simultaneous loops rather
than waiting for a single serial pass. Each loop is cheaper and faster than one
omnibus loop, and the results feed a coordination layer that re-orients everyone.

**Typical parallel structure:**

| Role | Loop focus | Recommended model tier | Why |
|---|---|---|---|
| Observe agent | Data collection: metrics, logs, web scraping, API pulls, structured extraction | **Haiku** | Fast, cheap, excellent at structured extraction; no deep reasoning needed |
| Observe agent (unstructured) | Reading PDFs, dense text, ambiguous signals, multi-source synthesis | **Sonnet** | More capable parsing without full Opus cost |
| Orient agent | Pattern matching against known templates, simple hypothesis triage | **Sonnet** | Strong reasoning at reasonable cost |
| Orient agent (hard cases) | Novel situations, adversarial modeling, competing hypotheses, destruction & creation | **Opus** | Full reasoning power reserved for where it moves the needle |
| Decide agent | Hypothesis selection for routine, well-scoped decisions | **Sonnet** | Capable enough; Opus not needed for bounded choices |
| Decide agent (high stakes) | Irreversible, novel, or high-blast-radius choices | **Opus** | The one place to spend the extra capability budget |
| Act agent | Code execution, API calls, document generation, tool use | **Haiku / Sonnet** | Haiku for mechanical tasks; Sonnet when output quality matters |
| Coordination / Orient synthesis | Merging parallel observations into a shared orientation | **Opus** | This is the highest-leverage reasoning step; don't skimp |

**Model selection rule of thumb:** Start at Haiku for any phase that is
predominantly *retrieval or extraction*. Escalate to Sonnet when *synthesis or
structured reasoning* is required. Escalate to Opus only when the phase involves
*novel orientation, adversarial modeling, or irreversible decisions* — the places
where a wrong model is expensive.

**Shared orientation is the coordination contract.** Parallel loops only help if
the results converge. After parallel Observe loops complete, a single Orient pass
(Opus) must integrate all inputs into one shared mental model before Decide runs.
Without this, parallel teams optimize against different pictures of reality.

**Pre-planned responses** short-circuit the loop for known scenarios: the Observe
agent pattern-matches to a runbook, Decide is skipped, Act fires directly. This
is where Haiku shines — fast classification, low cost, high throughput.

## Fast mode (speed over certainty — without hallucinating)

Tempo is the whole point of OODA, so this skill ships a fast mode. Trigger it when
the user says "fast/quick," when a window is closing, or when the call is small or
reversible.

What fast mode does:

- **One compressed pass.** A two-line Observe, a one-line Orient (your single best
  read plus the single most dangerous assumption), the smallest reversible Decide,
  and Act. Skip the full toolkit.
- **Fewer inputs, chosen well.** Gather only the one or two observations that most
  change the answer; don't seek completeness.
- **Bias to reversible moves.** When you're acting on thin information, prefer
  actions you can walk back — that's what makes speed safe.

What fast mode never trades away — the anti-hallucination floor (this holds in
*every* mode):

- **Don't invent facts, numbers, sources, or certainty.** Moving fast means
  reasoning from less, not making more up.
- **Separate known / assumed / unknown,** and say which is which. Label your
  confidence. An explicit assumption is fine; a fabricated fact is not.
- **Flag the one check** that would most reduce the risk of being wrong, even if you
  proceed before doing it.
- **If you can't verify something that matters, say so** and either grab one cheap
  confirmation or pick a reversible path. Speed comes from doing less, never from
  asserting more than you know.

## Loop health check

Run this self-audit when a loop feels stuck or slow. All six should be true:

1. **Observe:** Am I looking at the current actual state — not assumptions or 5-minute-old data?
2. **Orient:** Have I named at least two genuinely different hypotheses — not one story plus strawmen?
3. **Decide:** Is my decision actionable and time-bound — not "we should probably…"?
4. **Act:** Will my action create an observable signal I can actually check?
5. **Cycling:** Am I completing loops — or stuck in one phase?
6. **Tempo:** Is my loop speed matched to the urgency — fast enough to matter, not so fast I'm acting on stale orientation?

If any fails: stop, name which phase is stuck, apply the fix from the speed killers table above.

## Common misconceptions to avoid

- "OODA just means be faster." No — it means be better-oriented and create
  mismatches. Speed without orientation is dangerous.
- "It's a strict sequence." No — the phases run concurrently and feed back;
  you're often observing and acting at once.
- "Decide is the important step." No — Orient is. Decide is sometimes skipped
  entirely.
- "It's about individual snap decisions." Boyd cared most about *organizations*:
  shared orientation and mutual trust are what let a team act fast without
  waiting for orders. (See the theory reference.)

## Output template

When you apply this skill to a real problem, present the analysis like this
(scale the depth to the stakes; in conversation you can render it as tight prose
rather than headers):

```
SITUATION (Observe)
- Decision to make + deadline + cost of inaction
- Key facts / what's changing / freshest signals
- Biggest unknown worth going to check

ORIENTATION (Orient)
- Current read of what's going on
- 2–3 competing hypotheses + the evidence that would separate them
- Premortem: top ways this goes wrong
- Most dangerous assumption to be wrong about
- Situation type (clear / complicated / complex / chaotic) → loop style

MOVE (Decide)
- The hypothesis we're testing: "We believe X; doing Y; expect Z"
- Why this move (reversible? cheap? keeps options open?)
- What would falsify it, and when we'll check

ACT + LOOP
- Concrete next action(s)
- What we'll observe to know if it worked
- Trigger + timing to re-enter the loop
- (If competitive) tempo read: how this affects the other side's orientation
```

## Worked example (compressed)

*A SaaS team is losing deals to a cheaper competitor and the instinct is to cut
price.*

- **Observe:** Win rate down 15% this quarter; losses cluster in mid-market;
  sales says "they're cheaper." Freshness gap: no one has read the actual lost-deal
  notes — that's a cheap thing to go check.
- **Orient:** Naming the orientation: "we're losing on price." Competing
  hypotheses: (a) price; (b) the competitor's faster onboarding; (c) a missing
  integration. Evidence that separates them lives in the lost-deal notes and a few
  buyer calls. Premortem: "we cut price, margins fall, and we *still* lose because
  it was never price." Most dangerous assumption: that price is the cause.
  Complex situation → probe before committing.
- **Decide:** Hypothesis: "Losses are driven by onboarding speed, not price." Test
  = offer 3 at-risk prospects a white-glove 48-hour onboarding (reversible, cheap)
  rather than a price cut. Falsifier: if they still churn to the competitor,
  it's not onboarding.
- **Act + loop:** Run the trial this week; instrument by tracking those 3 deals
  and logging the stated reason; re-orient in two weeks. Tempo read: a price cut
  is easy for the competitor to match (bad transient); a faster onboarding
  capability is harder for them to copy quickly (good transient).

The lesson the framework forces: the obvious move (cut price) was an action inside
an unexamined orientation. One cheap orientation step changed the move.

## Companion skills

This is the core framework; two companions extend it and are worth invoking
together on hard, multi-step work:

- **`ooda-skill-orchestrator`** — keeps you aware of the skills and tools you
  actually have at each phase, picks the best-fit one, and offers to research and
  build a new skill when a real capability gap is slowing the loop. Use it to bring
  the right capability to Observe/Orient/Decide/Act.
- **`ooda-find-fix-finish`** — an execution discipline for the **Act** phase
  (Find → Fix → Finish → Exploit/Analyze/Disseminate). Hand off to it once Decide
  has chosen the move, to execute precisely and turn the result into learning that
  re-enters this loop.

## Reference files

- `references/orientation-toolkit.md` — the working tools for the Orient phase:
  competing hypotheses, premortem, red-teaming, Bayesian updating, destruction &
  creation, and the Cynefin situation-match. Read this when you're doing a serious
  orientation pass.
- `references/tempo-and-competition.md` — operating inside another's loop,
  generating mismatches/fast transients, and when speed helps vs. hurts. Read for
  competitive or adversarial problems.
- `references/theory-and-sources.md` — Boyd's real loop diagram (every component,
  the implicit-guidance and feedback links), the organizational ideas, the
  misconceptions, and full citations. Read when you want the grounding or to teach
  it.
