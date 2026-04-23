# 2-Bit ADC using Comparators 

## Overview
This ADC is implemented using:
- 3 comparators
- A resistor voltage divider (to generate reference voltages)
- An averaged analog output:

Vout = (A + B + C) / 3

Where:
- A, B, C are comparator outputs (~1V or ~4V)

---

## 1. Behavior of the ADC

The input analog voltage (Vin) is compared against three reference voltages generated using a resistor divider:

- Vref1 = Vref / 4  
- Vref2 = Vref / 2  
- Vref3 = 3Vref / 4  

Each comparator outputs:
- HIGH if Vin > Vref  
- LOW otherwise  

| Vin Range                  | A B C |
|---------------------------|------|
| Vin < Vref/4              | 0 0 0 |
| Vref/4 ≤ Vin < Vref/2     | 0 0 1 |
| Vref/2 ≤ Vin < 3Vref/4    | 0 1 1 |
| Vin ≥ 3Vref/4             | 1 1 1 |

The output is then computed as:

Vout = (A + B + C) / 3

So:
- 000 → 1  
- 001 → 2  
- 011 → 3  
- 111 → 4  

This creates a stair
---

## 2. Resolution

The resolution of an ADC is the smallest detectable change in input voltage.

For a 2-bit ADC:

Δ = Vref / 4

This means:
- The input voltage range is divided into 4 equal levels
- Each step corresponds to one digital output level

Example (Vref = 5V):
- Resolution = 1.25V

The ADC cannot distinguish voltage changes smaller than this.

---

## 3. Output Characteristics

### (a) Quantized Output
The output is not continuous — it only takes discrete levels:
- 1
- 2
- 3
- 4

---

- The input becomes quantised

---

### (c) Effect of Input Signal

- For a **ramp input**:
  - Each level appears for equal time

- For a **sine wave input**:
  - Output stays longer at top and bottom levels
  - Basically unequal levels

---
