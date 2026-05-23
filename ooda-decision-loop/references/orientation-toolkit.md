# Orientation Toolkit

The Orient phase is where decisions are won or lost, so it deserves real tools.
Each tool below counters a specific way orientation goes wrong. You don't need all
of them every time — pick the ones that fit the failure mode you're most worried
about. A good default for a high-stakes call: competing hypotheses + premortem +
"most dangerous assumption."

## Contents
1. Surfacing your current orientation
2. Analysis of Competing Hypotheses (ACH)
3. The premortem
4. Red-teaming and modeling the opponent's orientation
5. Bayesian updating and avoiding incestuous amplification
6. Destruction and creation (rebuilding a stuck model)
7. The Cynefin situation-match (which loop to run)
8. Quick orientation audit (checklist)

---

## 1. Surfacing your current orientation

You cannot inspect a model you can't see. Before analyzing, write one sentence:
"My current read is that ___, which assumes ___." Boyd's insight is that this read
is silently shaped by five things, each a possible source of error:

- **Inherited instincts / temperament** — e.g. loss aversion, status-quo bias.
- **Culture and incentives** — what your org rewards, what "people like us" do.
- **Prior experience** — pattern-matching to the last similar situation, which may
  not actually be similar.
- **The new information at hand** — which may be partial, stale, or cherry-picked.
- **Your analysis and synthesis** — the reasoning you layer on top.

For each, ask: *is this helping me see, or making me see what I expect?* The act
of attribution ("I'm reading it this way because the last outage was a deploy, so
I assume this one is too") is what makes the bias available to challenge.

## 2. Analysis of Competing Hypotheses (ACH)

The single highest-leverage debiasing move, because it attacks confirmation bias
structurally.

1. Brainstorm **3+ genuinely different** explanations/courses of action. The bar:
   each should be defensible by a smart person — no strawmen.
2. List the key pieces of evidence and the major assumptions.
3. For each evidence item, mark which hypotheses it's *consistent* with. Crucially,
   look for evidence that is **inconsistent** with a hypothesis — disconfirmation
   is far more diagnostic than confirmation.
4. The strongest hypothesis is the one with the *fewest* inconsistencies, not the
   most supporting points (lots of evidence is consistent with several stories).
5. Identify the **one observation or test** that would most cleanly separate the
   top two hypotheses. That's usually your next action.

Anti-pattern: generating one real hypothesis plus decoys. If two of your three
hypotheses feel obviously dumb, you haven't done ACH — you've rationalized.

## 3. The premortem

Prospective hindsight. Imagine the decision has already failed, then explain why.

- "It is [date a few months out]. This decision failed badly. Write the story of
  how." Spend 5–10 minutes generating concrete failure causes.
- Then, for the top 2–3 causes, ask: can we cheaply detect this early, or design
  the move to be robust to it?
- Premortems work because they give people permission to voice doubts that
  optimism and group consensus suppress. They consistently surface risks that
  go-forward planning misses.

## 4. Red-teaming and modeling the opponent's orientation

- **Self red-team:** "If I wanted to tear this plan apart, where would I strike
  first?" Attack your own strongest assumption.
- **Opponent modeling (if there's an adversary/competitor):** build *their* OODA
  loop. What do they observe? What's their orientation — their incentives,
  constraints, blind spots, recent commitments they're anchored to? What will they
  predict you'll do? Their orientation is something you can exploit (see
  `tempo-and-competition.md`).
- Beware **mirror-imaging**: assuming the opponent values what you value and will
  do what you'd do. Most intelligence failures are mirror-imaging failures.

## 5. Bayesian updating and avoiding incestuous amplification

- Treat each new fact as evidence that should *move* your confidence, not as a
  trophy for the view you already hold. Ask: "How surprised am I by this? Which
  hypothesis predicted it best?"
- The named failure: **incestuous amplification** — a closed conversation where
  people only circulate confirming information, and confidence rises while
  accuracy doesn't. Counter it by deliberately seeking the best disconfirming
  evidence and by giving a dissenter explicit air cover.
- Practical tic: keep a short list of "things that would change my mind." If
  nothing could, you're not oriented — you're committed.

## 6. Destruction and creation (rebuilding a stuck model)

Boyd's epistemology (from his 1976 essay "Destruction and Creation"): any mental
model, left to refine itself internally, drifts out of match with reality. The fix
is a deliberate teardown-and-rebuild:

1. **Destruction (analysis):** break the situation into its constituent parts.
   Question each part on its own. Discard the frame that's holding them together.
2. **Creation (synthesis):** recombine the parts into a *new* whole — ideally
   importing structure from an unrelated domain. (Boyd's illustration: combine
   skis, an outboard motor, a bicycle chain, and tank treads → a snowmobile.
   None of the source domains "owns" the answer.)
3. Ask: "What's an analogy from a completely different field?" and "If I were
   inventing this from scratch today, knowing what I know, would I build it this
   way?"

Use this when you're stuck, when everyone agrees too easily, or when the obvious
options all feel bad — those are signs the *frame*, not the options, is the
problem.

## 7. The Cynefin situation-match (which loop to run)

Match your decision style to the kind of situation you're in (Dave Snowden's
Cynefin). Using the wrong style is a common, expensive error.

| Domain | Cause/effect | Right move | OODA flavor |
|---|---|---|---|
| **Clear** | Obvious, known | Apply best practice | Barely any loop — just act |
| **Complicated** | Knowable with analysis/expertise | Analyze, get experts, then act | Deliberate Orient, explicit Decide |
| **Complex** | Only clear in hindsight | Run small safe-to-fail probes; amplify what works | **Multiple parallel loops** — probe, sense, respond; don't over-plan |
| **Chaotic** | No discernible cause/effect | Act now to establish stability, then re-orient | Act → Observe first; impose order before analyzing |
| **Confused/Aporetic** | You don't know which domain | Break the problem into parts and place each | Orient on "where am I?" first |

(The fifth row — *Confused/Aporetic* — is Snowden's post-2020 rename of the older
"Disorder" domain: the state of not yet knowing which domain you're in. If you've
only seen the classic four-domain Cynefin, this is the same idea.)

Two cautions: (1) In **complex** domains, don't run one big loop — run several
small experiments at once and let a higher-level loop learn across them. (2) The
dangerous transition is **Clear → Chaotic**: complacency ("we've got this") makes
you stop observing, and you fall off a cliff you didn't see.

## 8. Quick orientation audit (checklist)

For a fast pass when you don't have time for the full toolkit, ask:

- What's my one-sentence read, and what does it assume?
- What are two other explanations a smart person would give?
- What's the most dangerous thing I could be wrong about?
- What's the cheapest observation that would change my mind, and have I gone to
  get it?
- Am I reacting to the situation as it is now, or as it was when I formed this view?
- (If competitive) what does the other side believe, and where are they slow or wrong?
