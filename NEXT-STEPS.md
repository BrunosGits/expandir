# Expandir — Next Steps

Working plan for the `expandir` repo itself. The master 5-month roadmap and infra
phases live in `~/ai-lab/roadmap.md`; this file is the concrete sprint plan that
sits next to the code and gets updated with each milestone.

## Current state (2026-08-16)

- Repo: **public** on GitHub, default branch `dev`, no open issues
- `dev` = upstream espanso `dev` (v2.4.0 era) + personalized README
- **No fork-specific code committed yet.** The README's only "Working" feature
  (`search_use_cursor_position`) does not exist in the tree — it is aspirational.
- Goal of this phase (roadmap Month 1): *Rust fundamentals + espanso internals*,
  ending in a published milestone on GitHub.

## 0. Fork hygiene — do before feature work

- [ ] Add upstream remote: `git remote add upstream https://github.com/espanso/espanso.git`
- [ ] Decide the branch strategy and write it down (recommendation below)
- [ ] Verify clean build on the VPS: `cargo build` from a fresh `target/` (note time + disk)

**Recommended branch strategy** (solo learner, keep it simple):

- `dev` stays **pure upstream + README**, so upstream merges never fight our code.
  Keep it rebased onto `upstream/dev` periodically.
- Fork work happens on short feature branches (`feat/<name>`), merged to `dev`
  only at milestone publish time.
- Every milestone ends with a tag: `expandir-0.x.0`.

## 1. Sprint A — Month 1: Rust fundamentals + espanso internals

1. [ ] Build from source on the VPS; note the toolchain (`rust-toolchain.toml`) and
      first-build duration. This is the "does my box actually compile this" gate.
2. [ ] Map the workspace: read `espanso-core` (types/config), `espanso-match`
      (matcher engine), `espanso-inject` (keyboard injection), `espanso-engine`
      (orchestration/daemon), `espanso-detect` (context detection).
      → Write `docs/fork/espanso-map.md` (crate → responsibility → key entry points).
3. [ ] "Hello world" module in Rust: a standalone crate that logs keypresses
      (esp. the roadmap Month 1 build). Use a small lib (e.g. `rdev`/`enigo`) —
      keep it **outside the espanso crates** so it compiles fast and stands alone.
      Put it under `scripts/keylog/`.
4. [ ] Implement `search_use_cursor_position` for real (macOS first — the README
      already claims it works, so make the claim true):
      - Find where the search window is positioned (likely `espanso-ui`)
      - Add the config key + schema entry (config parsing lives in `espanso-config`)
      - Position the window at the cursor when the option is set
      - Test on macOS; note Windows/Linux as pending in README
5. [ ] Publish the milestone:
      - Commit feature + docs; merge to `dev`; tag `expandir-0.1.0`
      - Journal entry + ROADMAP update (`~/ai-lab/roadmap.md`, Month 1 boxes)

## 2. Sprint B — Month 2 preview (from master roadmap)

- Study: `espanso-config`, `espanso-package`, YAML parsing
- Build: load custom match files from a directory + hot-reload of match files
- TOML config support (optional)
- Publish: repo + journal entry + roadmap update

## 3. Feature backlog (README "Planned")

Prioritized smallest-first; pick the next one after Sprint A.

- [ ] **Clipboard history + searchable UI** ← next after Sprint A
- [ ] Temporary copy/paste hotspots (register slots)
- [ ] AI snippet authoring assistant (needs Month 4 ML skills — later)
- [ ] Settings panel (GUI for config toggles)
- [ ] Match editor GUI

## Notes

- All work happens on the VPS (`~/expandir`); nothing project-related lives on the
  local computer.
- Every milestone = code + journal entry + roadmap update + a tag. No silent work.
