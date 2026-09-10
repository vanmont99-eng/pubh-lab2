# PUBH 4201 Lab 2: 10-year CHD risk by age and sex (Framingham)

## Data
Loaded at runtime from its original source via URL in the first code cell of
the notebook — not from a local or hand-cleaned copy.

SOURCE.md left the load URL as an open item, so I pinned the example mirror it
names:
https://raw.githubusercontent.com/GauravPadawe/Framingham-Heart-Study/master/framingham.csv

Because that mirror is a third party's repo, I also committed an unmodified
backup at data/raw/framingham_backup.csv. The notebook does not read that file;
it exists only in case the mirror moves.

## How to re-run
1. python3 -m venv .venv && source .venv/bin/activate
2. pip install -r requirements.txt
3. Open notebooks/lab2_framingham.ipynb and choose "Restart & Run All"

Headless, from the repo root:
jupyter nbconvert --to html --execute notebooks/lab2_framingham.ipynb

Built on Python 3.12.14.

## Contents
- notebooks/lab2_framingham.ipynb — analysis notebook
- notebooks/lab2_framingham.html — rendered export
- data/raw/framingham_backup.csv — unmodified backup (not used by the notebook)
- requirements.txt
- AI_USAGE.md
