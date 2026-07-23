# Multi-AI Project Template

Copy this whole folder to start a project you'll work on across **more than one AI app** (e.g. Claude and Codex), when different apps handle different components. It keeps the Continuity System benefits **and** prevents the two apps from overwriting each other's work.

> If a project only ever uses **one** app, you don't need this — just let the normal three files (PROJECT / STATE / DECISIONS) get created in the folder. Use this template only when two apps are involved.

---

## The one rule that prevents overwrites

**Each mutable file has exactly one owner.** Two apps never write the same file. That's the whole trick. Here's how the folders enforce it:

```
your-project/
├── PROJECT.md        ← shared north star. READ by both. Edited rarely, by ONE app.
├── DECISIONS.md      ← shared decision log. APPEND-ONLY (both can add lines safely).
├── claude/           ← Claude's workspace. Claude owns everything in here.
│   └── STATE.md      ← Claude's current focus + next action.
├── codex/            ← Codex's workspace. Codex owns everything in here.
│   └── STATE.md      ← Codex's current focus + next action.
└── shared/           ← FINISHED artifacts both apps read. Hand off completed work here.
```

- **`PROJECT.md`** — the goal/scope/rules for the whole project. Both apps read it; only edit it occasionally, and let one app "own" edits so it's never a tug-of-war.
- **`DECISIONS.md`** — append-only, so both apps adding entries won't clobber each other. Never rewrite past entries.
- **`claude/` and `codex/`** — each app works inside its own folder, including its own `STATE.md`. Because they're separate files, simultaneous work is safe.
- **`shared/`** — when a component is *finished*, drop the deliverable here for the other app to use. Treat it as read-only for whoever didn't produce it.

---

## How to use it

1. **Copy this folder** and rename it to your project.
2. Fill in **`PROJECT.md`** (goal, scope, who's doing what).
3. Decide **which app owns which component** and note it in `PROJECT.md` (e.g. "Claude: copy + content. Codex: build + code.").
4. In each app, point it at its own folder. Tell it: *"This is a multi-AI project. You own the `claude/` folder (or `codex/`). Read PROJECT.md and DECISIONS.md, keep your own STATE.md current, and only put finished work in `shared/`. Do not edit the other app's folder."*
5. When you hand a finished piece over, move it into `shared/` and note it in `DECISIONS.md`.

---

## Strongly recommended: put it under git

Git is the real safety net — it makes an overwrite **impossible to lose**:

```bash
cd your-project
git init
git add -A
git commit -m "start project"
```

Then every change is versioned and visible; nothing is ever silently lost. If you ever *do* want two apps working the same files at the same time, give each its own branch (`git switch -c claude-work` / `git switch -c codex-work`) and merge deliberately. You already have `git` set up.

---

## Quick reference: which situation are you in?

| Situation | What to do |
|---|---|
| One project, one app | Don't use this. Normal 3 files in the folder. |
| Two different projects, one in each app | Separate folders. No conflict possible. Don't need this. |
| One project, components split across apps | **Use this template.** One folder per app + shared north star + git. |
| Two apps on the *same* files at the *same* time | Use this template **and** a git branch per app. |
