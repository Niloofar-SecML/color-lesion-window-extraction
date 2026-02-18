# Copilot / AI Agent Instructions

This repository is a small research utility: "color-lesion-window-extraction".
Primary intent (from README): parametric window extraction (odd N: 5,7,9,...) and RGB min/max/avg feature computation for the PH2 dataset.

Keep guidance brief, concrete, and tied to the repository scope.

What this project does (big picture)
- Extract fixed-size square windows around lesion regions (parametric odd sizes N).
- Compute simple per-window color features: per-channel min, max, and average (RGB).
- Target dataset referenced: PH2 (dermatology lesion images).

Key files to consult or update
- README.md — project purpose and short description.
- LICENSE — project's license.
- .gitignore — repository ignore rules.

Immediate priorities for the agent
- If adding implementation code, keep it minimal and self-contained. Provide a single-module reference implementation first (e.g., `window_extraction.py` or `src/window_extraction.py`).
- Implement two focused functions as the canonical API:
  - `extract_windows(image, center, N) -> List[ndarray]` — return N×N windows (handle borders via padding).
  - `compute_rgb_features(window) -> Dict[str,float]` — return keys like `r_min`, `r_max`, `r_mean`, `g_min`, ...
- Include short doctests or small unit tests that validate behavior on synthetic arrays.

Conventions and expectations
- Use clear, minimal dependencies. If using Python, prefer `numpy` and `opencv`/`Pillow` only.
- Parameter `N` is always an odd integer; code should assert or normalize this.
- Border handling: prefer symmetric padding so center pixels remain aligned.
- Name new modules under `src/` if repository grows; tests under `tests/`.

Developer workflows (what an agent should assume)
- There are currently no build or test scripts in the repo. Before adding CI or test runners, confirm with the repo owner.
- For quick verification, run small Python scripts or pytest on added `tests/`.

Examples to follow (copy into code or tests)
- Example `compute_rgb_features` output shape: `{'r_min':0,'r_max':255,'r_mean':123.4,'g_min':...}`
- Example assertion for odd `N`: `assert N%2==1, "N must be odd"`

When to open PRs vs. asking questions
- If change is small and unambiguous (add single module + tests + README update), open a PR.
- If the change introduces a new build system, dataset download, or alters repository layout, ask the maintainer first.

If something is missing
- The README is minimal — ask the user for preferred language, test runner, and dataset placement before scaffolding.

Contact / follow-up
- After creating initial implementation, run a small self-test and attach the test output in the PR description.

---
Small, concrete, and repo-focused — expand only after maintainer confirmation.
