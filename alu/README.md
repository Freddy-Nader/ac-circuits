<div align="center">

# 8-bit ALU

<img src="example.png" width="512" alt="The ALU circuit with its eight operations, the result multiplexer, the flags and the comparisons">
</div>

An arithmetic logic unit for two 8-bit numbers `A` and `B`. A 3-bit code `Op` picks one of eight operations, and the
circuit also shows the flags `Z`, `N`, `C` and how `A` compares with `B`.

## How It Works

1. Every operation runs at the same time, one row per code, and an 8-input multiplexer lets the chosen one through to `R`.

   | Op | Operation | | Op | Operation |
   |---|---|---|---|---|
   | 000 | NOT A | | 100 | A AND B |
   | 001 | A NAND B | | 101 | A XOR B |
   | 010 | A − B | | 110 | A + B |
   | 011 | A NOR B | | 111 | A OR B |

2. **XOR** (subcircuit `XOR`) is built from its truth table with AND, OR and NOT gates, $\bar{b}a + b\bar{a}$, with no XOR gate.
3. **Flags.** `Z` is 1 when `R` is zero (an 8-input NOR), `N` is the sign bit `R7`, and `C` is the carry of `A + B` or the
   borrow of `A − B`. A second multiplexer on `Op` makes `C` 0 for the logic operations.
4. **Comparisons** (unsigned) come from the subtractor, which is always on, so they are valid for every `Op`. With
   `Zs` = "A − B is zero" and `Bo` = borrow: `EQ = Zs`, `NE = ¬Zs`, `LT = Bo`, `GE = ¬Bo`, `GT = ¬(Bo + Zs)`,
   `LE = Bo + Zs`.

## Files

| File | What it is |
|---|---|
| `alu.circ` | Circuits `ALU` (main, inputs `A[8]`, `B[8]`, `Op[3]`) and `XOR`. |
| `vectors.txt` | Logisim test vector for `ALU`, 320 cases: every pair of 0, 1, 127, 128, 255 plus 15 random pairs, for all eight codes. |

## Getting Started

Open `alu/alu.circ` in Logisim-evolution 4.1.0 or later. Pick the Poke tool (the hand) and click the bits of `A`, `B`
and `Op`. To run the test, go to Simulate → Test Vector and load `vectors.txt`.
