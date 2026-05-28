# Project Conventions

This is an **nbdev3** project. **Notebooks in `nbs/` are the source of truth.**

## Rules

- **Never edit `.py` files in `hello_claude/` directly** — they are auto-generated.
- All code changes happen in `nbs/*.ipynb` notebooks.
- After editing a notebook, run `nbdev-prepare` to sync modules, run tests,
  clean notebooks, and update `README.md`.
- New public functions need:
  - A docstring on the first line
  - The `#| export` directive at the top of the cell
  - At least one test cell with `assert` statements directly below
- Use `#| hide` for cells that shouldn't appear in docs.
- Commit messages follow Conventional Commits: `feat:`, `fix:`, `docs:`, `test:`, `refactor:`.

## Workflow for fixing an issue

1. Read the issue carefully.
2. Identify the notebook in `nbs/` that owns the relevant module.
3. Edit the notebook (not the `.py` file).
4. Add or update test cells in the same notebook.
5. Run `nbdev-prepare` and confirm tests pass.
6. Commit on a new branch named `claude/<issue-number>-<short-slug>`.
7. Open a PR referencing the issue with `Fixes #<number>`.

## Useful commands

- `nbdev-export` — notebooks → .py modules
- `nbdev-test` — run all notebook-based tests
- `nbdev-clean` — strip metadata from notebooks
- `nbdev-prepare` — all of the above plus README sync
- `nbdev-preview` — local docs preview (not needed in CI)