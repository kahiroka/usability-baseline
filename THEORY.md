# Usability Baseline — A Systemized UX/UI Theory (v1.1, peer-reviewed)

A systemization of [entry-to-usability-baseline.html](entry-to-usability-baseline.html),
revised after peer review. The cheatsheet states the ideas; this document
organizes them into a coherent system: core model → layers → mechanisms →
derived principles → design procedure. Claims added or strengthened in review
are marked **[rev]** and justified in §9 (Provenance & Changelog).

---

## 1. Core Model

**Axiom.** Usability is not a property of a product in isolation. It arises in
the *relationship* between three elements:

```
        [ Value ] ──── Delivery ────▶ [ Subject ]
           UX              UI          Accessibility

        └──────────── within a Context ────────────┘   [rev]
```

| Element  | Common name             | Question it answers        | Overall challenge            |
|----------|-------------------------|----------------------------|------------------------------|
| Value    | User Experience (UX)    | *What* does the product provide? | Maximize the value      |
| Delivery | User Interface (UI)     | *How* is the value conveyed?     | Deliver it efficiently  |
| Subject  | Accessibility           | *Who* receives the value?        | Define (and widen) the subject |
| Context **[rev]** | Context of use | *Where/when/under what conditions?* | Hold up across contexts |

**Definition (Usability).** Usability is the delivery of the product's value
to the subject, in context, **without loss and without delay**.

**Refinement (value is relational). [rev]** Value is not a fixed payload that
exists before delivery; it is *realized at the subject*. The same product has
different value for different subjects in different contexts — the theory
itself already implies this in §4, where an unconsidered color scheme
"diminishes the value for specific people." So value must be written
`value = f(product, subject, context)`, not `value = f(product)`. This is why
the order of operations below is not optional.

**Corollary (order of operations).** Delivery cannot be designed first.
The correct sequence is:

1. Recognize what the **value** is — *for whom, and where* **[rev]**.
2. Recognize who the **subject** is, and in what **context** they will use
   the product **[rev]**.
3. Only then design the **delivery**.

The rest of the theory elaborates each element: the Delivery layer (§2), the
Value layer (§3), and the Subject layer (§4), with Human-Centered Design (§5)
as the governing discipline, and an optional formalization (§6).

---

## 2. The Delivery Layer (UI)

The UI has two roles, and each role has its own key mechanism:

| UI role | Mechanism | Failure mode it prevents |
|---------|-----------|--------------------------|
| Deliver value without loss and delay | **Usability costs** (minimize lifetime total) | Loss — value never reaches the subject |
| Control the subject's immersion behind the scenes | **Immersion** (protect, spend deliberately) | Disturbance — value reaches the subject interrupted |

### 2.1 The Four Usability Costs

Costs are obstacles between the subject and the value. They factor along two
independent axes, giving a 2×2 taxonomy:

|              | **Learning Cost** (amortizable) | **Operating Cost** (recurring) |
|--------------|---------------------------------------------|----------------------------------------------|
| **Physical** | **PLC** — e.g., placement of physical buttons is hard to understand | **POC** — e.g., response delay makes every operation slow |
| **Logical**  | **LLC** — e.g., menu hierarchy is disorganized, items are hard to find | **LOC** — e.g., the same unnecessary steps are required every time |

The two axes have different characters:

- **Learning costs** (PLC, LLC) are paid once (or a few times) and then
  *amortized* — the subject eventually learns. They tax first contact and
  adoption.
- **Operating costs** (POC, LOC) are paid again on every use. Learning cannot
  amortize them away. They tax the entire lifetime of the product.

**Refinement (recurring, not unavoidable). [rev]** v1.0 called operating
costs "operationally unavoidable," but its own LOC example — "the same
*unnecessary* steps every time" — is avoidable by redesign. The correct
distinction is: learning costs can be amortized *by the subject*, operating
costs can only be reduced *by the designer*. All four costs are design
targets; none is a fact of nature.

**Refinement (lifetime cost, and the trade between axes). [rev]** "Minimize
all four" is under-specified because learning and operating costs often trade
against each other (an expert shortcut raises LLC but lowers LOC). The
decision rule is expected lifetime cost:

