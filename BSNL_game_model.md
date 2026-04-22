# BSNL Extension: Mixed-Motive Competitor — Game-Theoretic Model

## Overview

This document extends the repeated-Bertrand framework from `02_simulation.ipynb` by introducing a government-backed firm (BSNL) whose objective is a convex combination of profit and consumer surplus. The model asks: how does a welfare-weighted competitor change equilibrium prices, incumbent profits, and consumer outcomes in a concentrated telecom oligopoly?

---

## Players and Roles

| Player | Type | Objective |
|---|---|---|
| Airtel, Jio, Vi (×3) | Private incumbents | Maximise per-period profit; sustain tacit collusion via grim trigger |
| BSNL | Government-backed firm | Maximise α·π + (1−α)·CS, with α = 0.5 |

---

## Assumptions

### A1 — BSNL's objective is fixed externally (α = 0.5)
α is a **policy parameter** set by the government, not a variable BSNL optimises over. At α = 0.5 BSNL weighs its own profit and aggregate consumer surplus equally. This is a deliberate simplification — in reality α reflects political economy, budget pressures, and the government's mandate. Sensitivity to α is explored in the notebook.

### A2 — BSNL has a cost disadvantage (c_B = 1.3 · c_inc)
BSNL's marginal cost is 30% above private incumbents. This reflects its bloated legacy workforce (~65 000 employees vs Airtel's ~18 000), older infrastructure, and absence of lean outsourcing. BSNL prices low not because it is efficient but because it is subsidised.

### A3 — Partial market capture via linear share model
BSNL does **not** capture the entire market when it undercuts. Its market share is:

$$s_B(p_B, p_\text{inc}) = \min\!\bigl(s_0 + \gamma \cdot \max(p_\text{inc} - p_B,\, 0),\; s_\text{max}\bigr)$$

- $s_0 = 0.10$: captive base share (rural subscribers, government offices, price-insensitive customers who will not switch regardless).
- $\gamma = 0.020$: switching sensitivity — each ₹1 price advantage attracts an additional 2% of the market.
- $s_\text{max} = 0.35$: hard cap on BSNL's share even at extreme price gaps (reflects persistent quality/coverage inferiority).

This is more realistic than homogeneous Bertrand (winner takes all) and avoids the degenerate result where a slightly cheaper BSNL serves everyone.

### A4 — BSNL plays myopically (no repeated-game strategy)
BSNL solves a **static welfare-weighted problem each period**. It does not punish, reward, or anticipate incumbent strategies. This is appropriate given BSNL's bureaucratic pricing process (tariff changes require TRAI filings and government approval — no capacity for rapid strategic response).

### A5 — BSNL moves first; incumbents best-respond
BSNL's tariff plans are announced and sticky (changed infrequently). Incumbents observe BSNL's price and then choose their collusive price. This is a Stackelberg-style setup with BSNL as the de-facto price leader by default, not by strategic choice.

### A6 — Government subsidy cap (loss floor L̄)
BSNL can sustain per-period losses up to $\bar{L}$. If BSNL's welfare-optimal price would imply $\pi_B < -\bar{L}$, it adjusts upward to the minimum price that keeps losses at exactly $-\bar{L}$. This binds only when incumbents collude at very high prices — precisely when BSNL's welfare mandate most wants to undercut aggressively.

### A7 — Incumbents play standard grim trigger among themselves
BSNL's presence does not alter the punishment technology between incumbents. When any incumbent deviates from the collusive price, all incumbents revert permanently to Bertrand (price = MC) among themselves. BSNL continues pricing according to its own objective in all phases.

### A8 — Demand is linear
$$Q(p) = \max(a - b\cdot p,\; 0), \qquad a = 100,\; b = 1$$

Total quantity at a given price follows the same curve as the base model.

---

## Formal Model

### Demand and Market Shares

Each firm's quantity:

$$q_B = s_B \cdot (a - b\,p_B)$$

$$q_i = \frac{1 - s_B}{n} \cdot (a - b\,p_\text{inc}), \quad i = 1,\dots,n$$

where $s_B = s_B(p_B, p_\text{inc})$ from A3.

