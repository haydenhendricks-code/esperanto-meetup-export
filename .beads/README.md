# br (beads_rust) - local-first issue tracking

This repository uses **br** for issue tracking — a local-first,
SQLite+JSONL issue tracker with no background daemon. Migrated from `bd`
(Go/Dolt) on 2026-08-25; old bd/Dolt state is archived under
`.beads/legacy-bd-dolt-backup-2026-08-25/`, moved not deleted.

## Quick Start

```bash
br ready              # Find available work
br show <issue-id>    # View issue details
br create "title"      # Create a new issue
br update <issue-id> --claim   # Claim work
br close <issue-id>    # Complete work
```

Run `br robot-docs guide` for the full workflow reference (br's closest
equivalent to bd's `prime`; br has no `prime` subcommand).

## Architecture in one line

Issues live in a local SQLite DB (`.beads/beads.db`); `.beads/issues.jsonl`
is br's own JSONL export (kept current on every mutating command,
gitignored here). `br` never runs git itself (unlike bd's Dolt-backed
auto-push) — there is no cross-machine sync mechanism for this repo's
tracker today.

**Learn more:** https://github.com/Dicklesworthstone/beads_rust
