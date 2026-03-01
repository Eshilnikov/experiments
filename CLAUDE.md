# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-file browser game: `tic-tac-toe.html` — a standalone tic-tac-toe implementation with no build step, no dependencies, and no package manager.

**To run:** open `tic-tac-toe.html` directly in a browser.

## Architecture

Everything lives in one HTML file with three sections:

- **CSS** (lines 7–165): dark-themed UI, grid layout, animations
- **HTML** (lines 167–206): static board markup, score display, mode toggle buttons
- **JavaScript** (lines 208–349): game logic, Minimax AI, score tracking

**Game state** is managed with plain module-level variables (`board`, `current`, `gameOver`, `mode`, `scores`). No framework, no modules.

**AI** uses unoptimized Minimax (exhaustive search, no alpha-beta pruning) — acceptable for a 3×3 board.

**Modes:** Player vs Player (`pvp`) and Player vs AI (`ai`, human is always X, AI is O).

## Key notes

- The `checkWinnerBoard` function destructures `WINS` combos as `[a, c, d]` — the middle variable name is `c` (not `b`) which is intentional (avoids shadowing the board parameter `b`).
- Score state is in-memory only; refreshing the page resets scores.
- UI language is Russian.
