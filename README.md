# Nand2Tetris: building a computer from NAND gates

My work through *The Elements of Computing Systems* (Nisan and Schocken), alongside my computer engineering studies at the Technion. The goal is to understand a computer from the bottom up, from a single NAND gate to a CPU, assembler, and compiler, and to practise reading and debugging low-level designs.

## How I work

1. Design each chip on paper before opening the simulator.
2. Implement it in HDL and test it in the Nand2Tetris hardware simulator.
3. Look for redundancy once it works (shared signals, back-to-back Nots).
4. Break it on purpose, predict the result, and record it in the bug log.

## Tools

- Nand2Tetris web IDE (Hardware Simulator)
- VS Code for editing `.hdl` files
- Git and GitHub

## Progress

| Project | Topic | Status |
|---|---|---|
| 1 | Boolean logic (15 chips) | Done |
| 2 | Boolean arithmetic (adders, ALU) | Not started |
| 3 | Sequential logic | Not started |
| 4 | Machine language | Not started |
| 5 | Computer architecture | Not started |
| 6 | Assembler | Not started |

## Project 1 chips

Not, And, Or, Xor, Mux, DMux, Not16, And16, Or16, Mux16, Or8Way, Mux4Way16, Mux8Way16, DMux4Way, DMux8Way.

Nand counts for the elementary gates: Not 1, And 2, Or 3, Xor 4, Mux 4, DMux 4.

## Repo layout

- `projects/1/`: HDL files for Project 1
- `notes/bug-log.md`: mistakes, experiments, and what I learned