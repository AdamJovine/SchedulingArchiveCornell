## Overview
This repository contains datasets accompanying the paper "Cornell University Uses Integer Programming to Optimize Final Exam Scheduling".

Use these data to reproduce or benchmark exam timetabling models, compare objective trade-offs (conflicts, back-to-backs, 2-in-3s, etc.), and analyze solution quality.

## Repository structure
- `cornell/`: anonymized inputs for Spring 2024 at Cornell University
- `nottingham/`: schedules produced by our algorithms on the University of Nottingham benchmark dataset (see the dataset homepage at [nottingham dataset link](https://people.cs.nott.ac.uk/pszrq/data.htm))

## Data dictionaries

### Cornell inputs (`cornell/`)
- `exam_sizes.csv`
  - **exam**: anonymized exam identifier (integer)
  - **size**: number of students registered for the exam

- `p_co.csv`
  - Square, symmetric matrix where rows and columns are exam identifiers
  - Entry `(i, j)` gives the number of students co-enrolled in exams `i` and `j` (pairwise conflicts)
  - The diagonal is zero

- `t_co.csv`
  - Columns: **a**, **b**, **c**, **co**
  - Each row lists a triple of exams `(a, b, c)` and the number **co** of students simultaneously enrolled in all three
  - Useful for modeling objectives/constraints that penalize metrics involving triplets of exams

### Nottingham outputs (`nottingham/`)
Each CSV corresponds to a schedule our algorithms produced for a particular instance/parameterization of the University of Nottingham dataset (e.g., `23a`, `23b`, `26a`, `26b`).

Common columns:
- **exam**: exam/course identifier
- **Exam Block**: block index used by the benchmark instance (often corresponds to a day or session group)
- **slot**: timeslot index within the instance
- **size**: number of students registered for the exam
- **b2bs**: count of back-to-back occurrences involving this exam in the assigned solution
- **confs**: count of hard conflicts (should be zero in feasible schedules)
- **2i3s**: count of “2 exams in 3 slots” occurrences involving this exam
- **score**: per-exam contribution to the objective value in our runs
- **score_norm**: normalized version of the score for easier comparison across exams

## Citation
If you use these data, please cite:

```
@article{ye2024cornell,
  title={Cornell University Uses Integer Programming to Optimize Final Exam Scheduling},
  author={Ye, Tinghan and Jovine, Adam and van Osselaer, Willem and Zhu, Qihan and Shmoys, David},
  journal={arXiv preprint arXiv:2409.04959},
  year={2024}
}
```

## Acknowledgments
- University of Nottingham dataset: see the official description at the [nottingham dataset link](https://people.cs.nott.ac.uk/pszrq/data.htm).
