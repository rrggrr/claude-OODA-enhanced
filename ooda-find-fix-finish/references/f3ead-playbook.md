# Find-Fix-Finish / F3EAD Playbook

Depth reference for executing the cycle well and adapting it to a new domain. Read
when you're running a real, consequential execution or porting the method.

## Contents
1. The cycle, step by step
2. The doctrinal variants and how they relate
3. How it nests with OODA
4. Speed vs. certainty: the failure modes
5. Domain adaptations
6. Sources

---

## 1. The cycle, step by step

**Find** - establish the starting point: the specific target, opportunity, or
leverage point, and why it matters. Discipline: you must articulate *who/what and
why* before working it, which prevents undirected effort.

**Fix** - develop the situation until you have enough fidelity to act: confirm
identity/location/conditions, ideally from multiple sources; understand the
pattern (when/where the opportunity exists); establish the window. Discipline:
multi-source confirmation; a single source is not a fix.

**Finish** - take decisive action within the window, then confirm the effect.
Discipline: the trigger condition is defined during Fix; once it's met, hesitation
loses the fix. Always assess the effect.

**Exploit** - treat everything the action yields (results, artifacts, reactions,
data) as new intelligence to feed the next cycle, not as a closed-out result.

**Analyze** - convert exploitation material into insight that drives the next
Find and updates orientation.

**Disseminate** - push the result and the learning across everyone whose picture
should update, deliberately, to defeat silos. ("A network to defeat a network.")

The historically decisive point: in F3EAD the *main effort is the EAD*, not the
F3. The action exists to generate intelligence that powers the next, better action.
That inversion is what turns single strikes into a compounding loop.

## 2. The doctrinal variants and how they relate

Terminology is used loosely in secondary sources; keep these straight.

- **F3 - Find, Fix, Finish.** The core triad; the legacy formulation. "Finish" is
  frequently non-kinetic (disruption, legal action, information operations).
- **F3EAD - Find, Fix, Finish, Exploit, Analyze, Disseminate.** The
  intelligence-driven version (popularized by special-operations practice in Iraq,
  ~2004-2009). Documented as an "alternate" targeting methodology in U.S. Army
  targeting doctrine; in practice the primary method for time-sensitive,
  network-focused work. Best for execution against fleeting/short-suspense targets.
- **F2T2EA - Find, Fix, Track, Target, Engage, Assess.** The joint/air "kill
  chain" for dynamic targeting (Joint Publication 3-60); origin in 1990s airpower
  doctrine aiming for very short response times. In practice, Track/Target
  are often folded into Fix by modern sensor fusion.
- **D3A - Decide, Detect, Deliver, Assess.** The deliberate-targeting, planning
  method for conventional forces. A useful pairing rule from the literature: *D3A
  is the planning tool; F3EAD is the execution tool for short-suspense targets.*
  F3EAD has no explicit "Decide" because that happens upstream (in OODA terms, in
  Orient/Decide).

Mapping the three onto each other (approximate):

| F3EAD | F2T2EA | OODA |
|---|---|---|
| Find | Find | Observe/Orient |
| Fix | Fix (+Track/Target) | Orient |
| Finish | Engage | Act (the action) |
| Exploit/Analyze/Disseminate | Assess | feedback → Observe/Orient |

## 3. How it nests with OODA

Two relationships, both useful:

1. **It implements OODA's Act.** When the loop reaches "do the thing," F3EAD is the
   disciplined sequence by which the act is prepared (Find/Fix), executed (Finish),
   and learned from (EAD).
2. **It is itself an OODA loop** at the intelligence level: Exploit observes,
   Analyze orients, Disseminate acts (into the next Find). This is why practitioners
   describe F3EAD in Boyd's own terms - operating faster than the adversary can
   react, "getting inside the decision cycle." No doctrine formally diagrams the
   OODA↔F3EAD relationship; it's an analytical correspondence, but a clean one.

## 4. Speed vs. certainty: the failure modes

High tempo is the source of advantage and the source of catastrophe. Name the
failure modes so you can guard them:

- **Stale fix** - acting on a confirmation that has expired; the target/situation
  moved. Guard: re-confirm freshness before Finish for anything mobile.
