# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository

**GitHub:** https://github.com/Eshilnikov/experiments — общее пространство для экспериментов и проектов.

Каждый проект живёт в отдельной папке внутри репозитория (например, `tic-tac-toe/`, `restaurant-app/`). Одиночные файлы — в корне.

## Git workflow

После каждого значимого изменения:
1. `git add <файлы>`
2. `git commit -m "описание"` — сообщение на английском, кратко описывает суть изменений
3. `git push`

Для стабильных версий проектов ставить теги: `git tag v1.0 && git push --tags`

**Откат:**
- К тегу: `git checkout v1.0`
- Отмена коммита: `git revert <hash>`
- Жёсткий откат: `git reset --hard <tag/hash>`

## Git config (локальный)

```
user.name = Eshilnikov
user.email = Eshilnikov@users.noreply.github.com
```

## Current projects

### tic-tac-toe.html

Single-file browser game — standalone tic-tac-toe, no build step, no dependencies.

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
