# HSB Bee Tracker (Software)

This repo contains the starter workflow for analyzing bee videos and exporting outputs (CSV metrics / optional plots).
If you are not a CS major: no worries — follow the steps below exactly. If something fails, check **Common issues & fixes**.

---

## What this repo is for
- Open a bee video (`.mp4`)
- Run the analysis notebook end-to-end
- Export results to `outputs/` (CSV / plots / logs)

---

## Project folder overview (what’s what)
- `notebooks/`  
  Jupyter notebooks (demo + experiments). This is what most teammates run.
- `data/`  
  **LOCAL videos only** (ignored by git). Put `.mp4` files here.
- `outputs/`  
  Generated results (CSV / plots / logs). Safe to commit **small** CSVs if needed.
- `.venv/`  
  Your local Python environment (ignored by git).

### About `.gitkeep`
Git does not track empty folders. A `.gitkeep` file is a tiny placeholder so folders like `data/` and `outputs/` still appear in the repo even when empty.

---

## What you need (one-time setup)

### 1) Install VS Code
Install **Visual Studio Code**.

Recommended VS Code extensions (install inside VS Code):
- **Python** (by Microsoft)
- **Jupyter** (by Microsoft)

### 2) Install Python (required)
Install **Python 3.10+** (3.11 / 3.12 recommended).

Verify Python works:
```bash
python --version
```

If `python` doesn’t work, try:
```bash
python3 --version
```

**Windows note:** During Python install, make sure you check **“Add Python to PATH”**.

### 3) Install Git (required)
Install Git so you can clone and pull updates.

Verify Git:
```bash
git --version
```

---

## Quick start (run the notebook end-to-end)

### 1) Clone this repo
Open VS Code → Terminal (or any terminal), then run:
```bash
git clone https://github.com/YOUR_ORG/YOUR_REPO.git
cd hsb-bee-tracker-starter
```

> Replace `YOUR_ORG/YOUR_REPO` with your real GitHub path.

---

### 2) Create a virtual environment (recommended)
This creates an isolated Python environment for this project:
```bash
python -m venv .venv
```

If that fails, try:
```bash
python3 -m venv .venv
```

---

### 3) Activate the environment
You must activate the environment **every time** before installing/running.

**Windows (PowerShell):**
```powershell
.\.venv\Scripts\Activate.ps1
```

**Windows (Command Prompt / cmd):**
```bat
.\.venv\Scripts\activate.bat
```

**macOS / Linux:**
```bash
source .venv/bin/activate
```

✅ After activation, your terminal usually shows something like `(.venv)` at the left.

---

### 4) Install dependencies (packages)

First upgrade pip:
```bash
python -m pip install --upgrade pip
```

Then install project dependencies:

**Option A (recommended):** if this repo has `requirements.txt`, run:
```bash
python -m pip install -r requirements.txt
```

**Option B:** if `requirements.txt` does NOT exist yet, run this once:
```bash
python -m pip install numpy pandas matplotlib opencv-python jupyter ipykernel
```

(Optional but recommended) After installing, you can create `requirements.txt` for the team:
```bash
pip freeze > requirements.txt
```

---

### 5) Register the Jupyter kernel (so VS Code runs notebooks in this environment)
```bash
python -m ipykernel install --user --name hsb-bee-tracker --display-name "HSB Bee Tracker (.venv)"
```

---

### 6) Add the input video (LOCAL ONLY)
Large videos are **NOT** stored in GitHub.

Put your `.mp4` file here:
```
data/<your_video>.mp4
```

Example:
```
data/2024-10-25_1848.mp4
```

The `data/` folder is intentionally ignored by git (so videos won’t be uploaded).


### How to change the video used in the notebook

After you put your `.mp4` file in the `data/` folder, open:

```text
notebooks/beeTracker_backsub.ipynb

Find the video input line near the top of the notebook.
```
Example:
```
in1 = cv.VideoCapture('../data/2024-10-25_1848.mp4')
```
Replace the old file name with your own file name.

Example:
```
in1 = cv.VideoCapture('../data/my_video.mp4')
```
Make sure:

1. your file is inside the data/ folder

2. the file name matches exactly

3. the file ends with .mp4

---

### 7) Run the notebook in VS Code
1. In VS Code, open the notebook:
   ```
   notebooks/beeTracker_backsub.ipynb
   ```
2. Top-right of the notebook, click **Select Kernel**
3. Choose:
   - `HSB Bee Tracker (.venv)` (preferred), OR
   - the Python interpreter that points to `.venv`
4. Click **Run All** (or run cells from top to bottom)

---

### 8) Check outputs
Outputs should appear in:
```
outputs/
```

Common outputs include CSV files (metrics/telemetry) and optional logs/plots.

---

## Team workflow (how not to break the repo)

### Pull updates (recommended before you start working)
```bash
git pull
```

### What you should commit
- Notebook changes (`.ipynb`) only if needed (prefer clean notebooks)
- Python code (`src/`)
- Small output CSVs if the team wants to share them
- `requirements.txt` and README updates

### What you should NOT commit
- Videos (`data/*.mp4`)
- Your virtual environment (`.venv/`)
- Huge generated files (large plots / caches)

If you need to share videos, use Google Drive / OneDrive and paste the link.

---

## Common issues & fixes

### 1) `python` command not found / “python is not recognized”
Try:
```bash
python3 --version
```

If you are on Windows, reinstall Python and check **Add Python to PATH**.

---

### 2) `pip` not found or installs to the wrong Python
Always use:
```bash
python -m pip install --upgrade pip
python -m pip install <package>
```

This guarantees `pip` matches the same Python you’re running.

---

### 3) Notebook imports fail (example: `ModuleNotFoundError: cv2`)
This usually means VS Code is using the **wrong kernel**.

Fix:
1. Make sure the terminal shows `(.venv)` (environment activated)
2. In the notebook: **Select Kernel** → pick `HSB Bee Tracker (.venv)` (or `.venv`)
3. Reinstall dependencies inside `.venv`:
   ```bash
   python -m pip install opencv-python
   ```
4. Restart the notebook kernel:
   - In VS Code notebook toolbar: **Restart** then **Run All**

---

### 4) VS Code can’t see your `.venv`
- Make sure you created `.venv` in the repo root (same folder as README).
- In VS Code:
  - `Cmd+Shift+P` (Mac) / `Ctrl+Shift+P` (Windows)
  - Search: **Python: Select Interpreter**
  - Choose the interpreter inside `.venv`

---

## FAQ

### Q: Do I need to run steps 2–5 every time?
No. Steps 2, 4, 5 are usually one-time.
But you **must activate** `.venv` (step 3) every time you open a new terminal before running.

### Q: Where do I change which video is used?
Inside the notebook, there is usually a variable/path like:
- `video_path = "data/xxx.mp4"`
Update it to your file name.

---

## Contact / Help
If you get stuck, post:
- A screenshot of the error
- Your OS (Windows/macOS)
- The output of:
  ```bash
  python --version
  python -m pip --version
  ```
