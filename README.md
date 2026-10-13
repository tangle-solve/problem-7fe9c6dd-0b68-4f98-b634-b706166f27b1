<!-- solve-problem:7fe9c6dd-0b68-4f98-b634-b706166f27b1 -->
# Can quantum computers solve all NP problems efficiently?

A [Tangle Solve problem](https://solve.tangle.tools/problems/7fe9c6dd-0b68-4f98-b634-b706166f27b1).

## What is the problem?

The question is whether every problem in NP can be solved in bounded-error quantum polynomial time, i.e., whether NP ⊆ BQP. Formally: BQP is the class of languages decidable by a uniform family of polynomial-size quantum circuits with bounded error probability (≤ 1/3); NP is the class with polynomially-checkable witnesses. Since SAT is NP-complete, the question reduces exactly to: does there exist a polynomial-time quantum algorithm deciding SAT? Most researchers conjecture NP ⊄ BQP (in fact even PH ⊄ BQP is conjectured in some formulations), but no proof exists. Note an important subtlety: proving NP ⊄ BQP would require non-relativizing techniques, because oracle worlds exist relative to which NP ⊆ BQP (a random oracle makes Grover-type search quadratically faster, but relative to certain oracles NP-complete problems collapse into BQP; conversely relative to a random oracle NP ⊄ BQP holds with probability 1 — see Bennett et al.). So the problem is intrinsically about overcoming relativization barriers, and possibly algebraization barriers.

## Why does it matter?

This is the central question about the ultimate power of quantum computers for combinatorial optimization. An affirmative answer would revolutionize cryptography (breaking most deployed public-key and symmetric schemes beyond what Shor/Grover already do), optimization, and AI search. A negative answer would delineate the true limits of quantum speedups, guiding investment in quantum annealing and variational algorithms (QAOA, etc.), which implicitly promise heuristic NP-hard optimization gains. It also sits at the heart of complexity theory: it is a prerequisite-style question for the widely believed conjecture BQP ⊄ PH vs. PH ⊄ BQP landscape.

## What's already known?

- Grover's algorithm gives a quadratic speedup for unstructured (black-box) search: O(√2ⁿ) queries for SAT over n variables.
- Bennett, Bernstein, Brassard, Vazirani (1997) proved a matching Ω(√2ⁿ) quantum query lower bound for black-box search, showing quantum computers cannot get more than quadratic speedup for unstructured search. Crucially, this is a relativizing result: it says nothing definitive about NP vs. BQP in the unrelativized world.
- BBBV also constructed an oracle relative to which NP ⊄ BQP (essentially the random oracle), and oracles are known relative to which NP ⊆ BQP — so any proof must avoid relativization.
- Shor's factoring/discrete-log algorithms show specific problems (in NP ∩ coNP suspects) fall in BQP, but factoring is not believed NP-complete (unless PH collapses; verify).
- Aaronson–Kuperberg oracle separations involving QMA vs. PH, and "algebrization" (Aaronson–Wigderson 2009) show even non-relativizing arithmetization techniques face barriers here.
- No nontrivial unconditional lower bound against BQP for any NP problem is known; even proving explicit functions require superlinear quantum circuit size is open.

## What would count as solving it?

Either direction resolves it:

1. **Positive:** An explicit polynomial-time quantum algorithm (uniform circuit family) deciding SAT with error ≤ 1/3. This would prove NP ⊆ BQP.
2. **Negative:** A proof that SAT ∉ BQP (equivalently NP ⊄ BQP), by any technique — circuit lower bounds, a new barriers-surmounting proof system, or a reduction from a known-hard object. A referee would accept any rigorous, peer-reviewable proof; the key challenge is it must evade relativization and (likely) algebrization.
3. **Partial credit variants:** unconditional superquadratic or exponential quantum lower bounds for explicit NP problems in restricted models; or resolving BQP vs. PH.

## How to start

1. Read Bennett–Bernstein–Brassard–Vazirani (1997) carefully to internalize why black-box lower bounds don't transfer — the oracle construction is the crux of the barrier.
2. Read Aaronson–Wigderson "Algebrization: A New Barrier in Complexity Theory" (2009) to understand which proof techniques are ruled out.
3. Watrous's survey (arXiv:0804.3401, especially the sections on BQP's relationship to classical classes) gives the cleanest formal treatment of BQP and known containments (BQP ⊆ PP, ⊆ PSPACE).
4. The natural obstacle: lower bounds against BQP require understanding quantum circuits with access to arbitrary entangled states and intermediate measurements — we lack techniques even for classical circuit lower bounds of comparable strength. A plausible attack route is via the "BQP vs. PH" sub-question, or via polynomial-method/representation-theoretic tools generalized to non-black-box settings.

## Key references

- C. Bennett, E. Bernstein, G. Brassard, U. Vazirani, "Strengths and Weaknesses of Quantum Computing," SIAM J. Comput. 26(5):1510–1523, 1997. Proves the Ω(√N) black-box quantum search lower bound and constructs oracles separating NP from BQP — establishing the relativization barrier.
- J. Watrous, "Quantum Computational Complexity" (survey), arXiv:0804.3401, 2008. Encyclopedic survey defining BQP precisely and summarizing containments (BQP ⊆ PP) and open separations.
- S. Aaronson, A. Wigderson, "Algebrization: A New Barrier in Complexity Theory," ACM TOCT 1(1), 2009, arXiv:0804.3401-adjacent (verify: arXiv:0804.3401 is Watrous; Aaronson–Wigderson is arXiv:0805.1358 (verify)). Shows relativizing and arithmetizing techniques cannot resolve such separations.

## Warnings

- Do not mistake Grover-related query lower bounds for a resolution; they relativize and leave the unrelativized question untouched.
- Random oracles separate NP from BQP with probability 1, but oracles also exist collapsing them — any proposed proof must be checked against oracle counterexamples.
- The informal phrasing "solve all NP problems efficiently" means decision in BQP; don't conflate with QMA, sampling tasks, or heuristic/annealing performance.
- Beware claims that adiabatic/variational algorithms imply NP ⊆ BQP; known results (e.g., on minimum gaps in adiabatic unstructured search (verify)) show no polynomial speedup there.

---
*`ALGO-000188` · unverified*

## Acceptance guidance

Either direction resolves it:

1. **Positive:** An explicit polynomial-time quantum algorithm (uniform circuit family) deciding SAT with error ≤ 1/3. This would prove NP ⊆ BQP.
2. **Negative:** A proof that SAT ∉ BQP (equivalently NP ⊄ BQP), by any technique — circuit lower bounds, a new barriers-surmounting proof system, or a reduction from a known-hard object. A referee would accept any rigorous, peer-reviewable proof; the key challenge is it must evade relativization and (likely) algebrization.
3. **Partial credit variants:** unconditional superquadratic or exponential quantum lower bounds for explicit NP problems in restricted models; or resolving BQP vs. PH.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/7fe9c6dd-0b68-4f98-b634-b706166f27b1?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000188.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000188)
