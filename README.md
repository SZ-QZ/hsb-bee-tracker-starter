# HSB Bee Tracker (Software)

This repository is the software baseline for tracking bee movement and producing metrics for our team.

## Objective (Semester)
Build an easy-to-use system that analyzes bee videos and saves results for the team.

## Current Status
- **Phase 1 (KR1): Notebook transfer (starter baseline)** ✅ in progress
- Phase 2 (KR2): Database integration
- Phase 3 (KR3): Live analysis pipeline

## What we inherited / reviewed
Reference repo: https://github.com/ecstacide/bee-tracker  
We use it as a baseline idea and code reference.

## Folder structure
- `notebooks/` : Jupyter notebook(s) (demo + experiments)
- `src/` : reusable Python code (will grow over the semester)
- `outputs/` : generated results (CSV / plots / logs)
- `docs/` : notes, roadmap, data format, troubleshooting

## Inputs
- Bee video files (NOT stored in GitHub if large)
- Place local test videos in a folder like `data/` (gitignored)

## Outputs (baseline)
- A metrics result file (example: `outputs/metrics.csv`)
- Optional: plots or logs

**Output format goal (for KR2):**
We will keep output columns stable so they can be inserted into the database later.

## Setup (baseline)
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -U pip
pip install -r requirements.txt
pip install jupyter
