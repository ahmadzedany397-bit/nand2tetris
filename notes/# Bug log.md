# Bug log

Mistakes, optimizations, and lessons from the Nand2Tetris projects.

## Project 1

### Not: first draft had four errors
- **What I wrote:** `CHIP NOT`, `IN a, a;`, a Nand with pins `in1` and `in2`, and an output wire `nota` that nothing used.
- **Why it was wrong:** HDL is case-sensitive, so the chip name must match the file name (`Not`). Pins must be declared once and match the starter file (`in`, `out`). Nand's pins are `a` and `b`. The chip's output has to connect to the `OUT` pin.
- **Lesson:** use the starter file's pin names, and read the API box for each part's pin names.

### Xor: 9 Nands reduced to 4
- **First version:** 2 Ands, 2 Nots, and 1 Or, which costs 9 Nands.
- **Better version:** compute `Nand(a, b)` once and reuse it for two more Nands, then combine those with a final Nand. That is 4 Nands.
- **Lesson:** one wire can feed several part pins, so a shared intermediate result replaces duplicated gates.

### Mux: 8 Nands reduced to 4
- **First version:** two Ands feeding an Or, with a Not on `sel`.
- **Redundancy:** each And ends with a Not, and the Or begins with a Not on each input. Two Nots in a row cancel out.
- **Result:** `Nand(Nand(a, sel'), Nand(b, sel))`, which is 4 Nands.
- **Lesson:** look for back-to-back inversions after combining chips.

### DMux: needed help to find the 4-Nand version
- **First version:** 2 Ands and 1 Not (5 Nands). It works.
- **Optimized version:** `x = Nand(in, sel)`, then `b = Not(x)` and `a = And(in, x)`. This works because `in AND x = in AND sel'`.
- **How I checked it:** a four-row truth table.
- **Lesson:** a shared signal can carry information I would otherwise rebuild, like `sel'` here.

### Or8Way: miscounted the gates
- **Mistake:** I said the design used 8 Ors, but the tree has 4 + 2 + 1 = 7.
- **Rule:** combining n signals into one with two-input gates takes n - 1 gates.
- **Also:** a tree has a longest path of 3 Ors, where a chain of 7 would have 7.

### Git: push rejected (divergent branches)
- **Symptom:** `! [rejected] main -> main (fetch first)`, then `Need to specify how to reconcile divergent branches`.
- **Cause:** the remote had a commit I did not have locally.
- **Fix:** `git pull --no-rebase --no-edit`, then `git push`. No force-push.
- **Also:** `.DS_Store` showed up as untracked. Fixed with a `.gitignore` and `git rm --cached`.

## Still to do (not yet tested)

- Deliberate-break experiments: swap `sel[0]` and `sel[1]` in `Mux4Way16`, predict the failing Diff Table rows, run it, and record the result here.
- Or8Way: the provided test never sets `in[6]` or `in[7]` on its own. Test all 8 input positions by hand, and note what I find.