```
Total ≈ Learning + Operating × n        (n = expected number of uses)
```

- High-frequency tools (n large): accept higher learning cost to buy lower
  operating cost — expert interfaces, shortcuts, command languages.
- One-shot interfaces (n ≈ 1): minimize learning cost above all — kiosks,
  onboarding, checkout flows.

**Scope note (both directions of the loop). [rev]** Costs arise not only when
the subject acts on the product (execution) but also when the subject reads
the product's state and feedback (evaluation) — cf. Norman's two gulfs. An
unreadable status display is as much an LLC/LOC as a buried menu item. Error
costs (making, detecting, and recovering from errors) are recurring operating
costs and belong in the same ledger.

**Rule.** Minimize expected lifetime cost — but you may not have to bear all
four costs yourself. Two standard cost-transfer strategies:

1. **Delegate physical costs to the platform.** For mobile apps, PLC and POC
   are largely passed on to the device manufacturer.
2. **Delegate learning costs to conventions.** Following the UI guidelines of
   the application framework reduces PLC and LLC, because shared rules mean
   the subject does not have to relearn across applications.

### 2.2 Immersion

**Definition.** Immersion is the state in which the subject can enjoy the
value without any disturbance. (This is the interface-level counterpart of
*flow* in psychology. **[rev]**)

The term comes from VR but applies equally to classical UI. Immersion could be
folded into the two operating costs, but it is treated as a separate mechanism
because it concerns *continuity of experience*, not effort.

- **General rule (revised):** never take focus away from the subject *for
  free*. **[rev]** v1.0's absolute rule ("do not take any focus away") fails
  for safety alerts, destructive-action confirmations, and errors, where
  interrupting is the correct design. The workable form is an **interruption
  budget**: the disruption imposed must be proportional to the urgency and
  importance of what it delivers. Zero-urgency messages get zero focus
  (ambient/deferred); only genuine emergencies may seize it.
- **The UI's second role:** carefully control the subject's immersion *behind
  the scenes* — the subject should never notice the control.
- **Example, with its price stated. [rev]** A smooth animation prompts the
  subject to act without interfering with immersion. Note the mechanism:
  animation does not remove delay — it *adds* a small POC and buys continuity
  with it. The trade is only worth it if the animation is fast and
  interruptible; a slow, blocking animation spends operating cost *and*
  immersion at once.

---

## 3. The Value Layer (UX)

### 3.1 Functionality as the Foundation

**Axiom.** Functionality is the foundation of usability. A product must
function as claimed; no amount of delivery polish compensates for a product
that does not.

### 3.2 The Formatives–Functionality Frontier

Formative beauty (how it looks) and functional beauty (how it works) can
trade against each other — but only at the frontier:

```
 Formatives
     ▲
     │ ●
     │   ╲          ↗  push the frontier itself
     │     ● ──╮
     │    ○     ╰──●───     ○ = interior point: improve BOTH, no trade-off
     └────────────────▶ Functionality
```

- **Refinement (the trade-off is a frontier property). [rev]** v1.0's "if you
  prioritize formative beauty ... functional beauty will decrease" holds only
  *on* the Pareto frontier. Most real designs sit in the interior, where both
  can be improved at once — which is exactly the original text's own closing
  challenge ("aim for more beauty and more functionality"). State it as one
  rule: **first push toward the frontier (no trade-off exists there), and only
  on the frontier choose a point.**
- **Refinement (the axes are coupled). [rev]** Formatives and functionality
  are not fully independent: the *aesthetic–usability effect* (Kurosu &
  Kashimura 1995; Tractinsky et al. 2000) shows aesthetically pleasing
  interfaces are perceived as easier to use and buy tolerance for minor
  friction. Formative beauty therefore feeds back into delivered value rather
  than only competing with it — one more reason the pure trade-off picture
  only holds at the frontier.
- Example of a genuine frontier trade: sharp edges look cool but do not feel
  good to hold.
- **Choosing a point** on the frontier is the designer's (or the subject's)
  legitimate choice — there is no universally correct point.
- **Constraint:** manufacturing cost bounds how far the frontier can move.

---

## 4. The Subject Layer (Accessibility)

