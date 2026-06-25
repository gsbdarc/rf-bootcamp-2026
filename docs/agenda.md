# RF Coding Bootcamp 2026 — Agenda

**Stanford GSB DARC &nbsp;·&nbsp; 4 days &nbsp;·&nbsp; ~3 hours/day**

*Hands-on throughout. Each day ends with a Boss Gate — a capstone challenge you must push to GitHub to unlock the next floor.*

---

## 🔬 The Running Research Project

Every day adds a layer to **one research pipeline**. The dataset: SEC Form 3 filings — public disclosures of insider transactions. By Day 4, you'll have a fully documented, GPU-powered extraction pipeline running at scale on the Yens cluster.

Your `README.md` is a living document. It starts as a file inventory on Day 1 and ends as a production-grade pipeline description on Day 4. Each boss gate requires pushing an updated README.

| Day | What you add to the project |
|-----|-----------------------------|
| Day 1 | Organize the raw data dump. Write the first README. |
| Day 2 | Write the LLM extraction script. Process one filing. Update README. |
| Day 3 | Scale to hundreds of filings with a SLURM array job. Update README. |
| Day 4 | Swap to a local GPU model. Compare outputs. Final README. |

---

## Day 1 — Research Computing Foundations

**Theme:** Get oriented, get organized, get to the cluster.

**Why this bootcamp?**
What is research computing, a server, a terminal? How to be effective: habits that compound across a research career.

**The command line**
Core navigation and file operations; wildcards and bulk operations.
*Exercise:* `ls`, `cd`, `mkdir`, `mv`, `cp`, `rm`; rename 50 files with one wildcard command. Demo: the same task by hand vs. in the terminal — feel the difference.

**Staying organized in a research project**
What to do when a PI sends a raw data dump: look first, decide on a strategy, execute, document.
*Exercise:* Organize a messy SEC filing directory into a logical structure; write `README.md` describing what you did and why.

**Remote access**
SSH: log in to the Yens; cluster file system layout, storage quotas, software modules.
*Exercise:* `ssh` into the Yens; explore `/home`, `/scratch`; `module load` a tool; compare environments.

**File transfer**
Moving data between your laptop and the cluster.
*Exercise:* `scp` a file to the cluster and back; understand the shared `/scratch` filesystem.

**Version control**
Git as a lab notebook: fork → clone → commit → push.
*Exercise:* Fork the bootcamp repo, clone it to the Yens, make a commit, push.

### 📁 Project Milestone — Day 1
> Organized project committed with `README.md` describing the file structure.

### 🔑 Boss Gate 1
Organized project committed to GitHub.

---

## Day 2 — Python, AI Tools & the LLM Pipeline

**Theme:** From a Jupyter notebook to a working AI research pipeline.

**JupyterHub & Python environments**
Notebooks vs. scripts; virtual environments, `pip`, reproducibility; `$PATH` and how `module load` and `venv activate` change it.
*Exercise:* Connect to JupyterHub; load modules and observe `$PATH`; create a venv, `pip install` packages, register a Jupyter kernel; write and run a script from the terminal.

**Stanford AI Playground**
Stanford's gateway to frontier models (GPT-4, Claude, Llama, and more); web GUI and API gateway; what leaves the cluster and to where; tokens, costs, and context windows.
*Exercise:* Explore the web GUI at aitools.stanford.edu; load an API key securely from `.env`; add `.env` to `.gitignore`; initialize an OpenAI-compatible client.

**AI coding agents at Stanford** *(30-min discussion block)*
Data privacy and security when using AI tools; what logs are kept; best practices for researchers.

**Your first LLM pipeline**
First API call; Pydantic structured output; moving from notebook to script.
*Exercise:* Send one SEC Form 3 filing to the LLM API; extract `insider_name` and `role`; validate with a Pydantic model; serialize to JSON; refactor into a `.py` script.

### 📁 Project Milestone — Day 2
> `scripts/extract_filing.py` added; processes one filing and returns validated JSON. `README.md` updated with pipeline description and how to run the script. Committed and pushed.

### 🔑 Boss Gate 2
Working LLM extraction script pushed to GitHub, returning structured output.

---

## Day 3 — The Cluster: SLURM & Batch Computing

**Theme:** Stop running big jobs on the shared kitchen — learn the scheduler.

**The kitchen analogy** *(30-min live demo + class participation)*
What is a compute cluster; why shared resources need a scheduler; SLURM as head chef — stations, tickets, the queue.
*Exercise:* Run `userload` and `htop`; watch live resource contention across the Yens; discuss what you see.

**Resource estimation**
Measure wall time and memory before writing a single `#SBATCH` directive.
*Exercise:* `time python extract_filing.py`; watch memory with `htop -u $USER`; profile a mystery script from a second terminal — guess the `--time` and `--mem` before checking.

**Writing and submitting a SLURM job**
`#SBATCH` directives: time, memory, CPUs, email; `sbatch`, `squeue`, `sacct`, `scancel`; reading logs.
*Exercise:* Write `jobs/extract.sh`; submit with `sbatch`; monitor with `squeue`; retrieve output with `sacct`; cancel a job.

**Job arrays**
One script, one `--array` flag, hundreds of inputs running in parallel.
*Exercise:* Convert to a job array (`#SBATCH --array=1-100`); one task per filing; collect all results.

**Documentation**
Writing a README while the details are still fresh.
*Exercise:* Update `README.md` with SLURM instructions and how to rerun the array.

### 📁 Project Milestone — Day 3
> `jobs/extract.sh` and `jobs/array_extract.sh` added; results from all filings in `results/`; `README.md` updated with SLURM instructions. Committed and pushed.

### 🔑 Boss Gate 3
Array job complete, results committed, README updated.

---

## Day 4 — Scaling Up: Arrays, GPUs & Local LLMs

**Theme:** One job is a proof of concept. A pipeline is research.

**GPU computing on the Yens**
GPU tiers: A30 / A40 / H200 — VRAM, use cases, when the queue wait is worth it; `--gres=gpu:1`.
*Exercise:* Submit a GPU job to `yen-gpu4` (H200); verify with `nvidia-smi` and a PyTorch CUDA check.

**Local LLMs with Ollama**
Model weights on cluster hardware; nothing leaves the Yens; the OpenAI-compatible API means the same code works everywhere.
*Exercise:* Pull `llama3.2:3b`; `ollama serve` in a `screen` session; swap `base_url` in your Day 2 script — same code, local endpoint.

**Comparing LLM access patterns**
Local Ollama vs. Stanford AI Playground vs. third-party APIs — data residency, cost, model availability.
*Exercise:* Run the same 5 filings through both Playground and Ollama; save side-by-side in `results/comparison.csv`.

**Human vs. LLM & agent failure modes** *(discussion)*
When AI helps and when humans win; hallucination at scale, runaway loops, prompt injection, irreversibility — name them before your pipeline does.
*Exercise:* Review comparison results — where did the models disagree? What would it take to verify? What would you do differently if you were processing 10,000 filings?

### 📁 Project Milestone — Day 4
> `results/comparison.csv` added (Playground vs. Ollama outputs side-by-side). `README.md` finalized — full pipeline from raw data to GPU-powered extraction, both endpoints, how to rerun. Committed and pushed.

### 🔑 Boss Gate 4
Full pipeline documented and pushed — raw data in, structured results out, README tells the story.

---

*Questions? Reach out to the DARC team — we're here all week.*
