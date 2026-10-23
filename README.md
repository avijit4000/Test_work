# Test_work

A small personal repository for **data science learning and Pandas practice**, maintained by [Avijit Biswas (@avijit4000)](https://github.com/avijit4000).

The repository is intentionally minimal: it contains one hands-on Jupyter notebook that walks through core Pandas operations (loading, inspecting, summarising, grouping, filtering, slicing, and plotting data), a GitHub profile page, and two placeholder files used as scratch space.

- **Remote:** <https://github.com/avijit4000/Test_work>
- **Default branch:** `main`
- **Primary language:** Python (Jupyter Notebook)

<!-- LAST-UPDATED:START -->**Last updated:** 2026-10-23 (IST)<!-- LAST-UPDATED:END -->

> A Windows scheduled task (`GitDailyGreeter`) rewrites the date above and appends a greeting to the
> [Daily Check-in Log](#daily-check-in-log) every morning at **08:00 IST**, then commits and pushes it.

---

## Table of Contents

- [Repository Overview](#repository-overview)
- [Repository Structure](#repository-structure)
- [File Reference](#file-reference)
- [Pandas_intro.ipynb — Walkthrough](#pandas_introipynb--walkthrough)
- [Requirements](#requirements)
- [Getting Started](#getting-started)
- [Daily Automation — GitDailyGreeter.exe](#daily-automation--gitdailygreeterexe)
- [Project Status and Known Limitations](#project-status-and-known-limitations)
- [Daily Check-in Log](#daily-check-in-log)
- [Author](#author)
- [License](#license)

---

## Repository Overview

| Item | Details |
| --- | --- |
| Purpose | Educational / learning sandbox for data analysis with Pandas |
| Project type | Notebook-based exploration — not a packaged application |
| Total tracked files | 8 |
| Notebooks | 2 (`Pandas_intro.ipynb`, `jeow.ipynb`) |
| Top-level scripts | `daily_update.py` (automation), `build.ps1` (build) |
| Source packages / modules | None |
| Build system | PyInstaller for the automation executable |
| Tests | None |
| CI/CD | None |
| License | None specified |

This is a **flat repository** — there are no subdirectories, no `src/`, no `tests/`, and no configuration files such as `requirements.txt`, `package.json`, or `pyproject.toml`.

---

## Repository Structure

```
Test_work/
├── avijitbiswas.md       # GitHub profile README (personal introduction, links, skills)
├── Pandas_intro.ipynb    # Pandas tutorial notebook — the main content of this repo
├── jeow.ipynb            # Empty notebook (placeholder, 0 bytes)
├── file                  # Plain-text scratch file ("this is ok.")
├── README.md             # This document
├── daily_update.py       # Daily README updater + Task Scheduler installer
├── build.ps1             # Builds dist\GitDailyGreeter.exe with PyInstaller
├── .gitignore            # Ignores build artefacts and virtual environments
└── dist/                 # Build output (git-ignored)
    └── GitDailyGreeter.exe
```

---

## File Reference

### `Pandas_intro.ipynb`

The core artifact of the repository. A Jupyter notebook (49 cells, all code cells — no Markdown documentation cells) that performs exploratory data analysis on a salary dataset using **Pandas** and **Matplotlib**.

- Notebook metadata: `kernelspec` = `Python 3 (ipykernel)`, `language_info.version` = `3.8.5`
- Imports: `pandas`, `matplotlib.pyplot`
- Expected input file: `Salaries.csv` (loaded with `pd.read_csv('Salaries.csv')`)

> **Note:** `Salaries.csv` is **not** included in this repository, so the notebook will not run end-to-end until you supply the file yourself and place it in the repository root (or update the path in the second cell).

### `avijitbiswas.md`

A GitHub profile README describing the author:

- Master of Data Science, IIT Ropar & IIM Amritsar alumnus
- Badges and links for Twitter/X, LinkedIn, Stack Overflow, Kaggle, Facebook, Instagram, YouTube, and LeetCode
- A technology badge grid covering Python, Pandas, TensorFlow, PyTorch, scikit-learn, Seaborn, Matplotlib, OpenCV, MATLAB, Django, Flask, HTML/CSS, Docker, Kubernetes, Linux, Git, AWS, Azure, GCP, Hadoop, MongoDB, MySQL, PostgreSQL, SQL Server, SQLite, Arduino, and Illustrator
- GitHub stats, streak, top-languages, and trophy widgets

### `jeow.ipynb`

A completely empty notebook kept as a placeholder for future experiments.

### `file`

A one-line plain-text scratch file containing `this is ok.` — not used by any code.

### `daily_update.py` and `build.ps1`

The automation behind the daily README update — see
[Daily Automation — GitDailyGreeter.exe](#daily-automation--gitdailygreeterexe) for behaviour,
commands and build steps. `daily_update.py` is plain standard-library Python (3.9+) and needs no
third-party packages at runtime.

---

## Pandas_intro.ipynb — Walkthrough

The notebook proceeds from basic inspection to aggregation and visualisation, in this order:

| Section | Cells | Operations demonstrated |
| --- | --- | --- |
| Setup | 0 | `import pandas as pd` |
| Load data | 1 | `df = pd.read_csv('Salaries.csv')` |
| Inspect structure | 2–7 | `df.head()`, `df.tail(10)`, `df.columns`, `df.dtypes`, `df.describe()` |
| Descriptive statistics | 8–13 | `df.max()`, `df.min()`, `df.mean()`, `df.std()`, `df.describe()` |
| Categorical counts | 11 | `df.discipline.value_counts()` |
| Subset of rows | 14–17 | `df_50 = df.head(50)` and statistics on the subset |
| Column access | 18–22 | Attribute access `df.salary`, bracket access `df['salary']`, DataFrame slice `df[['salary']]` |
| Series statistics | 23–25 | `df.phd.describe()`, `df.phd.count()`, `df.phd.mean()` |
| Value counts on rank | 27 | `df['rank'].value_counts()` |
| Grouping / aggregation | 28–32 | `groupby(['discipline','rank']).mean()`, `groupby(['discipline','sex']).mean()`, `groupby('rank')[['salary','phd']].mean()` |
| Boolean filtering | 33, 43 | `df[df.salary > 120000]`, `df[(df['sex']=='Male') & (df['salary']<100000)]` |
| Positional indexing | 36–41, 44 | `df.iloc[0:4, 2:5]`, `df.iloc[0:10, 0:3]`, `df.iloc[[3,4], 1:5]`, `df.iloc[22, 4:6]` |
| Label-based indexing | 42 | `df.loc[0:4, ['rank','discipline']]` |
| Visualisation | 45 | `df['sex'].value_counts().plot.bar()` |
| Visualisation with labels | 46 | `df.groupby(['rank']).mean()` → `g['salary'].plot(kind='bar')`, annotated with `plt.bar_label(container)` |
| Scratch cells | 47–48 | `print("Avijit")` and an empty cell |

### Key concepts covered

1. **Loading CSV data** into a DataFrame.
2. **Exploring shape and schema** via `head`, `tail`, `columns`, and `dtypes`.
3. **Summary statistics** — mean, max, min, standard deviation, and the `describe()` report.
4. **Series vs. DataFrame access** — dot notation versus bracket notation, and the difference between `df['salary']` (Series) and `df[['salary']]` (DataFrame).
5. **`value_counts()`** for frequency analysis of categorical columns such as `discipline`, `rank`, and `sex`.
6. **`groupby` aggregation** across one or more keys (`discipline`, `rank`, `sex`).
7. **Boolean masking** with single and combined conditions (`&`).
8. **`iloc` for positional indexing** and **`loc` for label-based indexing**, including mixed row/column slices.
9. **Plotting with Matplotlib** through Pandas' `.plot()` accessor — bar charts, plus value labels on grouped bars.

### Typical cell usage

```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('Salaries.csv')

# Structure and summary
df.head()
df.dtypes
df.describe()

# Frequency of a categorical column
df['rank'].value_counts()

# Aggregation by one or multiple keys
df.groupby('rank')[['salary', 'phd']].mean()
df.groupby(['discipline', 'sex']).mean()

# Filtering
df[(df['sex'] == 'Male') & (df['salary'] < 100000)]

# Positional and label-based slicing
df.iloc[0:10, 0:3]
df.loc[0:4, ['rank', 'discipline']]

# Visualisation
df['sex'].value_counts().plot.bar()
g = df.groupby(['rank']).mean()
ax = g['salary'].plot(kind='bar')
for container in ax.containers:
    plt.bar_label(container)
plt.show()
```

---

## Requirements

There is no dependency manifest in the repository. The notebook relies on the following third-party libraries:

| Package | Role |
| --- | --- |
| `pandas` | Data loading and manipulation |
| `matplotlib` | Bar chart rendering |
| `jupyter` / `ipykernel` | Notebook execution environment (Python 3.8+ recommended, matching the notebook metadata) |

Install them with:

```bash
pip install pandas matplotlib jupyter
```

### Expected input data

`Salaries.csv` must exist in the same directory as the notebook. The notebook references the following columns:

- `rank` — academic rank (categorical)
- `discipline` — academic discipline (categorical)
- `sex` — gender (categorical)
- `salary` — numeric salary
- `phd` — numeric, years since PhD

---

## Getting Started

1. **Clone the repository**

   ```bash
   git clone https://github.com/avijit4000/Test_work.git
   cd Test_work
   ```

2. **Create an environment and install dependencies**

   ```bash
   python -m venv .venv
   # Windows
   .venv\Scripts\activate
   # macOS / Linux
   source .venv/bin/activate

   pip install pandas matplotlib jupyter
   ```

3. **Add the dataset**

   Place `Salaries.csv` in the repository root (it is not tracked here).

4. **Launch Jupyter and open the notebook**

   ```bash
   jupyter notebook Pandas_intro.ipynb
   ```

5. **Run the cells** top to bottom, or use *Run All*.

### Common commands

| Task | Command |
| --- | --- |
| Install dependencies | `pip install pandas matplotlib jupyter` |
| Start Jupyter Notebook | `jupyter notebook` |
| Start JupyterLab | `jupyter lab` |
| Open the tutorial directly | `jupyter notebook Pandas_intro.ipynb` |
| Run as a script (optional) | `jupyter nbconvert --to script Pandas_intro.ipynb` |

The notebook itself has **no** build, lint, or test commands. The automation component in this
repository is compiled with `build.ps1` — see the next section.

---

## Daily Automation — GitDailyGreeter.exe

`GitDailyGreeter.exe` is a small Windows utility that keeps this README alive. A Windows Task
Scheduler entry runs it **every day at 08:00 IST**; the program then:

1. Rewrites the `Last updated` stamp at the top of this README with the current IST date.
2. Inserts a new row at the top of the [Daily Check-in Log](#daily-check-in-log) containing the date
   and a *Good morning* greeting.
3. Runs `git pull --rebase --autostash`, commits **only** `README.md`, and pushes to `origin`.

Re-running it on the same day is safe: the log row is replaced, not duplicated, and no commit is
created when nothing changed.

### Files

| File | Purpose |
| --- | --- |
| `daily_update.py` | Source of the utility — README stamping, git push, task installation |
| `build.ps1` | Builds the standalone executable into `dist\GitDailyGreeter.exe` |
| `dist\GitDailyGreeter.exe` | Compiled executable (not tracked by git) |

### Install

Build the executable first (see [Building the executable](#building-the-executable)), then run:

```powershell
.\dist\GitDailyGreeter.exe --install --repo "d:\Work\test_softeare"
```

`--install` performs three actions:

1. Copies the executable to `%LOCALAPPDATA%\GitDailyGreeter\GitDailyGreeter.exe`, so the scheduled
   task keeps working even if the repository folder is moved or `dist\` is cleaned.
2. Writes `%LOCALAPPDATA%\GitDailyGreeter\config.json` with the repository path, branch and time.
3. Registers the Task Scheduler entry **GitDailyGreeter** (`Daily`, 08:00 IST) for the current user,
   with *Start when available* enabled so a missed run happens as soon as the PC wakes up.

Add `--run-now` to push the first update immediately after installing:

```powershell
.\dist\GitDailyGreeter.exe --install --repo "d:\Work\test_softeare" --run-now
```

### Commands

| Command | What it does |
| --- | --- |
| `GitDailyGreeter.exe --install [--repo PATH] [--time 08:00] [--run-now]` | Installs the utility and registers the daily task |
| `GitDailyGreeter.exe --uninstall` | Removes the scheduled task and the stored config |
| `GitDailyGreeter.exe --status` | Shows config, task state, last/next run and last log lines |
| `GitDailyGreeter.exe --run` | Performs one update + commit + push (used by the task) |
| `GitDailyGreeter.exe --run --dry-run` | Updates `README.md` locally without committing or pushing |
| `GitDailyGreeter.exe --help` | Prints usage |

### Logs and troubleshooting

- Every run appends to `%LOCALAPPDATA%\GitDailyGreeter\logs\YYYY-MM.log`.
- `--status` prints the last run result reported by Task Scheduler.
- The push needs cached GitHub credentials (Git Credential Manager) for the account that owns the
  task. Run `git push` once manually if the push step starts failing with authentication errors.
- The task runs under the signed-in user, so the machine must be on and the user logged in for the
  push to happen; *Start when available* covers missed runs after a shutdown.
- On a machine that is **not** set to IST, `--install` converts 08:00 IST into the equivalent local
  clock time automatically (for example 02:30 on a UTC machine) and prints the resolved time.

### Building the executable

```powershell
pip install pyinstaller
.\build.ps1
```

or manually:

```powershell
pyinstaller --onefile --name GitDailyGreeter --clean daily_update.py
```

The result is `dist\GitDailyGreeter.exe` — a single self-contained file with no Python dependency.

---

## Project Status and Known Limitations

- **Learning sandbox:** the repository has no application entry point, no packaging, and no automated tests.
- **Missing dataset:** `Salaries.csv` is referenced by `Pandas_intro.ipynb` but is not committed, so the notebook cannot execute as-is.
- **Empty placeholder:** `jeow.ipynb` contains no cells.
- **Scratch file:** `file` is unused plain text left in the repository root.
- **No dependency pinning:** library versions are not declared, so results may vary across Pandas/Matplotlib releases.
- **Undocumented cells:** the notebook contains only code cells — there is no narrative Markdown between steps.
- **No CI:** no GitHub Actions or other pipelines are configured.
- **Automation dependency:** the daily README update relies on a local Windows scheduled task and on
  valid git credentials; it is not part of a CI pipeline.

---

## Daily Check-in Log

Each morning at 08:00 IST the scheduled task adds one row below, newest first. The table is
maintained automatically — edit it by hand only if you also keep it consistent with the script.

<!-- DAILY-LOG:START -->
| Date (IST) | Greeting |
| --- | --- |
| 2026-10-23 | Good morning! Today is Friday, 23 October 2026. |
| 2026-10-22 | Good morning! Today is Thursday, 22 October 2026. |
| 2026-10-21 | Good morning! Today is Wednesday, 21 October 2026. |
| 2026-10-20 | Good morning! Today is Tuesday, 20 October 2026. |
| 2026-10-19 | Good morning! Today is Monday, 19 October 2026. |
<!-- DAILY-LOG:END -->

---

## Author

**Avijit Biswas** — Master of Data Science, IIT Ropar & IIM Amritsar

- GitHub: [@avijit4000](https://github.com/avijit4000)
- LinkedIn: [avijit-biswas4000](https://www.linkedin.com/in/avijit-biswas4000/)
- Kaggle: [avijitbiswas01](https://www.kaggle.com/avijitbiswas01)
- Stack Overflow: [avijit-biswas](https://stackoverflow.com/users/19789991/avijit-biswas)
- LeetCode: [avijit4000](https://leetcode.com/avijit4000/)

---

## License

No license file is included in this repository, so the contents are protected by default copyright. If you intend to reuse this code, please contact the author for permission.