Consumer surplus uses the share-weighted effective market price:

$$p_\text{eff} = s_B\,p_B + (1 - s_B)\,p_\text{inc}$$

$$CS = \frac{(a - p_\text{eff})^2}{2b}$$

### Objective Functions

**Incumbents** (collusive phase):

$$\max_{p_\text{inc}}\; \pi_i = (p_\text{inc} - c_\text{inc})\cdot q_i(p_B,\, p_\text{inc})$$

Note: as $p_\text{inc}$ rises, $s_B$ grows (incumbents lose share to BSNL), so the optimum is interior — below the no-BSNL monopoly price $p^m$.

**BSNL:**

$$\max_{p_B}\; U_B = \alpha\,\pi_B + (1-\alpha)\,CS$$

$$\text{s.t.}\quad \pi_B \geq -\bar{L}$$

where $\pi_B = (p_B - c_B)\cdot q_B$.

### Stage-Game Equilibrium

The equilibrium is a fixed point $(p_B^*,\, p_\text{inc}^*)$ such that:

1. $p_B^* = \arg\max_{p_B} U_B(\,p_B,\; p_\text{inc}^*)$ subject to the loss floor
2. $p_\text{inc}^* = \arg\max_{p_\text{inc}} \pi_i(\,p_B^*,\; p_\text{inc})$

Both best-response functions are upward-sloping (strategic complements), and the fixed point is found numerically.

### Repeated Game — Collusion Sustainability

Define:
- $\pi^\text{coll}$: per-incumbent profit at $(p_B^*, p_\text{inc}^*)$
- $\pi^\text{dev}$: deviation profit — one incumbent undercuts $p_\text{inc}^* - \varepsilon$, capturing all $(1-s_B^*)$ incumbent market share instantly; BSNL's share is unchanged
- $\pi^\text{nash} = 0$: punishment payoff (incumbents at MC; BSNL's presence doesn't affect this since $c_B > c_\text{inc}$, so BSNL can never undercut incumbents at MC)

Then $\pi^\text{dev} \approx n \cdot \pi^\text{coll}$, and the IC constraint gives:

$$\delta^* = \frac{n-1}{n}$$

**This is identical to the no-BSNL result.** BSNL does not change *whether* collusion is sustainable — it changes the *level* at which incumbents collude (lower price, lower profit). The critical insight is that BSNL acts as a permanent price ceiling on incumbent collusion, not as a destabilising force.

---

## Parameters

| Parameter | Value | Interpretation |
|---|---|---|
| a, b | 100, 1 | Linear demand (same as base model) |
| c_inc | 20 | Incumbent marginal cost |
| c_bsnl | 26 | BSNL MC (30% premium) |
| s₀ | 0.10 | Captive base share |
| γ | 0.002 | Switching sensitivity per ₹1 gap |
| s_max | 0.35 | Share cap |
| α | 0.50 | Welfare weight |
| n | 3 | Number of incumbents |
| L̄ | 100 | Per-period max sustainable loss |

---

## Model Predictions

1. **Incumbents collude at $p_\text{inc}^* < p^m$**: BSNL's share-stealing effect makes the monopoly price sub-optimal for incumbents. The constraint is soft (BSNL's share is small) so the price reduction is moderate.

2. **BSNL prices above its own MC and is marginally profitable**: At α = 0.5 and γ = 0.002, the profit motive is strong enough to push BSNL's optimal price above $c_B = 26$.

3. **Consumer surplus is higher than under pure private oligopoly**: Even with BSNL's small market share, the large price gap (BSNL ~₹28–30 vs incumbents ~₹58) moves the effective average price down significantly, with a quadratic effect on CS.

4. **Critical δ is unchanged at (n−1)/n = 2/3**: BSNL disciplines the price level but not the sustainability of collusion.

5. **As α → 0**: BSNL prices near or below MC, the budget constraint binds, and government subsidy requirement grows. CS rises but BSNL is not self-sustaining.

6. **As α → 1**: BSNL behaves like a fourth private firm. If it prices near $p_\text{inc}$, its share stays near $s_0 = 10\%$ and it has minimal welfare impact.
