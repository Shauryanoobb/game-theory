# Theory Notes — Full Derivations

## 1. Bertrand Stage Game

**Setup.** n firms, homogeneous good, symmetric constant marginal cost c, market demand D(p).
Each firm i sets price p_i simultaneously. Consumers buy from the lowest-price firm (ties split evenly).

**Demand received by firm i:**
```
D_i(p_1,...,p_n) = D(p_i)     if p_i < min_{j≠i} p_j
                 = D(p_i)/k   if p_i ties with k−1 others at the minimum
                 = 0           otherwise
```

**Claim.** The unique pure-strategy NE is p_i = c ∀ i.

**Proof sketch.**
- Any p* > c cannot be equilibrium: some firm can undercut to p* − ε, capture full demand, earn (p*−ε−c)·D(p*−ε) > 0, which exceeds its (p*−c)·D(p*)/n share.
- p_i < c is weakly dominated (negative profit if served).
- p_i = c for all i: no profitable deviation (raising loses all demand; lowering gives negative profit).

**Why this contradicts India 2010–2016.** Positive EBITDA margins of 30–35% imply p >> c. Stage-game NE cannot explain the data → need repeated interaction.

---

## 2. Infinitely Repeated Bertrand — Folk Theorem

**Setup.** Stage game G played at t = 0, 1, 2, ... forever. Common discount δ ∈ (0,1).
Strategy: history-dependent pricing rule.
Solution concept: subgame-perfect equilibrium (SPE).

**Grim-trigger profile σ*.**
- At t = 0: play p^m (monopoly price, profits split n ways)
- At t > 0: play p^m if history shows everyone priced p^m in every past period; else play c forever.

**Deviation payoff.** At any period where collusion holds, firm i can deviate to p^m − ε, capture (nearly) all demand for one period, earn ≈ π^m. Thereafter, punishment reverts to 0 forever.

**Continuation payoffs (from any collusive period onwards):**
- No deviation: (π^m / n) · (1 + δ + δ² + ...) = (π^m/n) / (1−δ)
- Deviate once: π^m + 0 + 0 + ... = π^m

**Incentive constraint:**
```
π^m / n
─────── ≥ π^m
 1 − δ
```

Solving:
```
δ ≥ 1 − 1/n = (n−1)/n
```

**Interpretation.** The more firms, the more patient each must be to sustain collusion.

| n | Critical δ* |
|---|---|
| 2 | 0.500 |
| 3 | 0.667 |
| 4 | 0.750 |
| 5 | 0.800 |
| 7 | 0.857 |

**Folk Theorem (Fudenberg-Maskin 1986 version).** Any feasible, individually rational payoff can be sustained as SPE for δ close enough to 1. Collusion is *one* such equilibrium among many.

---

## 3. Why Jio's Entry Broke Collusion

Three mechanisms simultaneously:

**(a) Cost asymmetry.** If MC_Jio = c_J < c_incumbent, then:
- Jio's "deviation payoff" in the collusive regime is larger (bigger margin when undercutting)
- Jio's "punishment payoff" is not zero — at p = c_incumbent, Jio still earns (c − c_J) · D(c)
- → Jio's IC to collude is violated: *Jio's best response is always to undercut.*

**(b) n-shock.** Jio adds a player. Critical δ jumps from 0.67 (n=3) to 0.75 (n=4). Even symmetric firms might not sustain.

**(c) Time-horizon shock.** If Jio is believed to be short-lived, incumbents rationally fight. If Jio signals long horizon (the ₹1.5 lakh crore capex = sunk commitment), incumbents rationally accommodate → price collapse.

---

## 4. Predation / War of Attrition Model

**Setup.** After entry, stage game is Bertrand. Each firm i has a cash reserve W_i. Per-period loss under price war is L. Firm exits when cumulative losses exceed W_i.

**Symmetric war-of-attrition prediction:** firms mix over exit times. Expected survivor is the firm with largest W_i.

**Empirical mapping:**
| Firm | Parent backing | Outcome |
|------|----------------|---------|
| Aircel | Maxis (strained) | Exited 2018 |
| RCom | ADAG (distressed) | Bankrupt 2019 |
| Tata Docomo | Tata (strategic exit) | Exited 2017 |
| Vodafone India | Vodafone Group (pressured) | Merged 2018 |
| Idea | Aditya Birla | Merged 2018 |
| Airtel | Bharti (strong) | Survived |
| Jio | Reliance (deepest) | Dominant |

Ordering of exits matches ordering of parent financial strength → model is consistent with data.

---

## 5. Return of Tacit Collusion (Post-2020)

With n = 3 and very high δ (license horizons ~20 years, industry sunk investment):
```
(n−1)/n = 2/3 ≈ 0.667 << δ_effective ≈ 0.95+
```
Collusive equilibrium is *easily* sustainable.

**Observable signature — "conscious parallelism":**
- 25 Nov 2021: Airtel announces tariff hike (~20%)
- 29 Nov 2021: Jio matches
- 30 Nov 2021: Vi matches
- No prior announcement, no meeting — but near-simultaneous moves

This is legally distinct from a cartel (no communication proved) but equilibrium-equivalent to collusion.

---

## 6. Comparative Statics (for slides/notebook)

Critical parameters:
- **δ** (patience): ↑ δ → easier to sustain collusion
- **n** (number of firms): ↑ n → harder to sustain
- **cost asymmetry** (c_i spread): ↑ spread → harder (low-cost firm prefers undercutting)
- **demand elasticity**: ↑ elasticity → lower π^m, smaller gain from collusion, but IC unaffected in symmetric case
- **punishment severity**: Bertrand reversion is already the harshest; can't do better in this setup

All of these are sliders in the notebook.
