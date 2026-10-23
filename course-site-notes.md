# CS4510 course site notes (offline copy)

Source: https://cs4510.pages.ewi.tudelft.nl/ (2026/27). Fetched 2026-10-22 and summarised by a fetch tool, so this is not verbatim. The site went down on 2026-10-23.
Not captured: the actual specs of the "Two Loops" and "Compiler" WebLab assignments, the Coq Installation page, the Contact page, the Week 1 slides links.

## Home
- Deductive verification of functional and imperative programs with Coq/Rocq. Hoare Logic for imperative programs. Automation is not a focus.
- Weekly lectures follow the material; problem sessions with instructor and TA help. Pair programming encouraged.
- Material: Software Foundations (local versions). Each chapter has an HTML file (reading) and a `.v` file (exercises). VS Code with VsCoq recommended.
- Roadmap:
  1. Functional programming: Basics, Lists, Poly, Maps
  2. Specification and proofs of functional programs: Induction, Tactics, Logic, IndProp, Rel
  3. Imperative language implementation: Maps, Imp
  4. Specification and proofs of imperative programs: Hoare, Hoare2
- Evaluation: final grade from an individual Coq programming project; must score 5.8 or higher to pass. Weekly optional assignments do not count. No exam is mentioned.
- Each week's work plan lists exercises you are expected to be able to solve. Any other book exercise is optional (TAs may not be able to help; use peers and Mattermost).
- Help: Queue at queue.tudelft.nl/edition/1275 during problem sessions, or Mattermost (mattermost.tudelft.nl/cs4510-26-27-q1, sign up via invitation link on the site).

## Project
- Deadline: Friday 30 October 2026, 14:00 Delft time. Strict: failure to submit all deliverables fails the course.
- Submit on WebLab (2026-2027 CS4510 assignment page).
- Deliverables: (1) the "Two Loops" exercise, (2) all exercises of the "Compiler" assignment.
- Pass/fail. Must be correct (Rocq definitions and lemmas accurately model the problem) and complete (all lemmas proven, no `Admitted`, no `Axiom`).
- Collaboration: discuss with peers, but code must be your own. Plagiarism fails the project.
- AI: allowed to understand course material. Generating code with AI is not allowed and fails the project.

## Weekly plans
General rule each week: study the full chapter, including parts skipped in lectures, unless stated otherwise.

**Week 1.** Install Coq, join WebLab and Mattermost, read intro slides. Preface: ignore course-management info. Basics (Basics_short.v, basics.pdf). Problem session: `andb_true_elim2` (WebLab Basics).

**Week 2.**
- Induction (Induction_short.v, induction.pdf): all 1-star and 2-star exercises.
- Lists (Lists_short.v, lists.pdf): all 1-star and 2-star exercises.
- Poly (Poly_short.v, poly.pdf): all 1-star and 2-star exercises. The Church Numerals section is out of scope.
- Tactics (Tactics_short.v, tactics.pdf): self-study. Read everything, do the 1-star exercises, do not dwell on difficult parts.

**Week 3.** Logic (Logic_short.v, logic.pdf). Exercises: `and_assoc`, `contrapositive`, `de_morgan_not_or`, extra: `or_distributes_over_and`, `dist_exists_or`, `In_app_iff`, `logical_connectives` (both `andb_true_iff` and `orb_true_iff`).

**Week 4.**
- IndProp (IndProp_short.v, indprop.pdf). Focus: Inductively Defined Propositions, Using Evidence in Proofs, Exercising with Inductive Relations, Case Study: Improving Reflection. Exercises: `ev_sum`, `total_relation` (both parts), `empty_relation` (both parts), `reflect_iff`.
- Maps (Maps_short.v, maps.pdf). Focus: Total Maps. All exercises.
- WebLab: IndProp assignment 182509, Maps assignment 182525 (weblab.tudelft.nl/cs4510/2026-2027/assignment/<id>/info).

**Week 5.**
- Imp (Imp_short.v, imp.pdf). Define `optimize_0plus_b` and prove `optimize_0plus_b_sound` two ways: manually without automation, and with tacticals (short and elegant). Also `XtimesYinZ_spec`, `loop_never_stops`, `no_whiles_eqv`.
- Hoare (Hoare_short.v, hoare1.pdf). Read the whole chapter, especially the Rocq proofs of the Hoare logic proof rules. Read the Skip, Sequencing, Assignment subsections under Proof Rules. Exercises: `hoare_asgn_examples1`, `hoare_asgn_examples2`, `hoare_asgn_wrong`, `hoare_asgn_fwd`, `hoare_asgn_fwd_exists`.

**Week 6.** Work on the project.
- Hoare: same as Week 5 (step through the Rocq proofs of the proof rules).
- Hoare2 (hoare2.pdf, no short version). Read the whole chapter, especially the part on implementation in Rocq. Exercises: `if_minus_plus_reloaded`, `if_minus_plus_correct`, `div_mod_outer_triple_valid`, `slow_assignment`, `parity`, `sqrt`.
