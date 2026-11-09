# Wideband Metasurface EM Absorber Simulation

An engineering project focused on the design, computational simulation, and multi-variable parametric optimization of a flexible, textile-based metamaterial absorber (MA) targeting the X, Ku, and K microwave bands (8.04 GHz to 28.2 GHz).

---

## 🚀 Key Performance Metrics

* **Absorption Efficiency:** >90% continuous wave attenuation.
* **Optimized Bandwidth:** up to **20.008 GHz** continuous profile (8.19 GHz to 28.2 GHz).
* **Fractional Bandwidth:** Exceeds 100%.
* **Target Applications:** Radar Cross-Section (RCS) reduction, stealth technology, and wearable EMI shielding.

---

## 🛠️ System Architecture & Layer Design

The absorber utilizes a robust 3-layer sandwich configuration modeled and simulated in **CST Studio Suite**:

### 1. Top Layer
* **Material:** PU Conductive Film
* **Design Geometry:** Patterned Ring + Cross FSS (Frequency Selective Surface)
* **Key Specifications:** Tuned Surface Resistance (Rs = 100 to 200 ohms per square)

### 2. Middle Substrate
* **Material:** Scuba Knitting Fabric
* **Role:** Dielectric spacer layer
* **Key Specifications:** Thickness (ts = 2.6 mm), Permittivity (Epsilon r = 2), Loss Tangent (tan delta = 0.02)

### 3. Bottom Plane
* **Material:** Copper Metallized Fabric
* **Role:** Reflective ground plane boundary condition
* **Key Specifications:** Thickness (tm = 0.1 mm), Surface Resistance (less than 0.02 ohms per square), blocks 100% of wave transmission

---

## 📐 Mathematical & Circuit Modeling

The localized electric field resonance occurring within the subwavelength "meta-atoms" is structurally mapped using an **RLC Series Equivalent Circuit Model**.

### 1. Complex Electrical Impedance Formula
The patterned top layer acts as a series resonator. Its electrical impedance, represented as Z, dynamically changes based on the wave frequency (omega) and matches with the free space impedance (Z0 = 377 Ohms) using this normal formula:

Z = R + j * omega * L + 1 / (j * omega * C)

* **R (Resistance):** Equivalent surface resistance of the PU conductive film.
* **L (Inductance):** Structural inductance created by the conducting cross arms.
* **C (Capacitance):** Capacitance generated within the dielectric gap rings.
* **j:** The imaginary unit tracking phase variance.

### 2. Reflection Coefficient Boundary Equation
To calculate how much radar signal reflects back, the system continuously computes the Reflection Coefficient (S11) using the total input impedance of the absorber layers (Z_in) and the impedance of air (Z0):

S11 = (Z_in - Z0) / (Z_in + Z0)

* **Perfect Absorption (S11 = 0):** This happens when the absorber's impedance perfectly matches the air (Z_in = Z0). The top part of the formula becomes zero, meaning zero reflection and near 100% absorption.
* **Perfect Reflection (S11 = 1 or -1):** This happens if the impedance is completely mismatched, causing all waves to bounce back and making the object highly visible on radar.
 
### 3. Total Electromagnetic Absorption Formula
The total absorption of the system, represented as A, is calculated using the reflection coefficient (S11) and transmission coefficient (S21). Since the copper ground plane completely blocks the wave from passing through, the transmission becomes zero (S21 = 0), and the formula simplifies to:

A = 1 - (S11 * S11)

---

## 📊 Parametric Sweep Findings

Multi-variable optimization logic was executed to identify the absolute best design parameters for high-efficiency wave absorption. The key findings from the simulation sweeps are:

* **Surface Resistance (Rs):** Tuning the surface resistance to 200 ohms per square optimizes the impedance matching between the metamaterial layer and free space. This configuration yields near-unity absorption over the widest possible continuous bandwidth of 20.008 GHz.
* **Substrate Thickness (ts):** A thickness of 2.6 mm serves as the optimal mechanical spacer dimension. Increasing the thickness to 3.6 mm shifts performance to lower frequencies but heavily destroys the high-frequency coverage. Decreasing it to 1.6 mm shifts the window completely toward the higher Ka-band, losing the critical lower X-band efficiency entirely.
* **Substrate Permittivity (Epsilon r):** Lower dielectric constant values between 1.5 and 2.0 are required to maximize ultra-wideband behavior. Increasing the permittivity to 4.5 shifts the absorption peak to lower frequencies and causes a heavy reduction in total fractional bandwidth.

---

## 📁 Repository Structure

```text
├── simulation_files/      # CST Studio Suite models, boundary profiles & setup files
├── reports/               # Complete Project presentation deck and document PDFs
└── README.md              # Project overview and optimization documentation
```

---

## 👥 Contributors

* **Sutej Raj** (NIT Patna)
* **Ankush Raj** (NIT Patna)
* **Jadhav Mohith** (NIT Patna)
* **Supervisor:** Dr. Rajan Agrahari (ECE Dept., NIT Patna)
