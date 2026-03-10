# Voltage-regulator-design-and-simulation
# ⚡ Linear Voltage Regulator Design

## 📌 Overview

This project presents the **design, analysis, and simulation of a linear voltage regulator circuit** capable of converting a high AC input voltage into a **stable adjustable DC output voltage**.

The system includes:

- AC voltage step-down using a transformer
- AC to DC conversion using a bridge rectifier
- Ripple reduction using a capacitor filter
- Voltage stabilization using an operational amplifier and transistor-based regulation stage
- Current limiting protection

The circuit was analyzed and simulated to validate its performance and stability.


# 🎯 Project Requirements

The voltage regulator was designed with the following specifications:

| Parameter | Value |
|-----------|------|
| Input Voltage | 220V AC |
| Output Voltage Range | 4V – 16V |
| Maximum Output Current | 2.5 A |

The objective is to maintain a **stable DC output voltage** despite variations in input voltage or load.


# 🧠 System Architecture

The voltage regulator consists of four main stages:

1. **Transformer**
2. **Bridge Rectifier**
3. **Capacitor Filter**
4. **Voltage Regulation Stage**

### Block Diagram

```
AC Input (220V)
      │
      ▼
 Transformer
      │
      ▼
Bridge Rectifier
      │
      ▼
 Capacitor Filter
      │
      ▼
Voltage Regulation Circuit
      │
      ▼
 Adjustable DC Output (4V – 16V)
```

# 🔌 Transformer Stage

The transformer reduces the **220V RMS AC input** to a lower voltage suitable for rectification.

### Voltage Relationship

```
Vpeak = Vrms × √2
```

For a 220V RMS supply:

```
Vpeak ≈ 311V
```

The transformer steps this down to approximately **24V RMS** at the secondary.

### Transformer Function

- Steps down high AC voltage
- Provides isolation
- Supplies the rectifier stage


# 🔁 Bridge Rectifier and Capacitor Filter

## Bridge Rectifier

A **full-wave diode bridge** converts AC voltage into pulsating DC voltage.

During each half-cycle:

- Two diodes conduct
- Current flows through the load in the same direction

This results in a **rectified waveform**.

## Capacitor Filter

A capacitor is added to smooth the ripple in the rectified voltage.

### Ripple Voltage Formula

```
C = I / (f × ΔV)
```

Where:

- **I** = Load current (2.5A)
- **f** = 100Hz (full-wave rectifier frequency)
- **ΔV** = Allowed ripple voltage

This produces a smoother DC voltage around **24V** before regulation.


# ⚙️ Voltage Regulation Stage

The regulation stage stabilizes the output voltage using:

- **Zener diode** (voltage reference)
- **Operational amplifier (LM393)** as an error amplifier
- **TIP3055 power transistors**
- **Feedback network**
- **Current sensing resistor**

### Components Overview

| Component | Function |
|----------|----------|
| Zener diode (2.5V) | Reference voltage |
| LM393 Op-Amp | Error amplifier |
| TIP3055 Transistors | Power regulation |
| Potentiometer | Output voltage adjustment |
| R8 (0.15Ω) | Current sensing |


## Feedback Control

The circuit uses **negative feedback**.

Steps:

1. Output voltage is divided using a resistor network.
2. This voltage is compared with the Zener reference.
3. The operational amplifier generates an **error signal**.
4. The transistors adjust conduction accordingly.

This ensures the **output voltage remains stable**.


# 🧮 Resistance Calculations

The output voltage is determined by the feedback network:

```
Vout = Vz × (1 + Rtop / R7)
```

Where:

- **Vz = 2.5V**
- **R7 = 1kΩ**

For **Vout = 16V**:

```
Rtop ≈ 5.4kΩ
```

Chosen values:

| Component | Value |
|----------|------|
| R5 | 490Ω |
| Potentiometer (P) | 4.9kΩ |


## Load Resistance

```
RL = Vout / Iout
```

Resulting range:

```
RL ∈ [1.6Ω , 6.4Ω]
```

Chosen value:

```
RL = 4.8Ω
```


# 🛠 Circuit Implementation

The full circuit includes:

- Transformer
- Full bridge rectifier
- Filter capacitor
- Zener reference
- Operational amplifier
- Power transistors
- Current limiting resistor

The regulator operates as a **linear voltage regulator with feedback control**.


# 🧪 Simulation

The circuit was simulated using **PSpice / Cadence tools**.

Two main simulation methods were used:

## 1️⃣ Transient (Time Domain) Analysis

Purpose:

- Observe voltage behavior over time
- Verify voltage stability
- Analyze ripple reduction

## 2️⃣ DC Sweep Analysis

Purpose:

- Evaluate regulator response
- Observe voltage variation as the potentiometer changes


# 📊 Statistical Analysis

To evaluate reliability, the following simulations were performed:

### Monte Carlo Analysis

Used to study variations caused by:

- Component tolerances
- Parameter variations

Measured parameter:

- **Power dissipated by load (RL)**

### Worst Case Analysis

Determines:

- Maximum voltage
- Maximum power dissipation
- Safety margins


# 📈 Results

The simulation confirmed that:

- The rectifier successfully converts AC to DC.
- The capacitor filter significantly reduces ripple.
- The regulation stage stabilizes output voltage.
- Output voltage can be adjusted within **4V – 16V**.
- Current limiting protects the circuit.


# ⚡ Key Concepts Demonstrated

This project demonstrates several fundamental electronics concepts:

- AC to DC conversion
- Transformer voltage scaling
- Rectification
- Ripple filtering
- Feedback regulation
- Current limiting
- Power transistor control

# 🧾 Conclusion

A **linear voltage regulator** maintains a stable output voltage despite variations in input voltage, load conditions, or temperature.

In this project:

- A regulator capable of **4V–16V adjustable output** was designed.
- The circuit successfully supports **up to 2.5A output current**.
- Feedback control ensures voltage stability.
- Simulation results validate the circuit’s functionality.

While linear regulators are simple and reliable, they are less efficient compared to switching regulators because excess energy is dissipated as heat.

# 📚 References

- Laura Ivanciu, Emilia Șipoș — *Electronic Devices*
- Floyd — *Electronic Devices: Conventional Current Version*
- Electronics StackExchange
- Cadence Community
- CircuitLab
- Cirkit Designer
- Educational resources and simulation documentation
