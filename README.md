# Game AI Agent Comparison

This project compares four game-playing agents using win rate and average decision time. The notebook calculates a fitness score for every agent and displays the result in a bar chart.

## Requirements

- Python 3.12
- uv

Recorded and tested on 25 September 2026:

```text
uv 0.12.10 (3c979abda 2026-09-04 x86_64-pc-windows-msvc)
Python 3.12.14
```

These values were produced with:

```powershell
uv --version
uv run python --version
```

## Recreate and run the project

From the project directory, recreate the environment from the lockfile:

```powershell
uv sync --locked
```

Start JupyterLab through the project environment:

```powershell
uv run --locked jupyter lab
```

Open `notebooks/game_ai_agent_comparison.ipynb`. Select the Python interpreter from this project's `.venv` if Jupyter asks for a kernel. Then choose **Restart Kernel and Run All Cells**. Every cell should finish without an error and the chart should appear below the final cell.

## Expected result

```text
Recommended agent: Neural Agent B
Win rate: 78%
Average decision time: 8 ms
Fitness score: 74.0
```

## Project files

- `.python-version` tells uv to use Python 3.12 for this project.
- `pyproject.toml` contains the project metadata, Python requirement, runtime dependencies (`pandas` and `matplotlib`) and development dependencies (`jupyterlab` and `ipykernel`).
- `uv.lock` records the exact resolved package versions so every developer can recreate the same environment.
- `.venv` is the local environment created by uv. It contains the installed interpreter and packages, is generated from the project files and is excluded from Git.

## Troubleshooting: pandas is missing

If a teammate receives `ModuleNotFoundError: No module named 'pandas'` after cloning the repository, I would first check `python --version` and the Python executable shown by the notebook. The executable must point to this project's `.venv`. I would also check the selected Jupyter kernel and confirm that it uses the same project environment.

Next, from the repository root, I would restore the locked environment:

```powershell
uv sync --locked
```

I would restart Jupyter with `uv run --locked jupyter lab`, select the project kernel, and use **Restart Kernel and Run All Cells**. I would verify that all cells complete without errors, all four agents are displayed, and Neural Agent B is recommended with a fitness score of 74.0.
