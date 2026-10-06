<div align="center">

  # DC from binary to Maya numerals in [Logisim Evolution](https://github.com/logisim-evolution/logisim-evolution)
  
  [How It Works](#how-it-works) • [Files](#files) • [Getting Started](#getting-started) • [License](#license)
  
  [![LinkedIn](https://img.shields.io/badge/-Alfredo%20Nader-0077B5?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjAwIiBoZWlnaHQ9IjIwMCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB2aWV3Qm94PSIwIDAgMjQgMjQiPjxwYXRoIGZpbGw9IiNmZmZmZmYiIGQ9Ik0yMC40NDcgMjAuNDUyaC0zLjU1NHYtNS41NjljMC0xLjMyOC0uMDI3LTMuMDM3LTEuODUyLTMuMDM3Yy0xLjg1MyAwLTIuMTM2IDEuNDQ1LTIuMTM2IDIuOTM5djUuNjY3SDkuMzUxVjloMy40MTR2MS41NjFoLjA0NmMuNDc3LS45IDEuNjM3LTEuODUgMy4zNy0xLjg1YzMuNjAxIDAgNC4yNjcgMi4zNyA0LjI2NyA1LjQ1NXY2LjI4NnpNNS4zMzcgNy40MzNhMi4wNiAyLjA2IDAgMCAxLTIuMDYzLTIuMDY1YTIuMDY0IDIuMDY0IDAgMSAxIDIuMDYzIDIuMDY1bTEuNzgyIDEzLjAxOUgzLjU1NVY5aDMuNTY0ek0yMi4yMjUgMEgxLjc3MUMuNzkyIDAgMCAuNzc0IDAgMS43Mjl2MjAuNTQyQzAgMjMuMjI3Ljc5MiAyNCAxLjc3MSAyNGgyMC40NTFDMjMuMiAyNCAyNCAyMy4yMjcgMjQgMjIuMjcxVjEuNzI5QzI0IC43NzQgMjMuMiAwIDIyLjIyMiAweiIvPjwvc3ZnPg==)](https://www.linkedin.com/in/alfredo-nader/)
  [![GitHub](https://img.shields.io/badge/-Freddy--Nader-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/Freddy-Nader) 
  [![Personal Website](https://img.shields.io/badge/anader.xyz-FFFFFF?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGZpbGw9Im5vbmUiIHZpZXdCb3g9IjAgMCAyNCAyNCIgc3Ryb2tlLXdpZHRoPSIxLjUiIHN0cm9rZT0iYmxhY2siIGNsYXNzPSJzaXplLTYiPgogIDxwYXRoIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIgZD0iTTEyIDIxYTkuMDA0IDkuMDA0IDAgMCAwIDguNzE2LTYuNzQ3TTEyIDIxYTkuMDA0IDkuMDA0IDAgMCAxLTguNzE2LTYuNzQ3TTEyIDIxYzIuNDg1IDAgNC41LTQuMDMgNC41LTlTMTQuNDg1IDMgMTIgM20wIDE4Yy0yLjQ4NSAwLTQuNS00LjAzLTQuNS05UzkuNTE1IDMgMTIgM20wIDBhOC45OTcgOC45OTcgMCAwIDEgNy44NDMgNC41ODJNMTIgM2E4Ljk5NyA4Ljk5NyAwIDAgMC03Ljg0MyA0LjU4Mm0xNS42ODYgMEExMS45NTMgMTEuOTUzIDAgMCAxIDEyIDEwLjVjLTIuOTk4IDAtNS43NC0xLjEtNy44NDMtMi45MThtMTUuNjg2IDBBOC45NTkgOC45NTkgMCAwIDEgMjEgMTJjMCAuNzc4LS4wOTkgMS41MzMtLjI4NCAyLjI1M20wIDBBMTcuOTE5IDE3LjkxOSAwIDAgMSAxMiAxNi41Yy0zLjE2MiAwLTYuMTMzLS44MTUtOC43MTYtMi4yNDdtMCAwQTkuMDE1IDkuMDE1IDAgMCAxIDMgMTJjMC0xLjYwNS40Mi0zLjExMyAxLjE1Ny00LjQxOCIgLz4KPC9zdmc+)](https://www.anader.xyz)

  <img src="example.png" width="512" alt="Example of the LEDs with the number 13">
</div>


A circuit that takes a 5-bit number $n$ and draws it as a Maya numeral (0 to 19) on a 4×7 LED matrix, built and simulated in Logisim-evolution.

## How It Works

The decoder is split into two subcircuits.

1. **EATER** divides $n$ by 5. The quotient $R$ is the number of full bars and the remainder $C$ is the number of loose dots.
2. **CREATOR** turns $C$ and $R$ into four 4-bit words $F_0$ to $F_3$, one per LED row, from the bottom up. Each row shows a bar, the dots or nothing. Zero is detected separately and drawn as the shell.

Inputs from 20 to 31 are not a single Maya digit, so they show the shell too.

## Files

### `maya.circ`

The final circuits. Open this one to see the project working.

| Circuit | What it is |
|---|---|
| `main` | Showcase. One input $n$ drives every version side by side: the bare LED wiring, CREATOR, the no-AI design, the ROM and the 4-bit version. |
| `EATER` | Final 5-bit EATER. |
| `EATER_noAI` | Original 5-bit EATER, factored by hand without AI. |
| `EATER_4bit` | 4-bit EATER, for inputs 0 to 15. |
| `EATER_ROM` | The whole truth table stored in a 32×16 ROM, for comparison. |
| `VARIABLES` | Box with the shared subexpressions used inside `EATER`, to save space. |
| `VARIABLES_4` | Same, for `EATER_4bit`. |
| `CREATOR` | Final CREATOR, with `EATER` inside. |
| `CREATOR_noAI` | `CREATOR` with `EATER_noAI` inside. Only used in `main`. |
| `CREATOR_4bit` | `CREATOR` with `EATER_4bit` inside. Only used in `main`. |

### `tests.circ`

Every idea tried along the way, kept to show how the design changed. The circuits from `main` to `CREATOR_4bit` are copies of the ones in `maya.circ`.

| Circuit | What it is |
|---|---|
| `MAYA_IDEA`, `LEDS` | Early ideas for the LED display. |
| `EATER_1` to `EATER_3`, `EATER_4bit_1` | Earlier versions of EATER. |
| `CREATOR_1` to `CREATOR_8` | Earlier versions of CREATOR. |
| `G4`, `G5` | Checks for whether the input is 20 or more. EATER later absorbed this logic. |

## Getting Started

Install [Logisim-evolution](https://github.com/logisim-evolution/logisim-evolution/releases) 4.1.0 or later, then

```bash
git clone https://github.com/Freddy-Nader/ac-circuits.git
```

Open `maya/maya.circ`. The `main` circuit loads first. Pick the Poke tool (the hand) and click the bits of input `n` to change the number.

This practice is also published on its own at [Freddy-Nader/maya](https://github.com/Freddy-Nader/maya).

## License

This project is open source software licensed under the MIT License. See [LICENSE](../LICENSE) for details.
