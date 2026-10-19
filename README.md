# Test_work

A small personal repository for **data science learning and Pandas practice**, maintained by [Avijit Biswas (@avijit4000)](https://github.com/avijit4000).

The repository is intentionally minimal: it contains one hands-on Jupyter notebook that walks through core Pandas operations (loading, inspecting, summarising, grouping, filtering, slicing, and plotting data), a GitHub profile page, and two placeholder files used as scratch space.

- **Remote:** <https://github.com/avijit4000/Test_work>
- **Default branch:** `main`
- **Primary language:** Python (Jupyter Notebook)

---

## Table of Contents

- [Repository Overview](#repository-overview)
- [Repository Structure](#repository-structure)
- [File Reference](#file-reference)
- [Pandas_intro.ipynb — Walkthrough](#pandas_introipynb--walkthrough)
- [Requirements](#requirements)
- [Getting Started](#getting-started)
- [Project Status and Known Limitations](#project-status-and-known-limitations)
- [Author](#author)
- [License](#license)

---

## Repository Overview

| Item | Details |
| --- | --- |
| Purpose | Educational / learning sandbox for data analysis with Pandas |
| Project type | Notebook-based exploration — not a packaged application |
| Total tracked files | 4 |
| Notebooks | 2 (`Pandas_intro.ipynb`, `jeow.ipynb`) |
| Source packages / modules | None |
| Build system | None |
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
└── README.md             # This document
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

There are **no** build, lint, or test commands in this repository.

---

## Project Status and Known Limitations

- **Learning sandbox:** the repository has no application entry point, no packaging, and no automated tests.
- **Missing dataset:** `Salaries.csv` is referenced by `Pandas_intro.ipynb` but is not committed, so the notebook cannot execute as-is.
- **Empty placeholder:** `jeow.ipynb` contains no cells.
- **Scratch file:** `file` is unused plain text left in the repository root.
- **No dependency pinning:** library versions are not declared, so results may vary across Pandas/Matplotlib releases.
- **Undocumented cells:** the notebook contains only code cells — there is no narrative Markdown between steps.
- **No CI:** no GitHub Actions or other pipelines are configured.

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
