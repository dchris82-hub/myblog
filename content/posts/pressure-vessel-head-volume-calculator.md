---
title: "Pressure Vessel Head Volume Calculator: Hemi, Ellipsoidal, Torispherical"
date: 2026-04-24
tags: ["Equipment Design", "Pressure Vessel", "Volume Calculator"]
---

When designing a pressure vessel or a storage tank, calculating the accurate internal volume is essential for determining residence time, capacity, and fluid inventory. The geometry of the vessel ends (heads) significantly affects this volume.

This interactive tool allows engineers to calculate the internal volume of standard pressure vessel heads based on the inside diameter and head geometry type.

---

{{< head-calc >}}

---

{{< ad-mid >}}

---

## 📘 Mathematical Formulas for Head Volume

Vessel heads are manufactured in various shapes to withstand different pressure ratings. The volume ($V$) can be expressed as a function of the inside diameter ($D$). 

Below are the standard formulas used in this calculator, where $D$ is in meters, and $V$ is in cubic meters ($m^3$).

### 1. Hemispherical Head
A hemispherical head provides the strongest geometric shape to withstand pressure, as it evenly distributes stress. It is exactly half of a sphere.
$$V = \frac{\pi \cdot D^3}{12}$$

### 2. 2:1 Ellipsoidal Head (Standard Semi-Elliptical)
This is the most common head type for high-pressure applications. The radius of the major axis is exactly twice that of the minor axis, providing a good balance between internal volume, strength, and manufacturing cost.
$$V = \frac{\pi \cdot D^3}{24}$$

### 3. Torispherical Heads (Dished Heads)
Torispherical heads consist of a central "Crown" with a large radius and a "Knuckle" with a smaller radius that connects the crown to the cylindrical shell. The volume depends on the specific ratios of these radii.

**Standard ASME F&D (100% Crown, 6% Knuckle):**
Common for low to medium pressure vessels.
$$V = 0.0847 \cdot D^3$$

**10% Dished (80% Crown, 10% Knuckle):**
$$V = 0.0960 \cdot D^3$$

## 🚨 Engineering Notes
* **Straight Flange (S.F.):** The calculations above provide the volume for the curved section only. In actual manufacturing, heads include a cylindrical "Straight Flange" section (typically 1.5 to 2 inches) to allow for welding to the shell. The volume of this straight section ($V = \frac{\pi \cdot D^2}{4} \cdot L_{SF}$) must be calculated separately and added to the total.
* **Wall Thickness:** Inputs should strictly be the **Inside Diameter (I.D.)**. If Outside Diameter (O.D.) is used, subtract twice the nominal wall thickness before calculating internal capacity.
