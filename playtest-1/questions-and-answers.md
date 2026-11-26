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

