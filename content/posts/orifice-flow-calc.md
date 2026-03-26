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
* **Gas Density Calculation:** For gases, the tool calculates upstream actual density from $P_1$, $T_1$, $MW$, and $Z$. Ensure $P_1$ is entered as absolute pressure, and $Z$ is evaluated at the specific inlet relieving condition. 
* **Volumetric Flow:** Reported volumetric flow is strictly based on upstream actual density. It should **not** be interpreted as standard/normal flow ($Sm^3/h$, $Nm^3/h$) or downstream actual flow.
* **Velocity of Approach ($E$):** Applying the incompressible velocity-of-approach factor ($E$) to the compressible isentropic equations is a pragmatic approximation used in this estimator. It is not a rigorous application of standard compressible metering formulas.
* **Discharge Coefficient ($C_d$):** The discharge coefficient is strictly a user-specified constant and is **not** dynamically correlated to the Reynolds number.
* **Scope of Use:** This tool is intended for conceptual design and preliminary estimations only. It is **not** for final detailed design, custody transfer, or certified safety relief sizing.

## 📘 Technical Background & Equations

Unlike simple calculators that apply a generic expansibility factor to the incompressible equation, this estimator separates gas calculations into subcritical and choked regimes using a simplified ideal-gas-style isentropic approach.

### 1. Liquid Phase (Incompressible Flow)
For liquids, the density is assumed constant across the orifice. The mass flow rate ($q_m$) is calculated using the standard orifice equation:

$$q_m = C_d E A \sqrt{2 \rho_1 \Delta P}$$

Where:
* $C_d$ = Discharge Coefficient (typically ~0.62)
* $E$ = Velocity Approach Factor = $\frac{1}{\sqrt{1 - \beta^4}}$
* $A$ = Orifice bore area ($m^2$)
* $\rho_1$ = Upstream density ($kg/m^3$)
* $\Delta P$ = Pressure drop ($P_1 - P_2$)

### 2. Gas Phase (Compressible Isentropic Flow)
When a gas passes through a restriction, it expands. This tool evaluates the critical pressure ratio ($r_c$) using the specific heat ratio ($k$):

$$r_c = \left(\frac{2}{k + 1}\right)^{\frac{k}{k - 1}}$$

Let $r$ be the actual pressure ratio ($P_2 / P_1$). The calculation diverges based on the flow regime:

**A. Subcritical Flow ($r > r_c$):**
The flow is not limited by the speed of sound. The mass flow is calculated as:

$$q_m = C_d E A \sqrt{ 2 \rho_1 P_1 \left(\frac{k}{k-1}\right) \left[ r^{2/k} - r^{(k+1)/k} \right] }$$

**B. Choked (Sonic) Flow ($r \le r_c$):**
When the flow reaches sonic conditions at the controlling section, the mass flow is evaluated using the critical-flow form. Further lowering the downstream pressure ($P_2$) will not increase the mass flow rate:

$$q_m = C_d E A \sqrt{ \rho_1 P_1 k \left(\frac{2}{k+1}\right)^{\frac{k+1}{k-1}} }$$

*(The estimator will display a warning flag if choked conditions are reached, and the actual calculations will rely on the critical limit.)*