**Definition.** Accessibility is, in a nutshell, *who you provide value to*.

- The subject is diverse: children, the elderly, the injured, the disabled.
- An accessibility failure is a **value failure for specific people** — e.g.,
  an unconsidered color scheme diminishes the product's value for subjects
  with color-vision differences. The product did not get worse in general;
  it got worse *for them*.
- **Refinement (accessibility includes situations). [rev]** Impairment is
  often situational, not personal: one-handed use while carrying a child,
  sunlight glare, a noisy train. This ties the Subject axis to the Context
  element of §1 — the same subject moves in and out of the "edge" population
  as context changes, so accessibility work is not for a fixed minority.
- **Refinement (the curb-cut effect). [rev]** Designing for edge subjects
  routinely improves the product for everyone (curb cuts, captions, high
  contrast). Accessibility is therefore not only a widening of the subject
  but one of the most reliable ways to *push the frontier* of §3.2 — it
  raises functionality without a formative price.
- **Challenge:** create something easy to use for all people, knowing this is
  genuinely hard.

This is why "define the subject" is part of the core model (§1): every
delivery decision implicitly includes or excludes people.

---

## 5. Human-Centered Design (HCD)

**Principle.** Design for the human's convenience, not the implementation's.

**Test.** If implementation convenience is exposed to the outside, it is not
HCD.

**Diagnostic example.** "You must disable function A to enable function B."
When the subject must manage the machine's internal constraints, the function
model is leaking.

**Remedy (revised). [rev]** v1.0 prescribed "more abstraction," but
abstraction is not monotonically good: over-abstraction hides system state
and produces mode errors and surprise — violating visibility of system
state. The refined remedy has two branches:

1. If the constraint **can** be absorbed, abstract it away — but shape the
   abstraction after the *subject's mental model* of the function, not after
   a tidier version of the implementation.
2. If the constraint **cannot** be absorbed (physics, safety, cost), do not
   hide it — *translate* it: expose it in the subject's terms, at the moment
   it matters, with the reason. An honest visible constraint costs less than
   an invisible one that strikes unpredictably.

HCD is the discipline that keeps the whole system honest: costs (§2.1) are
measured from the subject's side, immersion (§2.2) is protected for the
subject's sake, and the frontier point (§3.2) may even be the subject's
choice.

---

## 6. Formalization: Delivery as a System Response [rev]

The original cheatsheet's own figure draws delivery as a *damped step
response* — a control-systems metaphor the text never cashes out. Doing so
unifies the theory's three failure words:

| Control term | Theory term | Meaning for the subject |
|---|---|---|
| Steady-state error | **Loss** | Some value never arrives (§1 definition) |
| Rise time / lag | **Delay** | Value arrives late (§2.1 operating costs) |
| Overshoot / ringing | **Disturbance** | Value arrives, but the experience oscillates — interruptions, jank, mode surprises (§2.2 immersion) |

Read this way, "without loss and delay" was always one clause short; the
figure supplies the third: **without loss, delay, or disturbance**. A UI is a
channel whose step response should converge quickly, settle cleanly, and
track the subject's intent with zero steady-state error.

---

## 7. Derived Principles (Summary)

1. **Relational usability.** Usability = value delivered to the subject, in
   context, without loss, delay, or disturbance; it exists only in the
   Value–Delivery–Subject–Context relationship.
2. **Value and subject before delivery.** Never design the UI before knowing
   what is delivered, to whom, and in what context.
3. **Minimize expected lifetime cost** across the four costs (PLC, POC, LLC,
   LOC): `Learning + Operating × n`. Trade learning against operating
   according to usage frequency; count evaluation and error costs in the
   same ledger.
4. **Transfer costs where possible** — physical costs to the platform,
   learning costs to shared conventions.
5. **Spend focus, never leak it.** Interruptions must pay for themselves in
   urgency; guide invisibly (fast, interruptible animation) when urgency is
   low.
6. **Function as claimed.** Functionality is the foundation; nothing above it
   stands without it.
7. **Frontier first, point second.** In the interior, improve formatives and
   functionality together (they even reinforce each other via the
   aesthetic–usability effect); only on the frontier is choosing a point
   legitimate.
