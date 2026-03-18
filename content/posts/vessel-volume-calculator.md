---
title: "Vessel Liquid Volume Calculator"
date: 2026-03-18
tags: ["Engineering", "Tool"]
---

This calculator computes the liquid volume in a vessel.

{{< vessel-liquid-volume-calc >}}
{{< ad-mid >}}
Boost your productivity with this calculation tool!

# 📘 Technical Guide: Vessel Liquid Volume Calculation (Engineering-Oriented)

This calculator evaluates vessel liquid volume using a combination of **analytical geometry** and **numerical integration**, providing reliable results for **process design, sizing verification, and engineering estimation**.

---

## 1. Definition of Length ($L$)

In this tool, **Length ($L$)** is defined as:

> **Straight Cylindrical Length (Tangent-to-Tangent, T/T)**

- This represents only the cylindrical shell length.
- The **total internal vessel height/length** is:

$$
\text{Total Length} = L + 2 \times \text{Head Depth}
$$

### Head Depth
- **Hemispherical head:** $D/2$
- **2:1 Ellipsoidal head:** $D/4$
- **Flat head:** $0$

---

## 2. Head Geometry Modeling

### 2.1 Hemispherical Head
- Modeled as a **true hemisphere**
- Volume and partial volume follow exact spherical geometry

---

### 2.2 2:1 Ellipsoidal Head

The 2:1 ellipsoidal head is modeled as:

> **Ideal half-ellipsoid (semi-ellipsoid)**

- Semi-axes:
  - Horizontal radius: $r = D/2$
  - Vertical depth: $a = D/4$

- Full head volume:

$$
V = \frac{\pi D^3}{24}
$$

> ⚠️ **Note:**  
> This is an ideal geometric model.  
> Real fabricated heads (e.g., ASME F&D) include knuckle regions and may differ slightly.

---

### 2.3 Flat Head
- Assumed to have **zero internal volume contribution**
- Used for simplified cylindrical vessels

---

## 3. Horizontal Vessel Calculation

For horizontal vessels, total volume is calculated as:

$$
V = V_{\text{cylinder}} + V_{\text{heads}}
$$

---

### 3.1 Cylindrical Section

The liquid volume in the cylindrical section is calculated using the **circular segment method**:

- Based on liquid height $h$
- Uses trigonometric segment area formula

---

### 3.2 Head Sections (Numerical Integration)

Unlike simplified approaches, head volumes are computed using:

> **Numerical integration along the head axis**

Procedure:
1. The head is discretized along its axial direction
2. At each location:
   - Local radius is determined from geometry
   - Liquid-filled cross-sectional area is computed
3. Volume is obtained by integrating these areas

This method is applied to:
- Hemispherical heads
- 2:1 ellipsoidal heads

> ✔ This approach avoids inaccuracies associated with closed-form approximations for partially filled horizontal heads.

---

## 4. Vertical Vessel Calculation

Vertical vessels are divided into three regions:

---

### 4.1 Bottom Head Zone ($0 \le h \le \text{Head Depth}$)

The volume is calculated using the **partial volume of a rotational solid**:

$$
V = \frac{\pi r^2}{b^2} \left( b h^2 - \frac{h^3}{3} \right)
$$

Where:
- $r = D/2$
- $b =$ head depth

---

### 4.2 Cylindrical Shell Zone

For liquid levels within the cylindrical section:

$$
V = V_{\text{bottom head}} + \pi r^2 (h - b)
$$

---

### 4.3 Top Head Zone

When liquid enters the top head:

$$
V = V_{\text{bottom head}} + V_{\text{shell}} + V_{\text{top head (partial)}}
$$

Due to geometric symmetry:
- The **top head partial volume** is calculated using the same formulation as the bottom head.

---

## 5. Numerical Stability & Validation

To ensure robust calculations:

### 5.1 Domain Clamping
- Prevents invalid values in:
  - $\arccos$
  - square root
- Ensures inputs remain within valid geometric bounds

---

### 5.2 Input Validation
The following conditions are enforced:
- $D > 0$
- $L \ge 0$
- $LLL \ge 0$, $HLL \ge 0$
- $HLL > LLL$

---

### 5.3 Height Limitation
Liquid height is automatically limited to the physically valid maximum:

- **Horizontal vessel:** $0 \le h \le D$
- **Vertical vessel:**
  - Flat: $L$
  - Ellipsoidal: $L + D/2$
  - Hemispherical: $L + D$

---

## 6. Modeling Assumptions

This calculator is based on the following assumptions:

- Identical head type on both ends
- No internal structures (trays, baffles, agitators)
- No nozzle or piping volume included
- No corrosion allowance or wall thickness correction
- Pure geometric (volume-only) calculation
- Ellipsoidal head treated as **ideal half-ellipsoid**

---

## 7. Applicability

This tool is suitable for:

- Vessel sizing checks
- Surge volume estimation
- Hold-up volume estimation
- Process design verification

---

## ⚠️ Disclaimer

This calculator provides **engineering-level estimation**.

For final design and procurement:
- Always verify against **vendor drawings**
- Confirm with **mechanical design calculations**
- Consider fabrication tolerances and internal components

---
