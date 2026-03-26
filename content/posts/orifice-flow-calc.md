---
title: "Restriction Orifice (RO) Flow Estimator: Gas & Liquid"
date: 2026-03-26
tags: ["Fluid Dynamics", "Process Design", "Orifice Sizing", "Estimation Tools"]
---

Sizing a Restriction Orifice (RO) or evaluating flow across a given orifice plate is a daily task in process engineering. Whether you are checking pump minimum flow lines (liquids) or making a preliminary estimate for gas restriction cases, understanding flow limits—especially choked flow—is critical.

This browser-based estimator provides preliminary mass-flow and upstream actual volumetric-flow estimates across an orifice for compressible gases and incompressible liquids.

---

{{< orifice-flow-calc >}}

---

{{< ad-mid >}}

---

## 🚨 Engineering Limitations & Disclaimer

Before using the estimates provided by this tool, please note the following critical boundaries:
* **Gas Density Input:** The gas density provided must be the **upstream actual density** at the specific operating pressure (P1) and temperature (T1).
* **Phase Changes & Two-Phase Flow:** The liquid model assumes strict incompressibility and **does not cover cavitation, flashing, or two-phase flow** phenomena.
* **Scope of Use:** This tool is strictly intended for conceptual design and preliminary engineering estimations. It is **not** for final detailed design, custody transfer metering, or certified safety relief (PSV/BDV) sizing.

## 📘 Technical Background & Equations

Unlike simple calculators that apply a generic expansibility factor to the incompressible equation, this estimator separates gas calculations into subcritical and choked regimes using a simplified ideal-gas-style isentropic approach.

### 1. Liquid Phase (Incompressible Flow)
For liquids, the density is assumed constant across the orifice. The mass flow rate (qm) is calculated using the standard orifice equation:

qm = Cd * E * A * sqrt(2 * rho1 * DP)

Where:
* Cd = Discharge Coefficient (typically ~0.62)
* E = Velocity Approach Factor = 1 / sqrt(1 - beta^4)
* A = Orifice bore area (m2)
* rho1 = Upstream density (kg/m3)
* DP = Pressure drop (P1 - P2)

### 2. Gas Phase (Compressible Isentropic Flow)
When a gas passes through a restriction, it expands. This tool evaluates the critical pressure ratio (rc) using the specific heat ratio (k):

rc = [ 2 / (k + 1) ]^[ k / (k - 1) ]

Let r be the actual pressure ratio (P2 / P1). The calculation diverges based on the flow regime:

**A. Subcritical Flow (r > rc):**
The flow is not limited by the speed of sound. The mass flow is calculated as:

qm = Cd * E * A * sqrt( 2 * rho1 * P1 * [k / (k - 1)] * [ r^(2/k) - r^((k+1)/k) ] )

**B. Choked (Sonic) Flow (r <= rc):**
When the flow reaches sonic conditions at the controlling section, the mass flow is evaluated using the critical-flow form. Further lowering the downstream pressure (P2) will not increase the flow rate:

qm = Cd * E * A * sqrt( rho1 * P1 * k * [ 2 / (k + 1) ]^[ (k+1) / (k-1) ] )

*(The estimator will display a warning flag and show the "Effective DP" used for this choked condition.)*