- **Misidentification** - a behavioral/surface signature matched the wrong thing.
  Guard: require a second independent confirmation for irreversible actions.
- **Intelligence echo chamber** - a flawed Find, cycled fast, deepens the error
  each loop. Guard: periodically challenge the Find itself, not just execution.
- **Strategic displacement** - tactical execution becomes so efficient it crowds
  out the upstream question, "is this the right objective/target class?" Guard:
  keep a tether to Orient/Decide; tempo serves the goal.
- **Out-of-order execution** - the steps are often run out of order in practice,
  which means the discipline lives in judgment, not in checklist compliance. Guard:
  know *why* each step exists so you can compress safely instead of skipping blindly.

The general rule for compressing under time pressure: cut search and ceremony, not
confirmation of irreversible moves. Speed should come from reversibility and
parallelism, never from pretending you've confirmed something you haven't.

## 5. Domain adaptations

The cycle generalizes well beyond its origin; "Finish" = achieve the effect.

- **Cybersecurity (threat hunting / incident response):** the best-documented
  civilian use. Find = hypothesis-driven lead; Fix = corroborate across
  logs/EDR/network; Finish = contain/eradicate and verify it stopped; EAD = turn
  artifacts into indicators and detections and share them. Practitioner curricula
  (e.g., FIRST's CTI materials) treat F3EAD as a standard intelligence cycle and
  distinguish "rigid" (fixed requirements, fail fast) from "flexible" (revise
  mid-cycle) runs.
- **Sales / deal execution:** Find = the specific account/decision-maker/trigger;
  Fix = confirm budget/authority/need and the buying window; Finish = decisive
  close motion; EAD = log why it won/lost into the playbook.
- **Operations / project delivery:** Find = the actual constraint; Fix = confirm
  it's the real bottleneck (not a symptom); Finish = the intervention; EAD =
  post-mortem and standardize the fix.
- **Software debugging:** Find the bug, Fix = reproduce and confirm root cause
  (don't patch on a guess), Finish = deploy and verify, EAD = regression test +
  write-up.
- **Intelligence/analysis:** the native domain - Find a question, Fix the evidence,
  Finish a judgment/product, EAD to refine collection and brief stakeholders.

Caution when porting: practitioners often use "Fix" loosely to mean "understand the
problem." Keep the stronger meaning - *confirm to a standard sufficient to act* -
or you lose the discipline that makes the cycle safe at speed.

## 6. Sources

(Public doctrine and commentary on decision/execution method; nothing operational
about causing harm.)

1. Faint & Harris, "F3EAD: Ops/Intel Fusion 'Feeds' the SOF Targeting Process,"
   Small Wars Journal, 2012. (Argues exploitation/analysis - the "EAD" - is the
   cycle's main effort, and that "finish" is frequently non-kinetic.)
2. Gomez, "The Targeting Process: D3A and F3EAD," Small Wars Journal, 2011.
   (The widely-cited framing: D3A is the planning tool, F3EAD the execution tool
   for short-suspense targets.)
3. U.S. Army FM 3-60, *Army Targeting* (current edition) - F3EAD as an alternate
   methodology; D3A as the deliberate method. (Confirm the current edition/date
   directly; doctrinal publications are revised periodically.)
4. Joint Publication 3-60, *Joint Targeting* - F2T2EA dynamic-targeting kill chain.
5. Benitez, "It's About Time: The Pressing Need to Evolve the Kill Chain," War on
   the Rocks, 2017 - https://warontherocks.com/2017/05/its-about-time-the-pressing-need-to-evolve-the-kill-chain/
6. FIRST, Cyber Threat Intelligence SIG Curriculum (F3EAD for cyber) -
   https://www.first.org/global/sigs/cti/curriculum/
7. On the OODA relationship and tempo, see the companion `ooda-decision-loop`
   skill's `references/theory-and-sources.md` (Boyd: operating inside the
   adversary's decision cycle).

(Sources gathered May 2026. Exact URLs for doctrinal PDFs change; the documents
themselves - FM 3-60, JP 3-60 - are the durable references.)
