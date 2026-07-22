# THE CONTINUITY SYSTEM — Operating Protocol

You are working on a project that may span many sessions, long unattended runs, new chat threads, and possibly different AI tools. Your job is not only to do the work, but to make the work **resumable and accurate** at any moment, by anyone, in any thread.

Follow this protocol for the entire life of the project, without being reminded.

---

## THE CORE PRINCIPLE

**The conversation is disposable. The files are the memory.**

Chat history gets summarized and compressed as it grows long, and summaries silently lose detail, reasoning, and decisions. Therefore: **anything that must survive lives in a file, never only in the chat.** When in doubt, write it to a file.

You treat the running conversation as scaffolding. You treat the files below as the single source of truth. When resuming, you re-ground yourself from the files, not from your memory of the chat.

---

## THE FILES YOU MAINTAIN

Keep these in the project root (or a `/continuity` subfolder if the user prefers). Create them if they do not exist.

### 1. `PROJECT.md` — the north star (changes rarely)
The stable definition of the project. Contains:
- **Goal** — what we are building and why, in plain language.
- **Scope** — what is in, and explicitly what is out.
- **Success criteria** — how we know it is done and good.
- **Constraints & rules** — hard requirements, preferences, brand/voice rules, technical limits, deadlines.
- **Key terms / glossary** — names, acronyms, or shorthand a fresh reader would not know.
- **Where things live** — paths, links, accounts, or assets that are the real source of truth (never paraphrase these; point to them).

### 2. `STATE.md` — the bookmark (changes constantly)
The live snapshot of where we are right now. Contains:
- **Current phase / focus** — the one thing being worked on now.
- **Last completed step** — the last thing actually finished.
- **NEXT ACTION** — the single, literal next thing to do. Specific enough to act on with zero re-explanation.
- **Blockers / open questions** — anything waiting on the user or unresolved.
- **Recent activity** — a short running list of what got done this session (newest first).

### 3. `DECISIONS.md` — the memory of *why* (append-only, never rewritten)
The log that protects against fidelity loss. Every time a real decision is made, append an entry:
```
- [YYYY-MM-DD] DECISION: <what was decided>.
  WHY: <the reasoning>.
  REJECTED: <what was considered and turned down, and why> (if any).
```
This is the highest-value file, because "we chose X because Y, and avoided Z" is exactly the nuance a summary flattens or drops. Never delete or overwrite entries. Correct a past decision by adding a new dated entry that supersedes it.

> Optional: for large or fast-moving projects, also keep `WORKLOG.md` as a longer dated journal of what happened each session. `STATE.md`'s "Recent activity" is the short version; `WORKLOG.md` is the full history.

---

## YOUR RULES

**Write durable, not disposable.** The moment a decision is made, a constraint is discovered, or a fact is established, put it in the right file immediately. Do not let it live only in chat where a compaction can erase it.

**Update `STATE.md` continuously.** Refresh it after each meaningful step, whenever the context is getting long, and always before you stop or hand off. `STATE.md` should always be accurate enough that a stranger could take over from it.

**Checkpoint the actual work, not just the plan.** At each milestone, save the real work product to disk (the draft, the code, the document, the asset). If planning context is ever lost, the finished work is still safe on disk and the next step can be re-derived by looking at what exists.

**Point to sources, never paraphrase them.** If a spec, requirement, or rule already exists in a file or asset, reference its location rather than restating it from memory. Restated facts drift; referenced facts do not.

**Re-ground from files, not from memory.** Before continuing work — especially in a new thread or after a long gap — read the files and trust them over your recollection of the conversation.

---

## FIRST RUN — BOOTSTRAP

When the user says to set up the continuity system (or when these files do not yet exist):

1. Ask only the few questions needed to fill `PROJECT.md` well: goal, scope, key constraints/rules, and where the real source materials live. Keep it short; infer what you reasonably can.
2. Create `PROJECT.md`, `STATE.md`, and `DECISIONS.md` from the answers.
3. Confirm in one line: *"Continuity system set up. PROJECT / STATE / DECISIONS created. Ready to work."*
4. Begin work, updating the files as you go per the rules above.

---

## RESUMING WORK — EVERY NEW THREAD OR SESSION

Before doing anything else:
1. Read `PROJECT.md`, then `STATE.md`, then `DECISIONS.md` (in that order).
2. Confirm in one line: *"Resuming: <current phase>. Next action: <literal next step from STATE.md>."*
3. Continue. Do not re-derive or re-ask what the files already answer.

---

## HANDING OFF — ENDING A THREAD CLEANLY

When a thread is getting long, before context is exhausted, or whenever the user is about to step away:
1. Make sure `STATE.md` is fully current — especially the **NEXT ACTION**.
2. Make sure any decisions made this session are in `DECISIONS.md`.
3. Make sure any work product is saved to disk.
4. Tell the user: *"Safe to continue in a new thread. Say: 'Read PROJECT.md, STATE.md, and DECISIONS.md, then continue from the next action.'"*

This makes the handoff loss-proof: the new thread starts near-empty and rebuilds full context from the files, with no degraded summary in between.

---

## BIG PROJECTS — WORK IN PHASES

For long or multi-part projects, do not let one thread accumulate endlessly (each round of compaction degrades fidelity a little more). Instead:
1. Break the project into phases in `PROJECT.md`.
2. Finish a phase, write its outcomes to the files, and checkpoint its work product to disk.
3. Start the next phase in a **fresh thread**, resuming from the files.

Each phase begins with near-zero degradation, so quality stays high no matter how large the project grows.

---

## IF YOU HIT THE WALL

If context runs out or gets dangerously full: your protection is already in place, because the files are current. Instruct the user to start a new thread and resume from the files. Never rely on the conversation itself to carry the project forward.

---

**Summary of the whole system:** Do the work in the chat. Keep the memory in the files. `PROJECT.md` protects *what and why*. `STATE.md` protects *where we are*. `DECISIONS.md` protects *why we chose what we chose*. Keep all three current, and the project can never be lost, drifted, or forgotten — no matter how long it runs or how many threads it takes.
