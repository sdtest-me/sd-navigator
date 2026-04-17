# SDTEST® SD-Navigator

**Behavioral simulation engine based on Spiral Dynamics and Algebra of Conscience**

→ **[Live demo](https://sdtest-me.github.io/sd-navigator/)**

---

## What it does

SD-Navigator models how management decisions affect an organization's behavioral system over time.

It answers questions that standard analytics cannot:
- *What will happen if we reduce staff with our current vMeme profile?*
- *How will different value systems react to a salary cut?*
- *Which decision path produces the most stable outcome?*

The model is built on the transition function:

```
S(t+1) = f[S(t), u(k), C]
```

Where:
- `S(t)` — current state vector (7 vMemes + 3 psychological sensors)
- `u(k)` — management action (u1–u9)
- `C` — empirical correlation matrix from SDTEST® dataset
- `J` — stability score from Lefebvre's Algebra of Conscience

---

## Theoretical foundations

| Component | Source |
|-----------|--------|
| vMeme framework (Purple → Turquoise) | Clare Graves / Beck & Cowan — Spiral Dynamics |
| Algebra of Conscience scoring (J) | Vladimir Lefebvre |
| Empirical correlations (C matrix) | SDTEST® dataset — 91,000+ assessments, 172 countries |
| Dynamic Programming Model | Bellman optimality principle |

---

## How to use

Open `index.html` in any browser — no server, no dependencies, no login required.

### Controls

**State vector S(t) — worldview profile**
Set the current vMeme distribution of your organization (0.00–1.00 per meme). Use your SDTEST® assessment results or estimate from observation.

**Psychological sensors**
- `Fear` — current level of existential threat in the system
- `Trust` — trust in leadership and institutional stability
- `Wellbeing` — general psychological safety

**Management action u(k)**

| Code | Action |
|------|--------|
| u1 | Unpaid vacation |
| u2 | Do nothing (pause) |
| u4 | Reduce salaries |
| u6 | Remote work policy |
| u7 | Reduce staff |
| u9 | Innovation push |

**Objective weights wᵢ**
Adjust the relative importance of each factor in the J score calculation.

### Output tabs

- **Predicted state S(t+1)** — vMeme trajectory and psychological sensor deltas after action
- **Butterfly effects** — network cascade chain showing weak-signal amplification
- **Adaptive protocol** — condition-action map for the current system state

---

## Correlation matrix (C)

The C matrix encodes empirically measured relationships between management actions and vMeme/sensor responses, derived from SDTEST® survey data.

Example entries:

```javascript
u7 (Reduce staff): {
  purple: +0.02, red: +0.03, blue: -0.02, orange: -0.01,
  green: -0.04, yellow: -0.05, turquoise: -0.02,
  fear: +0.25, trust: -0.18, well: -0.22,
  actionImpact: -0.70
}
```

This version uses a **synthetic demonstration dataset**. The full empirically-calibrated correlation matrix is available through the [SDTEST® Research and Enterprise tiers](https://sdtest.me).

---

## J score — Algebra of Conscience

```
J = −ΔFear·w_fear + ΔWellbeing·w_well + ΔTrust·w_trust + actionImpact·w_action + cultureFit·w_cult
```

| J range | Interpretation |
|---------|---------------|
| J > 0.20 | Optimal — action strengthens system stability |
| −0.10 ≤ J ≤ 0.20 | Neutral — moderate or mixed effect |
| J < −0.10 | Warning — action predicted to destabilize the system |

---

## Extending this model

This is the public demo layer. Contributions welcome:

- Add new management actions (u3, u5, u8...)
- Implement multi-step trajectory simulation (t+1, t+2, t+3)
- Add country/industry presets for S(t) initialization
- Visualize the vMeme distribution as a radar chart
- Build a comparison mode (action A vs action B)

See [Issues](https://github.com/sdtest-me/sd-navigator/issues) for open tasks.

---

## Relationship to SDTEST® platform

```
Layer 1 — Individual assessment    →  sdtest.me (free)
Layer 2 — Global behavioral dataset →  sdtest.me (Research / Enterprise)
Layer 3 — SD-Navigator™             →  this repo (demo) + Sponsor Lab (calibrated on your data)
```

The public version demonstrates the simulation logic on a synthetic dataset.  
The Sponsor Lab version is calibrated on your organization's own SDTEST® data — turning the demo into a real decision-support system.

→ [Learn more about SDTEST®](https://sdtest.me)

---

## License

MIT — free to use, fork, and build upon.  
If you publish research or implementations based on this model, a reference to SDTEST® is appreciated.

---

*Built on Spiral Dynamics theory (Graves, Beck & Cowan) and Lefebvre's Algebra of Conscience.*  
*Empirical data: [SDTEST®](https://sdtest.me) — 91,000+ assessments · 39 VUCA indicators · 172 countries*
