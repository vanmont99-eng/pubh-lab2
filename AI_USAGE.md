# AI Usage

Model: Claude Opus 5 (claude.ai), September 2026.

**Setup and debugging.** I ran the environment setup myself and used Claude as a
reference when something broke. It caught two things I would have missed: that
the `repro-lab` env I'd tried to reuse from Lab 1 was a uv-managed venv whose
`uv.lock` I'd desync by installing into it, and that my first `python3 -m venv`
had built on macOS's bundled Python 3.9 rather than the 3.12 I assumed I had.
The empty kernel picker turned out to be missing VS Code extensions, which I
found by working through its suggestions. It recommended switching this repo to
uv for the lockfile; I stayed on pip and `requirements.txt` since the setup was
already working.

**Data source.** SOURCE.md left the URL as an open item, so I had to pick a
mirror. I asked Claude to confirm the example mirror named in that file was
still live, and it flagged that a github.com/.../blob/... link returns an HTML
page rather than the CSV, so `pd.read_csv` needs the raw.githubusercontent.com
form. I verified the load myself before writing any cells (4,240 rows, 16
columns), and decided to commit an unmodified backup since I'm depending on a
third party's repo.

**Analysis code.** Claude drafted the `pd.cut` binning and the
groupby/mean/unstack chain. I brought the question and the column names, ran the
range check that confirmed ages span 32-70 so nothing fell outside my bins, and
ran the cell counts. Two things it explained that I didn't know going in:
`pd.cut` defaults to right-closed intervals, so a 40-year-old would land in the
"30-39" bin unless you pass `right=False`; and the mean of a 0/1 column is the
incidence proportion directly, which is why `.mul(100)` gets you a percentage
without a separate count-and-divide.

**Interpretation.** Mine. Claude pointed out that the absolute and relative sex
gaps move in opposite directions across age groups, which I hadn't spotted, and
I checked it against the cell counts before writing anything — the smallest cell
is 253 men aged 30-39, so the 2.7x ratio there is the least stable figure in the
table. The wording and the limitations are my own.

**Pre-submission check and repo cleanup.** I asked Claude Code (Claude Opus 5)
to check the repo against the Lab 2 rubric. It found that my first push contained
an empty notebook because the finished version was never committed, and that the
file had been saved as `notebooks:lab2_framington.ipynb` at the repo root. A
macOS save dialog turns a `/` typed into a filename into `:`, so the file never
went into `notebooks/`. 
