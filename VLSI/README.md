# 8-bit CMOS ALU — VLSI Design Project

A full-custom **8-bit CMOS Arithmetic Logic Unit (ALU)** designed and characterized as part of an Introduction to VLSI project. The design was developed hierarchically in Cadence, from transistor-level building blocks to a complete 8-bit datapath, and verified through schematic simulation, layout, DRC, and LVS.

## Project Highlights

- Full-custom CMOS implementation of an 8-bit ALU
- Modular hierarchy based on a verified 1-bit ALU slice
- Clock-controlled input latches for synchronized operands
- Ripple-carry arithmetic datapath across eight slices
- Schematic, symbol, and layout views for reusable blocks
- Functional simulation of arithmetic and bitwise logic operations
- DRC/LVS verification of the complete layout
- Timing analysis including rise time, fall time, and propagation delay

## Supported Operations

The operation is selected by the 3-bit control signal `S2 S1 S0`:

| S2 | S1 | S0 | Operation |
|:--:|:--:|:--:|:--|
| 0 | 0 | 0 | `A + B` |
| 0 | 0 | 1 | `A - 1` |
| 0 | 1 | 0 | `A - B` |
| 0 | 1 | 1 | `A + 1` |
| 1 | 0 | 0 | `A XOR B` |
| 1 | 0 | 1 | `A NOR B` |
| 1 | 1 | 0 | `A NAND B` |
| 1 | 1 | 1 | `NOT A` |

Subtraction uses two's-complement arithmetic. The carry-out of each slice is connected to the carry-in of the next slice, while the initial carry-in is configured according to the selected arithmetic operation.

## Architecture

```text
A[7:0], B[7:0]
       |
Input latches controlled by CLK
       |
+------+------+------+------+------+------+------+------+
| ALU0 | ALU1 | ALU2 | ALU3 | ALU4 | ALU5 | ALU6 | ALU7 |
+------+------+------+------+------+------+------+------+
   |      |      |      |      |      |      |      |
   +------ ripple-carry arithmetic path -----------+
       |
      Y[7:0]
```

Each 1-bit slice contains:

- Arithmetic block: operand-selection MUX and full adder
- Logic block: XOR, NOR, NAND, and inverter functions
- Output selection between arithmetic and logic results
- Input synchronization latch and buffer

## Technology and Tools

- **Design domain:** VLSI / CMOS digital IC design
- **Design style:** Full-custom, hierarchical transistor-level design
- **EDA:** Cadence design tools
- **Verification:** Schematic simulation, Design Rule Check (DRC), Layout Versus Schematic (LVS)
- **Analysis:** Functional waveforms, rise time, fall time, and propagation delay

## Reported Design Results

| Metric | Result |
|:--|:--|
| ALU width | 8 bits |
| Layout width | `101.56 µm` |
| Layout height | `71.2 µm` |
| Calculated layout area | approximately `7,231.07 µm²` (`0.007231 mm²`) |
| Reported transistor count | `784` |
| DRC | 0 markers reported |
| LVS | Schematic/layout connectivity match reported |

The report includes the timing plots and functional waveforms for all eight operations. Exact numeric timing values should be added here when the original Cadence measurements are available in machine-readable form.

## Repository Contents

- [`VLSI-report.pdf`](./VLSI-report.pdf) — formatted project report
- [`VLSI-report.docx`](./VLSI-report.docx) — editable report source

## Engineering Skills Demonstrated

- CMOS digital circuit design
- Hierarchical VLSI architecture and reusable cell design
- Transistor-level schematic development
- Full-custom physical layout
- Ripple-carry arithmetic design
- Clock-controlled data synchronization
- Functional and timing simulation
- DRC/LVS-based physical verification
- Technical documentation and design analysis

## Scope

This is an academic VLSI design and characterization project. It demonstrates the design flow and verification of a CMOS datapath; it is not a fabricated silicon prototype.

## Authors

- Abed elhady abu ahmed
- Titiana Abu shkara
- Ameer Lawen
