# Charger & Cable Tracker

A single-file HTML app (`index.html`, vanilla JS, no build step, no dependencies) for
tracking chargers, cables, and related hardware around the house — what exists, where it
lives, and a room-by-room stock-take to find what's gone missing. `chargers.json` is the
seed/synced data file. Hosted on GitHub Pages, deployed from `main`, added to the phone
home screen. Same pattern as the companion project `a2k-uk/tshirts`.

## Workflow: push straight to main

This is a solo personal project — just Andy and Claude iterating. **No pull requests.**
Once a change is tested and you're happy with it, commit and push directly to `main`.
Skip opening a PR, skip waiting for review or merge approval.

Still worth doing before every push:
- Run the JS through `node --check` and validate `chargers.json` as well-formed JSON.
- Smoke-test the actual UI (a headless-browser pass covering the screens touched by the
  change is worth the few minutes) rather than trusting the diff alone.
- Write a real commit message — it's the only changelog now that there's no PR history.

## One thing to watch for

`chargers.json` on `main` is also the file the live app syncs to directly via the GitHub
Contents API (once a personal access token is pasted into the Data screen) — pushes from
the live site bypass git entirely. Before pushing a commit that changes `chargers.json`'s
shape or seed content, check whether `main` has moved since your local branch was last
synced (`git log origin/main`) — if it has, real data may have been entered live and a
naive overwrite would clobber it. Diff before assuming a clean push is safe.
