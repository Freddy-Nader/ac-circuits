<div align="center">

  # Binary adders

</div>

Ripple-carry adders of 1, 2, 4 and 8 bits, built by doubling, plus a 2-bit adder synthesized directly from Karnaugh maps. The half adder computes the XOR from AND, OR and NOT gates, $s = \overline{a}\,b + a\overline{b}$.

## How It Works

1. The half adder gives $s = a \oplus b$ and $c = ab$.
2. The full adder is two half adders and an OR gate on their carries.
3. Each bigger adder chains two adders of half its width, with the carry out of the low half going into the high half.

## Files

### [`sum.circ`](sum.circ)

| Circuit | What it is |
|---|---|
| `main` | Empty. Open the adders directly. |
| `semi` | Half adder without an XOR gate (3 AND-type gates and 1 OR). |
| `sum_1bit` | Full adder, two `semi` and an OR gate. |
| `sum_2bit`, `sum_4bit`, `sum_8bit` | Ripple-carry adders of 2, 4 and 8 bits, each one two copies of the previous width. |
| `sum_4c1` | 4-bit ripple-carry adder from four `sum_1bit`. |
| `sum_2` | 2-bit adder synthesized from Karnaugh maps (11 AND, 3 OR). |
| `sum_4bit_2` | Copy of `sum_4bit`. |
| `pruebas` | 8-bit test bench. |

### [`sum_classic.circ`](sum_classic.circ)

The same adders drawn with Logisim's classic appearance and labeled pins: `HA_1bit`, `FA_1bit`, `FA_2bit`, `FA_4bit`, `FA_8bit`, `sum_4c1` and `sum_2`. It also holds `pruebas` (test bench), `resta` (subtractor, unfinished) and `predictor` (pins only).

### [`suma.circ`](suma.circ)

A single `main` with a half adder and two 2-bit adders.

## Getting Started

Open `sum/sum.circ` in Logisim-evolution 4.1.0 or later and pick an adder from the circuit list. With the Poke tool (the hand), click the input bits to change $a$, $b$ and the carry in.
