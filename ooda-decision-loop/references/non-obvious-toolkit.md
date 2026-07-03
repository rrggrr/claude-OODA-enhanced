# The Non-Obvious Battery

Seven probes for the Orient phase. The core toolkit (competing hypotheses,
premortem, red team, steelman) converges on the *truest* story. This battery
diverges on purpose: it hunts the findings that are true, consequential, and
absent from everyone's first read. Obvious findings are table stakes - anyone
running the loop finds them. Mismatch (Boyd's actual win condition) comes from
orienting on what the other side's model doesn't contain.

## How to run it

1. **One line per probe, fast.** Ask each question against the current
   situation and write a single line. Most lines will be "nothing here" - that
   is fine and takes seconds.
2. **Chase only what snags.** A probe "snags" when the one-liner surprises you,
   contradicts the leading story, or names something you can't answer. Promote
   snags to real checks in the same Observe batch.
3. **Rank findings by impact times confidence.** A 70%-confident finding that
   changes the decision beats a 99%-confident finding that decorates it. Report
   in that order; never in discovery order.
4. **Close with the contradiction test.** Orient is not done until at least one
   finding contradicts or complicates the initial framing. If the full battery
   produced none, say so explicitly - a genuinely clean battery raises
   confidence in the obvious read, which is itself a result.

## The seven probes

### 1. Negative space - the dog that didn't bark

**Ask:** if the leading story were true, what else would have to be visible?
List 2-3 predicted signals, then check for them. The absence of an expected
signal is evidence against the story that predicts it.

*Example:* "Sales says we're losing on price" predicts price objections in the
lost-deal notes. The notes never mention price. The story just lost its main
witness.

**Where it hides:** complaints never filed, errors that should have fired but
didn't, stakeholders who went quiet, metrics that should have moved and didn't,
questions nobody in the room is asking.

### 2. Outside view - the base rate

**Ask:** strip the specifics. Of all situations in this reference class, what
usually happens, and what usually causes it? Anchor there first; adjust for
specifics second.

*Example:* most "sudden quality collapse" incidents at a vendor trace to a
personnel or ownership change, not to the product. Check who left before
checking the product.

**Trap it defuses:** the inside view - reasoning only from this case's vivid
details, which the incumbent story has already curated.

### 3. Inversion - argue the opposite from evidence

**Ask:** assume the favored conclusion is flat wrong. What evidence would you
now *expect* to exist, and where would it be? Then look there. This is
different from red-teaming: red-team attacks your argument; inversion tells you
where to point the sensors.

*Example:* favored conclusion is "the migration caused the outage." Inverted:
if it didn't, there should be an unrelated change in the same window - go read
the full change log, not just the migration ticket.

### 4. Second-order - who reacts, what breaks next

**Ask:** play the obvious move forward one step. Who responds, adapts, retreats,
or exploits it? What load shifts onto what?

*Example:* the price cut is easy for the competitor to match in a week (bad
transient), and it re-anchors every future negotiation down (self-inflicted
second-order cost). The move that looked decisive is a donation.

**Rule of thumb:** any move that is easy for the other side to copy or cancel
is a first-order move; keep looking for the asymmetric one.

### 5. Incentive scan - cui bono

**Ask:** who benefits if the current story is believed? Whose data, summary, or
framing has a thumb on the scale - not from dishonesty, but from position?
Every observation arrived through someone with a stake.

*Example:* the manager blaming "market conditions" inherited the problem
accounts two months ago. The story may be true; the source is not neutral.
Weight accordingly and find one channel that bypasses the interested party.

### 6. Constraint flip - which wall is a door

**Ask:** list the constraints everyone treats as fixed. For each: physics, or a
past decision? Contract terms, budget lines, org boundaries, "we've always,"
and "the system can't" are usually decisions - and decisions can be revisited.

*Example:* "we can't inspect faster, we have two techs" - the constraint is
actually "inspections are free," which is a pricing choice. Charge for
inspections, credit against purchase, and the queue clears itself.

### 7. Timeline anomaly - the change that maps, and the one that should but doesn't

**Ask two questions.** (a) What changed just *before* the problem appeared?
Build the timeline of all changes, not just the ones in the current story.
(b) What changed that *should* have produced an effect but visibly didn't?
The second is negative space in time - a lever that turned out to be
disconnected tells you the causal model is wrong.

*Example:* the revenue drop starts the week the senior rep's accounts were
redistributed - two months before anyone framed it as a pricing problem. And
the ad-spend doubling in the same window moved nothing, so demand-gen isn't
the binding constraint either.

## Anti-patterns

- **Battery as ritual.** Running all seven and reporting seven paragraphs of
  nothing. One line each; expand only the snags.
- **Non-obvious as contrarian.** The goal is findings that are non-obvious
  *and true and consequential* - not a hot take. Every battery finding still
  needs evidence and a falsifier before it drives a Decide.
- **Burying the lead.** If probe 7 found the real cause, it goes first in the
  output, ranked above the obvious findings - impact order, always.
- **Skipping it under time pressure.** In fast mode, run probes 1, 5, and 7
  only (negative space, incentives, timeline) - they are the cheapest per
  insight. Cutting all seven is how fast mode finds only what everyone else
  already found.

## When to skip the battery

Skip it when the situation is *clear* (known answer, execution only) or when
the loop is a pure computation. If the situation earned the OODA loop at all,
it earns at least the three-probe fast pass.
