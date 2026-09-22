# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## 1. Retrieved chunks contain the answer

For at least 4 of my 5 test questions, the retrieved chunks include one that
contains the answer.

**Why this target:**
The five questions use facts stated directly in five different guides, so a
useful retrieval system should find the evidence for most of them. I allow one
miss because fixed-size chunks can split a question's wording from its answer.

---

## 2. Every answer names a source

Every answer the system produces names at least one source document.

**Why this target:**
The retrieval results retain each chunk's source filename, so attribution does
not depend on the model guessing where a fact came from. Missing it on any
answer would make that answer hard to verify.

---

## 3. The relevance gate stops out-of-corpus questions

When I ask a question my documents clearly don't cover, the relevance gate
stops it and the system returns "I don't have enough information about that" —
in at least 4 of 5 tries.

<!-- The five questions are the ones in `OUT_OF_SCOPE` at the bottom of
     `questions.py`, and `run_eval.py` puts them through the gate and writes
     what happened into your run log. Swap them for your own if you'd rather —
     just keep five of them, or the "4 of 5" above has nothing to be 4 of. -->

**Why this target:**
The five out-of-scope questions concern unrelated topics, so their closest
matches should be much weaker than guides about this region. I allow one error
until the distance measurements in Milestone 4 show where the two groups fall.

---

## 4. Something about your chunks

For the first chunk produced from each of `guide_givens_mill.md`,
`guide_eating.md`, `guide_accessibility.md`, `guide_seasons.md`, and
`guide_walking.md`, at least 4 of 5 end after a complete sentence rather than
in the middle of one.

**Why this target:**
The guides use sentences to state practical facts such as times, distances, and
restrictions. A chunk that ends mid-sentence can separate a fact from its
qualifier, so I would be disappointed if this happened in more than one of five
different guide types.



---

## 5. Your choice

In one `run_eval.py` evaluation run, answers to at least 4 of the 5 test
questions contain that question's `expects` phrase, ignoring capitalization.

**Why this target:**
Each expected phrase is a factual detail written in the corpus, not a subjective
recommendation. Requiring four matches tests whether the final answer preserves
the key detail retrieved from the guides while leaving room for one generation
or retrieval failure.



---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 2 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 1. Retrieved chunks contain the answer

         For at least 4 of my 5 test questions, the retrieved chunks include
         one that contains the answer.

         **Why this target:** ...

         > **Revised in unit 2:** For at least 4 of 5 questions, the top three
         > results contain the answer.
         >
         > **Why revised:** I couldn't judge "the chunks include one that
         > contains the answer" the same way twice — I scored two questions
         > differently on Monday than on Wednesday. The new version is
         > something I can actually check.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said 4 of 5 but got 2 of 5, so 2 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.

     The whole reason the originals stay visible is so someone can see what you
     said before you knew the answer.
     ───────────────────────────────────────────────────────────────────────── -->
