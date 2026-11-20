# Poteto Playbook Quest

A small game that explains each `/poteto-mode` playbook from [pstack](https://github.com/cursor/plugins/tree/main/pstack) for learners. Pick a level and watch the potato walk through the steps.

Play it at https://georgeroberts1.github.io/poteto-playbook-quest/. It is also linked from [AI Stuff](https://georgeroberts1.github.io/ai-stuff/), a collection of my AI projects.

Turn on **CS mode** on the home screen for a harder version aimed at computer science students. Each playbook gets a CS lens (a real concept such as Amdahl's law or topological sort, with code), an order-the-steps puzzle, and a harder boss question.

```text
npm start    # serves docs/ at http://localhost:8000
npm test     # one test per playbook, checked against the real playbook files
```

The page is static files in `docs/`, so GitHub Pages can serve it directly (Settings, Pages, source GitHub Actions, which the workflow needs).

The tests read the installed pstack plugin from `~/.claude/plugins/cache/cursor-plugins/pstack`. Set `POTETO_PLAYBOOKS` to point at another copy of the `playbooks/` folder.

CI (`.github/workflows/ci.yml`) runs the tests on every PR and push, and weekly to catch upstream playbook changes. Pushes to `main` deploy `docs/` to GitHub Pages only when the tests pass. In CI the tests check out `cursor/plugins` and set `POTETO_PLAYBOOKS` to its playbooks.
