# Playtest 1: questions and answers

Every question and report from playtest 1, the correct answer, and what was done about it.
Newest at the bottom. Status is one of: **answered**, **fixed** (with the build it shipped in),
**held** (for a later round), or **won't change** (with the reason).

---

### 1. A right answer marked wrong: `3d/dx(sin(x))` for the target 3cos(x)
**Type:** bug
**Reported:** 2026-11-25, from a tester's screenshot of a duel against Remy Mainder

**What happened:** The target was **3cos(x)**. The tester typed `3d/dx(sin(x))`, which is correct
(3 times the derivative of sin x is 3cos x), but the game said "Incorrect — that doesn't match the
target" and counted it as a wrong answer.

**Why:** The game only multiplied when you typed `*`. `3*d/dx(sin(x))` would have counted, but a
number written directly in front of something (`3d/dx(…)`, `2x`, `3cos(x)`) couldn't be read, and the
message blamed the math instead. That was unfair, especially since targets themselves are written
that way.

**Answer:** You were right. Writing things side by side now means multiplying, just like on paper:
`2x`, `3cos(x)`, `2(x+1)`, `(x+1)(x-1)` and `3d/dx(sin(x))` all work. Typing the target straight back
(`3cos(x)` for 3cos(x)) still doesn't count; build it a different way. The in-game cheat sheet
(lightbulb button) now says "2x means 2*x".

**Status:** fixed; ships in the next playtest build.

---

### 2. Is `d/dx((5+3)x³ + 2.5x² + 4x)` right for the target 5x² + 5x + 4?
**Type:** question
**Reported:** 2026-11-25, from a tester's screenshot of a duel against Remy Mainder

**What happened:** The game said "Incorrect — that doesn't match the target."

**Answer:** The game was right. (5+3) is 8, so the answer is d/dx(8x³ + 2.5x² + 4x) = **24x²** + 5x + 4,
and the target starts with **5x²**. The 5x and the 4 were spot on. The fix is one key: **(5/3)** instead
of (5+3), since 5/3 · 3x² = 5x². This counts: `d/dx((5/3)*x^3+2.5*x^2+4*x)`. (+ and ÷ sit next to each
other on the calculator, so this is an easy slip.)

**Status:** answered; no change needed.
