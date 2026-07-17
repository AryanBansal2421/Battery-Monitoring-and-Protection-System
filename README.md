# Battery Monitoring and Protection System

## Overview

This project presents the design and simulation of a Battery Monitoring and Protection System using LTspice. The system continuously monitors battery voltage and provides protection against undervoltage and overvoltage conditions while also estimating the battery's state of charge using multiple threshold levels.

The design demonstrates practical analog circuit design concepts commonly used in battery-powered embedded systems, power management circuits, and industrial electronics.

---

## Objectives

* Monitor battery voltage using a resistor-divider sensing network.
* Detect low battery conditions using a comparator.
* Detect overvoltage conditions using a comparator.
* Improve noise immunity using hysteresis.
* Estimate battery state-of-charge using multiple voltage thresholds.
* Verify circuit operation through LTspice simulations.

---

## System Architecture

Battery Voltage → Voltage Divider → Vsense

Vsense is used by:

* Low Battery Detection Comparator
* Overvoltage Detection Comparator
* Battery Level Indicator Comparators

Outputs:

* LOW_BATTERY_ALERT
* OVERVOLTAGE_ALERT
* 80% Battery Indicator
* 50% Battery Indicator
* 20% Battery Indicator

---

## Design Specifications

| Parameter             | Value         |
| --------------------- | ------------- |
| Battery Voltage Range | 3.0V – 4.2V   |
| Divider Resistors     | 10kΩ, 33kΩ    |
| Divider Ratio         | 33/43 = 0.767 |
| Low Battery Threshold | 3.0V          |
| Overvoltage Threshold | 4.25V         |
| Comparator Supply     | ±5V           |
| Feedback Resistor     | 100kΩ         |

---

## Voltage Divider Design

The battery voltage is scaled using a resistor divider:

Vsense = VBAT × (R2 / (R1 + R2))

Where:

* R1 = 10kΩ
* R2 = 33kΩ

Divider Ratio:

Vsense = VBAT × (33 / 43)

Vsense = 0.767 × VBAT

Example:

For VBAT = 4.2V

Vsense = 4.2 × 0.767

Vsense ≈ 3.22V

---

## Low Battery Protection

A comparator is used to detect when the battery voltage falls below 3.0V.

Threshold Calculation:

VBAT = 3.0V

Vsense = 3.0 × (33 / 43)

Vsense ≈ 2.30V

Reference Voltage:

Vref_LOW = 2.30V

When:

Vsense < 2.30V

LOW_BATTERY_ALERT is activated.

---

## Hysteresis Implementation

A positive feedback resistor is added around the comparator to create hysteresis.

Benefits:

* Prevents output chatter near threshold voltage.
* Improves noise immunity.
* Creates separate turn-on and turn-off thresholds.

This technique is widely used in battery management and industrial sensing applications.

---

## Overvoltage Protection

A second comparator monitors battery overvoltage conditions.

Battery Limit:

VBAT = 4.25V

Corresponding Vsense:

Vsense = 4.25 × (33 / 43)

Vsense ≈ 3.26V

Reference Voltage:

Vref_OV = 3.26V

When:

Vsense > 3.26V

OVERVOLTAGE_ALERT is activated.

---

## Battery State-of-Charge Estimation

Multiple comparators are used to estimate battery charge level.

| Battery Level | Battery Voltage | Vsense Threshold |
| ------------- | --------------- | ---------------- |
| 80%           | 4.0V            | 3.07V            |
| 50%           | 3.6V            | 2.76V            |
| 20%           | 3.3V            | 2.53V            |

Indicators:

* Green LED → Battery > 80%
* Yellow LED → Battery > 50%
* Red LED → Battery > 20%

This provides a simplified state-of-charge estimation method.

---

## LTspice Simulations

Simulations Performed:

* DC Sweep Analysis
* Threshold Verification
* Hysteresis Verification
* Overvoltage Detection Verification
* Battery Level Indication Verification

---

## Key Concepts Demonstrated

* Analog Circuit Design
* Voltage Divider Networks
* Comparator Circuits
* Threshold Detection
* Positive Feedback
* Hysteresis
* Battery Monitoring
* Power Management Fundamentals
* LTspice Simulation

---

## Applications

* Battery-Powered Embedded Systems
* IoT Devices
* Portable Electronics
* Industrial Monitoring Systems
* Battery Protection Circuits
* Energy Storage Systems

---

## Future Improvements

* Current Sensing using Shunt Resistor
* Overcurrent Protection
* MOSFET-Based Load Disconnect
* Microcontroller Integration
* PCB Implementation
* Battery Percentage Display

---


