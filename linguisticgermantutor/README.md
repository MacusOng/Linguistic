# Linguistic — Macus's German Tutor

A personal AI German tutor, powered by Claude Code. This is a clone-mode install of
[**Fluent**](https://github.com/m98/fluent) by [Mohammad Kermani](https://github.com/m98)
(MIT licensed — see [LICENSE](LICENSE)), pre-configured for German and set up to run entirely
through Claude Code on the web / GitHub-connected sessions — no local desktop install required.

Because these sessions run in fresh, ephemeral containers, there's no persistent local machine
to keep state on. So unlike a typical Fluent install, **the learning data in `/data` is
committed to this repo on purpose** — it's the only thing making progress (streaks, spaced
repetition, mistake patterns) survive between sessions. Keep this repo **private**.

## How to use it

Every time you want to practice, open a Claude Code session connected to this repo (via
claude.ai/code, the GitHub integration, or any other Claude Code on the web entry point) and
type a slash command:

```
/fluent-review     # Do this first — spaced-repetition review of what you've already learned
/fluent-learn       # Main adaptive session — mixes vocab/grammar/sentences based on weak areas
/fluent-vocab       # Flashcard-style vocabulary drills
/fluent-writing     # Writing practice (emails, letters, forms) with detailed corrections
/fluent-speaking    # Typed conversation / role-play practice
/fluent-reading     # Short German texts + comprehension questions
/fluent-progress    # Stats dashboard (also auto-triggers if you just ask "how am I doing?")
```

**First time only:** setup is already done (see your profile below), so you can jump straight
into `/fluent-review` or `/fluent-learn`. If you ever want to redo onboarding — change your
level, goals, or daily time — run `/fluent-setup`.

At the end of each session, ask Claude to **commit and push** the updated `/data` and
`/results` files so your progress is saved for next time. (If you forget, just ask in your next
session — nothing is lost until you close out without pushing.)

### Recommended routine

**Daily (~20-30 min):**
```
/fluent-review    # Reinforce what's due
/fluent-learn     # New material, adapted to your weak spots
```

**A couple times a week:** swap in `/fluent-speaking` or `/fluent-writing` for focused practice.

**Weekly:** `/fluent-progress` to see trends and celebrate wins.

## Your profile

- **Target language:** German (starting at A1)
- **Native / working language:** English (also fluent in Mandarin, Taiwanese Hokkien,
  Malay/Indonesian, Hainanese, Cantonese; basic Vietnamese and Thai)
- **Goals:** general fluency + conversational confidence
- **Daily time:** ~20-30 minutes

Edit `data/learner-profile.json` directly, or run `/fluent-setup`, if any of this needs to change.

## How it works

- **Evidence-based methodology:** active recall, SM-2 spaced repetition, immediate feedback,
  interleaving, comprehensible input (i+1), desirable difficulty (60-70% target success rate).
  Full details in [`LEARNING_SYSTEM.md`](LEARNING_SYSTEM.md).
- **6 JSON databases** in `/data` track your profile, overall progress, error patterns, mastery
  levels (0-5 ⭐), the spaced-repetition review queue, and full session history.
- **12 Claude Code skills** in `.claude/skills/` implement each command above, plus shared
  helpers (SM-2 math, feedback formatting, DB updates, session analysis).
- **Hooks** in `.claude/hooks/` auto-backup and validate the JSON databases on every write.
- Session write-ups land in `/results/` as `{skill}-session-{ID}.md` files.

See [`AGENTS.md`](AGENTS.md) for the full architecture reference (also usable with other AI
CLIs, e.g. Codex or Gemini, if you ever want to run this outside Claude Code).

## Credits

Built on [m98/fluent](https://github.com/m98/fluent) — MIT License. All teaching methodology,
skills, and hooks originate there; this repo is a personalized, German-focused deployment with
data persisted in git instead of gitignored.
