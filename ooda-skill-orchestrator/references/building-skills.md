# Building & Retaining Skills

How to turn a real capability gap into a durable, valuable skill - and how to
avoid the opposite failure of cluttering the library with overfit, single-use
"skills" that make future selection worse.

## The build-vs-one-off bar

Building a skill has a cost: it's effort now, and every skill that exists slightly
degrades selection accuracy for all the others. So build only when the payoff
amortizes. All four must hold:

1. **Recurrence** - the task will recur. A one-time need is solved one-off. (Tool/
   skill creation pays off precisely when the sub-problem repeats and the up-front
   cost is amortized over many later, cheap reuses.)
2. **Generalization** - the solution holds across different inputs, not just
   today's specific values, names, or dates. If it only works for this instance,
   it's a one-off in disguise.
3. **Verifiability** - you can say how you'd know it works: a test, a check, or a
   precise output spec. Skills that can be self-verified are the ones safe to keep
   and reuse; unverifiable ones rot silently.
4. **Clean interface** - well-defined inputs/outputs and a crisp, *distinctive*
   description. The description is the single biggest determinant of whether the
   skill gets correctly selected later, so it must clearly say what the skill is
   for and when to use it, without overlapping existing skills.

If any fails: solve it one-off this time. If a close-but-weak skill exists:
**enhance it** rather than create a near-duplicate. Duplicates are not redundancy;
they are selection noise.

## The research requirement (why this matters)

A skill worth retaining must encode something insightful and non-obvious - real
procedure, heuristics, and decision aids - not a thin restatement of what any model
already does by default. Before authoring:

- Research credible sources for the genuinely useful method (the standard practice,
  the expert heuristics, the common failure modes, the decision rules).
- Capture what's *non-obvious*: the steps people get wrong, the trade-offs, the
  edge cases.
- **Cite** it, and be honest about confidence. If you can't find solid grounding,
  say so and reconsider whether the skill should exist - a shallow skill is worse
  than no skill, because it will be selected and then disappoint.

Note: human-authored skills and agent-authored skills can each be valuable, and
each can misfire (a human's mental model may not match how the model actually
works; an agent may overfit to one example). The safeguard for either is the same:
verify against real tasks before retaining.

## Author with skill-creator, then verify

Use the `skill-creator` skill to do the authoring properly:

- A strong `description` (what it does AND when to trigger; a little "pushy" to
  combat under-triggering; no angle brackets; under the length limit).
- A lean SKILL.md (ideally under ~500 lines) with progressive disclosure - push
  depth into `references/` and bundle deterministic work into `scripts/`.
- Explain the *why* behind instructions instead of barking rigid MUSTs; today's
  models follow reasoning better than rules.
- Include a verification step.

Then **verify before retaining**: run its script, dry-run its procedure on a real
case, or have a fresh reviewer (a subagent) check accuracy and triggering. Only
add it to the library once it passes.

## Retain it

Package the skill (skill-creator's packager produces an installable `.skill`
file), save it to wherever the user keeps their skills, and tell them where it is
and what it triggers on. A retained skill should leave the user's toolkit
measurably stronger for next time - that is the whole point of the orchestrator.

## Sources

These are the well-established works behind this skill's approach. (Several very
recent papers on tool hallucination and skill self-evolution exist but were not
independently verified here; the principles below stand on the canonical sources.)

1. Sumers, Yao, Narasimhan, Griffiths, "Cognitive Architectures for Language
   Agents (CoALA)," 2023/2024 - https://arxiv.org/abs/2309.02427 (separating the
   action space / procedural memory from planning; agents err when they act on
   capabilities not actually in the verified action space).
2. Wang et al., "Voyager: An Open-Ended Embodied Agent with Large Language
   Models," 2023 - https://arxiv.org/abs/2305.16291 (the skill-library pattern:
   store reusable, self-verified skills; compose them later).
3. Cai et al., "Large Language Models as Tool Makers (LATM)," 2023 -
   https://arxiv.org/abs/2305.17126 (build a tool when the sub-problem recurs;
   amortize creation cost over cheap reuse).
4. Qian et al., "CREATOR: Tool Creation for Disentangling Abstract and Concrete
   Reasoning," 2023 - https://arxiv.org/abs/2305.14318 (separate designing a tool
   from using it).
5. Schick et al., "Toolformer: Language Models Can Teach Themselves to Use Tools,"
   2023 - https://arxiv.org/abs/2302.04761.
6. Shinn et al., "Reflexion: Language Agents with Verbal Reinforcement Learning,"
   2023 - https://arxiv.org/abs/2303.11366 (self-critique and re-entry when stuck).
7. "Agents Thinking Fast and Slow: A Talker-Reasoner Architecture," 2024 -
   https://arxiv.org/abs/2410.08328 (dual-process split: fast routine responses vs.
   slow deliberate reasoning - basis for this skill's fast mode).

General principle drawn from the tool-use literature and worth stating plainly:
selection accuracy degrades as the number of available tools grows, and tool
*descriptions* (not just relevance) strongly shape which tool gets picked - so
favor few, well-described, non-overlapping skills.
