# AGENTS.md

Guidance for agents in `hidden-lodge-sim`. See [README.md](README.md) for setup, config schemas, and commands.

## Structure

- Python SimulationCraft runners: `droptimizer.py` (single character), `guild_droptimizer.py` (guild), `website_sim_runner.py` (website API integration).
- `webapp.py` is the Flask runner service; `website_sim_runner_gui.py` is the Tkinter GUI. Inspect `requirements.txt` before adding dependencies.
- PowerShell scripts update SimC, run jobs, register scheduled tasks, and build/deploy the GUI executable.
- `config*.json` select SimC, profiles, candidate pools, output directories, and per-spec mappings. `generated/`, `results/`, and `tools/` are generated or external data; inspect `.gitignore` before staging.

## Conventions

- Repository and source directory: `jmusick/hidden-lodge-sim`, `C:/Users/JD/source/hidden-lodge-sim`. Prefer paths relative to the script/config or caller-supplied paths over another hardcoded checkout.
- Keep existing local config edits and credentials intact. Never print or commit real API keys. Update examples when changing a config field.
- Candidate mappings use `class:spec` keys. Preserve strict raid/boss mapping and current tier-token source overrides.
- The website contract is documented in [the website README](https://github.com/jmusick/hidden-lodge-website/blob/main/README.md) and implemented in its `src/lib/sim-api.ts` and `src/pages/api/sim/`. Check both ends before changing payloads or auth headers.
- Existing `LodgeSim` executable names, user-agent strings, and `X-LodgeSim-Key` are runtime names/contracts; a repository rename does not rename them.
- Validate Python syntax for changed modules; use a small local fixture for scoring/config changes before starting expensive sims. Do not launch a guild-wide production run as a smoke test.
- Maintain setup/implementation docs here. The Obsidian project note is an index plus personal context.
