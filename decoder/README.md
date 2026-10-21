<div align="center">

  # Decoders with enable

</div>

Binary decoders (DC) with an enable input, built from the smallest one up: 1 to 2, 2 to 4, 3 to 8 and 4 to 16 lines.

## How It Works

`DC1` is a 1-to-2 decoder with enable $E$, $y_0 = E\,\overline{x_0}$ and $y_1 = E\,x_0$, two AND gates. Each bigger decoder uses one `DC1` on its most significant bit to choose which of two smaller decoders is enabled, and those decode the remaining bits.

1. `DC2` (2 to 4) = three `DC1`.
2. `DC3` (3 to 8) = one `DC1` and two `DC2`, 14 AND gates.
3. `DC4` (4 to 16) = one `DC1` and two `DC3`, 30 AND gates.

## Files

### [`DC.circ`](DC.circ)

| Circuit | What it is |
|---|---|
| `main` | Empty. Open the decoders directly. |
| `DC1` | 1-to-2 decoder with enable. |
| `DC2` | 2-to-4 decoder with enable. |
| `DC3` | 3-to-8 decoder with enable. |
| `DC4` | 4-to-16 decoder with enable. |

## Getting Started

Open `decoder/DC.circ` in Logisim-evolution 4.1.0 or later and pick `DC4` (or any smaller one) from the circuit list. With the Poke tool (the hand), set the enable to 1 and click the input bits. Exactly one output turns on.