8. **Accessibility is value — and a frontier-pusher.** A product inaccessible
   to someone has less value for them; designing for the edges (including
   situational impairment) reliably improves the middle.
9. **Absorb or translate, never leak.** Abstract implementation constraints
   into the subject's mental model where possible; where impossible, expose
   them honestly in the subject's terms.

---

## 8. Design Procedure & Checklist

A working procedure that follows from §1–§6:

1. **Value** — State what value the product provides, *for whom and where*.
   Does it function as claimed?
2. **Subject & context** — State who the subject is and the contexts of use.
   Who is implicitly excluded — permanently (children, elderly, injured,
   disabled) or situationally (one-handed, glare, noise)? Do color schemes
   and similar choices diminish value for specific people?
3. **Delivery — costs** — For each interaction, estimate the four costs and
   the expected use count *n*:
   - PLC: is the physical layout understandable?
   - POC: is response delay minimal?
   - LLC: is the logical hierarchy organized? Is system state readable?
   - LOC: are there unnecessary recurring steps? What do errors cost to
     detect and undo?
   Given *n*, is the learning/operating trade set correctly? Which costs can
   be delegated to the platform or to framework guidelines?
4. **Delivery — immersion** — Does anything take focus without paying for it
   in urgency? Are prompts delivered invisibly (fast, interruptible
   animation) rather than disruptively? Does the interaction settle cleanly
   (no overshoot — §6)?
5. **Trade-off** — Is the design at the formatives–functionality frontier
   yet? If not, improve both; if so, is the chosen point deliberate? Can the
   frontier be pushed within manufacturing cost — e.g., via accessibility
   work?
6. **HCD test** — Is any implementation convenience exposed to the subject?
   If yes: absorb it behind an abstraction shaped by the subject's mental
   model, or translate it into the subject's terms — then repeat.

---

## 9. Provenance & Changelog

Base claims originate from *"Entry to Usability Baseline"* © @kahiroka.
Sections marked **[rev]** were added or corrected in the v1.1 peer review:

| # | Change | Reason |
|---|--------|--------|
| 1 | Added **Context** to the core model | The original triad omits context of use; the same product/subject pair has different usability in different contexts (cf. ISO 9241-11, which defines usability relative to "specified context of use"). |
| 2 | Made **value relational** (realized at the subject) | Internal consistency: §4's claim that value "diminishes for specific people" contradicts a fixed-payload view of value. |
| 3 | Operating costs reframed **recurring**, not "unavoidable" | The original's own LOC example ("*unnecessary* steps") is avoidable by design; the true asymmetry is amortizable-by-subject vs. reducible-only-by-designer. |
| 4 | Added **lifetime-cost rule** (`Learning + Operating × n`) | "Minimize all four" is under-specified when the axes trade against each other (expert shortcuts, kiosks). |
| 5 | Added **evaluation and error costs** to the cost scope | The original counts only execution-side costs; reading state/feedback and recovering from errors are costs too (cf. Norman's gulf of evaluation). |
| 6 | Immersion rule relaxed to an **interruption budget** | The absolute "do not take any focus away" forbids safety alerts and destructive-action confirmations, which are correct interruptions. |
| 7 | Animation example restated as a **cost-for-continuity trade** | Animations add delay rather than removing it; the claim "ensures delivery without delay" was literally false, though the design advice was right. |
| 8 | Trade-off restricted to the **Pareto frontier**; axes noted as coupled | Interior points allow improving both (the original's own closing challenge); the aesthetic–usability effect (Kurosu & Kashimura 1995; Tractinsky et al. 2000) shows formatives also feed value. |
| 9 | Accessibility extended with **situational impairment** and the **curb-cut effect** | Strengthens the section from a compliance framing to a frontier-pushing strategy, and links it to Context. |
| 10 | HCD remedy split into **absorb or translate** | "More abstraction" alone can hide state and cause mode errors; constraints that cannot be absorbed should be exposed honestly in the subject's terms. |
| 11 | Added §6 **system-response formalization** | Makes the original figure's damped step response do theoretical work: loss = steady-state error, delay = rise time, disturbance = overshoot; completes the definition to "without loss, delay, or disturbance." |
