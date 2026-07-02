# Foundation House Capital — Executive Operating System (v2)

The single-file command center for the Foundation Phase (2026–2029), rebuilt around the FHC/Atlas Executive Brief. Atlas exists to reduce cognitive load, improve decision quality, and increase stewardship — not to become another productivity app. This dashboard obeys the brief's final instruction: every module exists to simplify a real recurring decision or preserve a lesson.

**The objective is not to build Atlas yet — it is to become the man capable of building Atlas.**

## Files

```
/atlas-dashboard/
  index.html        ← the OS shell (rarely edited)
  data.json         ← ALL content — this is what you edit
  sync_data.py      ← run after editing data.json (keeps the file:// fallback in sync)
  README.md         ← this file
  seed-artifacts/   ← starting files for the repo's governance folders
    wrong-about/WRONG_ABOUT.md
    decision-journal/2026-07.md
```

## Recommended repo placement (auditability architecture)

GitHub is truth. Drive is presentation. Every meaningful decision produces a committed artifact.

```
FlowStateMacro/
├── atlas-dashboard/          ← this folder
├── governing-documents/      ← FHC Constitution, Editorial Constitution, Steward's Curriculum
├── decision-journal/         ← one markdown file per month  ← seed provided
├── ceo-letters/              ← one markdown file per week (2026-W27.md ...)
├── wrong-about/              ← WRONG_ABOUT.md               ← seed provided
├── council/                  ← charter, advisor evaluations, relationship notes
├── opportunities/            ← one file per live opportunity
├── knowledge-vault/          ← book notes — a book without notes doesn't count as read
├── atlas/  FHC/  content/  Journals/  Archives/   (existing)
├── DRIVE_INDEX.md
└── SCRATCH.md
```

Move the two `seed-artifacts/` folders to the repo root (so they become `/wrong-about/` and `/decision-journal/`) on first commit.

Drive mirror (for the CPA, attorneys, and Council-facing material): `Foundation House Capital / 00 Governing Documents · 01 Bookkeeping · 02 Council · 03 Allocation Memos · 04 Knowledge · 05 Archive`. Keep `DRIVE_INDEX.md` current whenever a canonical document moves.

## The tabs, in the order that matters

1. **Overview** — phase, readiness, bottleneck, statuses. Read first.
2. **Philosophy** — the chain (Source → Stewardship → FHC → Atlas → FSM → Assets → Impact) and the Final Instruction, displayed as design law.
3. **Priorities** — the only three things: Ship Episode 1, FHC financial infrastructure, daily deep work. Interactive checklists.
4. **Deep Work** — the 3.5 hr/day grid (Bookkeeping 60 / FSM 60 / Coding 60 / Reading 30), tracked per week with a live hours counter.
5. **Gates** — the capability gate ladder, Gate 0 → VI.
6. **Exec Systems** — KPIs, Anti-Goals, **Decision Journal**, Opportunity Pipeline, Relationship Capital, Knowledge Vault, **Weekly CEO Letter**, Return Matrix.
7. **Wrong About** — the permanent "Things I Was Wrong About" ledger.
8. **Weekly Review** — the Sunday ritual; feeds the CEO Letter and the two ledgers.
9. Intelligence, Council, Projects, Documents, Timeline, Risks, Repo & Drive, Sovereign Base, AI Team — supporting boards.

## The auditability loop (how entries reach GitHub)

The Decision Journal, Opportunity Pipeline, Relationship Capital, Wrong About ledger, and CEO Letter are all **editable in the browser** and saved to localStorage on your device. Each has a **"Copy as Markdown"** button that produces a commit-ready document with its destination path printed at the top. The loop:

1. Log the entry in the dashboard the moment it happens.
2. Sunday review: Copy as Markdown → paste into the corresponding repo file → commit.
3. localStorage is the scratchpad; **GitHub is the record.** If it isn't in the repo, it doesn't exist.

Also use **Export Snapshot** weekly — it downloads a JSON of all editable state (deep work grid, checklists, entries) you can commit for a complete history.

## Updating content

Edit **`data.json`** (plain JSON, one key per tab), then run:

```
python3 sync_data.py
```

That refreshes the copy embedded inside `index.html` so the dashboard shows identical data whether it's served (GitHub Pages / local server → loads `data.json` directly) or double-clicked from the file system (browsers block local fetch, so the embedded fallback is used). The footer always shows which source is active. Commit both files together.

To view with live `data.json` loading: `python3 -m http.server 8000` in this folder → `http://localhost:8000`, or enable GitHub Pages on the repo.

## Weekly operating rhythm (Sunday anchor)

1. Perplexity intelligence pull (ATLAS + FSM reports)
2. Update `data.json`: signal/noise, gate progress, KPIs, statuses → `sync_data.py`
3. Weekly Review tab → honest answers
4. CEO Letter → Copy as Markdown → commit to `/ceo-letters/`
5. Copy any new Decision Journal / Wrong About entries to their repo files
6. Export Snapshot, commit everything

## Backlog

GitHub Pages deployment · weekly report parser feeding data.json · CSV paper-trade import · bookkeeping export integration.
