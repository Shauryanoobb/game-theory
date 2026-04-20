# Price Wars in Indian Telecom: A Game-Theoretic Analysis of the Jio Entry Shock

## Slide 1 — Title
- Title, team members, course, date
- One-line hook: *"How did ARPU fall 60% in 18 months — and rise back with no announcement?"*

## Slide 2 — The Puzzle (Motivation)
- Chart: ARPU 2010–2024 (TRAI data) with three colored bands: Stable / Crash / Rebound
- Three observations to explain:
  1. Why were prices flat 2010–2016 despite cost decline?
  2. Why did prices crash Sep 2016 – Mar 2018?
  3. Why did prices rise in lockstep in Nov 2021 and Jul 2024?

## Slide 3 — Game Setup
- Players N = {Airtel, Vodafone, Idea, Jio, ...} (varies by phase)
- Actions: p_i ∈ [c, p_monopoly]
- Payoffs: π_i = (p_i − c_i) · D_i(p_1, …, p_n)
- Timing: simultaneous per period, infinite horizon, discount δ
- Information: complete (assumption)
- **Game class:** infinitely repeated Bertrand → entry game → repeated Bertrand

## Slide 4 — Stage-Game Bertrand NE
- Result: unique NE is p_i = c for all i → zero profits
- Contradiction with data → motivates repeated game

## Slide 5 — Phase 1 Model: Folk Theorem & Grim Trigger
- Collusive strategy: everyone prices at p^m, reverts to c forever if deviation
- Sustainability: δ ≥ (n−1)/n
- Plot: critical δ vs n
- Map to India: n=3 effective → δ ≥ 0.67 easily met

## Slide 6 — Phase 1 Evidence
- Airtel/Voda/Idea ARPU flat within ±5% for 24 quarters
- EBITDA margins 30–35%, well above cost recovery
- No CCI enforcement action — but "conscious parallelism"

## Slide 7 — Phase 2 Model: Jio as Asymmetric Entrant
- Jio's MC_J < c (all-IP network, no legacy overhead)
- Entry game tree: Jio (low vs very-low) → Incumbents (fight vs accommodate)
- Free-tier as costly signal (Milgrom-Roberts logic, inverted)
- SPE prediction: weakest exit, mid-tier merge, strongest survives degraded

## Slide 8 — Phase 2 Evidence
- Aircel bankruptcy (2018), RCom bankruptcy (2019)
- Vodafone-Idea merger (Aug 2018)
- Airtel survives with Africa/enterprise support
- ARPU crash graph overlay

## Slide 9 — Phase 3 Model: Collusion Returns
- Post-consolidation n = 3 → Folk Theorem bites again
- Event study: Nov 2021 hike, Jul 2024 hike — parallel within days
- No evidence of explicit cartel → tacit collusion

## Slide 10 — Computational Artifact (Live)
- Notebook demo: simulate repeated Bertrand under different δ, n, MC asymmetry
- Show grim-trigger trajectory, deviation shock, reversion path
- Overlay simulated vs actual ARPU 2010–2024

## Slide 11 — Comparative Statics & Robustness
- How δ changes with license tenure
- How MC asymmetry changes predation cost
- How product differentiation weakens Bertrand prediction

## Slide 12 — Policy Implications
- CCI 2017: predatory pricing cleared — was it right?
- AGR 2019: accidental duopoly engineering
- Floor pricing (2020 proposal): equivalent to enforcing collusion — reject
- Structural remedies > price regulation

## Slide 13 — Limitations
- Homogeneous goods assumption (coverage/quality differ)
- Complete information (costs are private → BNE extension)
- No capacity constraints (spectrum is scarce in reality)

## Slide 14 — Conclusion & Takeaway
- Three regimes, one framework (Bertrand repeated game)
- Market structure (n, cost asymmetry) predicts pricing behavior
- Game theory explains what "why did prices change?" journalism cannot

## Slide 15 — Q&A
- Backup slides: derivation of δ ≥ (n−1)/n, HHI computation, sensitivity tables
