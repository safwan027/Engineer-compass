# 🧭 Engineer Compass — Claude Skill

A Claude skill that acts as a **senior engineer co-pilot** — automatically sensing when you're in an unplanned exploration spiral and steering you toward production-grade thinking before the mess sets in.

---

## What it does

- **Auto-detects** vibe coding, scope creep, and dopamine-driven rabbit holes
- **Gives direction** — not just more information
- **Teaches proactively** — every response includes the underlying engineering principle + a fast-recall anchor
- **Systems thinking** — surfaces feedback loops, emergence, and leverage points on production-bound work
- **Attention signaling** — marks the single highest-stakes moment per response with `▶ Don't miss this`
- **Compass Artifact** — on demand, generates a fully editable session document: goal, decisions, architecture, principles learned, traps, next actions

---

## Install

### Claude.ai users
1. Download `engineer-compass.skill` from the [Releases](../../releases) page
2. Go to **Settings → Skills → Install from file**
3. Upload the file — done

### Developers (system prompt / agent projects)
Clone or copy the folder into your project:

```
your-project/
└── .claude/
    └── skills/
        └── engineer-compass/
            ├── SKILL.md
            └── references/
                └── principles.md
```

Then reference `SKILL.md` in your Claude system prompt or agent context.

---

## Contents

| File | Purpose |
|---|---|
| `SKILL.md` | Core skill — behaviors, triggers, artifact format |
| `references/principles.md` | ~30 software engineering principles with anchors for fast recall |

---

## The Compass Artifact

When you say *"capture this"*, *"make a compass"*, or *"save this session"* — Claude generates an editable artifact with:

- 🎯 The actual goal (stripped of detours)
- 🗺 What was explored
- ⚓ Decisions made + tradeoffs accepted
- 🧱 Architecture / structure
- 🔺 Principles learned with anchors
- ⚠️ Traps identified
- 📋 Next actions
- 🔗 References

---

## Contributing

PRs welcome — especially new principles with strong anchors, or improved system dynamics references.
