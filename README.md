# ECE 225A Study Notes: Probability

Personal study repository for ECE 225A at UC San Diego, taught by Alon Orlitsky. The course builds probability from first principles and uses it as the foundation for statistics and data science. This repo starts with the **Probability Review** module, split into five sessions. Each session has a runnable notebook, a set of practice problems to solve by hand for midterm and final prep, worked solutions, and a one-page cheatsheet.

## Sessions

### Module 01: Probability Review

| Session | Topics |
|---|---|
| [01 Probability basics](module-01-probability-review/session-01-probability-basics/) | Sample spaces, events, equiprobable spaces, counting with cards and poker hands |
| [02 Conditional probability and independence](module-01-probability-review/session-02-conditional-probability-independence/) | Set operations, conditional probability, independence (pairs and three events), product and chain rule, sequential selection, birthday paradox |
| [03 Bayes, random variables, expectation](module-01-probability-review/session-03-bayes-random-variables-expectation/) | Law of total probability, Bayes' rule, random variables, PMF and CDF, expectation, tail sums, LOTUS, linearity, indicator method |
| [04 Variance, covariance, joint distributions](module-01-probability-review/session-04-variance-covariance-joint/) | Variance and standard deviation, affine transformations, joint distributions, covariance, independent vs uncorrelated, variance of sums, correlation coefficient |
| [05 Distribution families](module-01-probability-review/session-05-distribution-families/) | Bernoulli, binomial, Poisson, geometric, continuous distributions (PDF, CDF, expectation), functions of continuous random variables |

Each session folder contains:

| File | Purpose |
|---|---|
| `notes.ipynb` | Concepts with intuition, definitions, worked examples, and Python checks (exact or simulation) |
| `exercises.md` | 12 exam-style problems (warm-up, exam-level, challenge) to solve by hand |
| `solutions.md` | Full worked solutions with exact and decimal answers |
| `cheatsheet.md` | One-page summary of formulas, tools, and common traps |

Suggested workflow: read the notebook, attempt the exercises closed-book, check against the solutions, then review the cheatsheet before the exam.

## Setup

Requires Python 3.10 or newer (developed with 3.11).

```bash
python -m venv .venv

# Windows (PowerShell)
.venv\Scripts\Activate.ps1
# macOS / Linux
source .venv/bin/activate

pip install -r requirements.txt
```

## Running the notebooks

Open them interactively:

```bash
jupyter lab
```

Or re-execute a notebook from the command line and save its outputs:

```bash
jupyter nbconvert --to notebook --execute --inplace module-01-probability-review/session-01-probability-basics/notes.ipynb
```

All simulations use a fixed seed, so results are reproducible.

## About this material

The original lecture slides are not included in this repository. All notes, exercises, solutions, and cheatsheets are my own study material, written in my own words from the lectures.
