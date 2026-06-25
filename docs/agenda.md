# RF Coding Bootcamp 2026 — Agenda

**Stanford GSB DARC &nbsp;·&nbsp; 4 days &nbsp;·&nbsp; ~3 hours/day**

*Hands-on throughout. Each day ends with a Boss Gate — a capstone challenge you must push to GitHub to unlock the next floor.*

---

## Day 1 — Research Computing Foundations

**Theme:** Get oriented, get organized, get to the cluster.

### Why This Bootcamp?
- What is research computing, and why does it matter for pre-docs?
- What is a server? How is it different from your laptop?
- What is a terminal, and why do researchers live in it?
- How to be effective: habits that compound across a research career

### The Command Line
- Demo: doing the same task by hand vs. in the terminal
- Core commands: navigate, list, create, move, delete
- Working with groups of files: wildcards and bulk operations

### Staying Organized in a Research Project
> *Scenario: your PI sends you a folder of raw data files with no structure. Now what?*

1. **Look first** — understand what you have before touching anything
2. **Decide on a strategy** — how should this be organized? File types? Date? Source?
3. **Execute** — move, rename, restructure with CLI commands
4. **Document** — write a README describing what you did and why

Tips: file listings, grouping by type, consistent naming conventions

### Remote Access & Version Control
- SSH: log in to the Yens cluster
- File transfer: move data between your laptop and the cluster
- Git: fork → clone → commit → push — your lab notebook for code

### 🔑 Boss Gate 1
Commit your organized project structure to GitHub.

---

## Day 2 — Python, AI Tools & the LLM Pipeline

**Theme:** From a Jupyter notebook to a working AI research pipeline.

### JupyterHub
- Connecting to JupyterHub on the Yens
- Notebooks vs. scripts: when to use each
- Python environments: virtual environments, pip, kernels

### Stanford AI Playground
- What it is: Stanford's gateway to frontier models (GPT-4, Claude, Llama, and more)
- Web GUI at aitools.stanford.edu — interactive exploration
- API gateway — the same models via code
- Trade-offs: audited, rate-limited, no personal billing needed

### Working with Claude and LLMs
- What are agents? What are the risks?
- Data privacy and security: what leaves the cluster, and where does it go?
- Tokens, costs, and context windows: the economics of every API call
- When to use Stanford AI Playground vs. a local model vs. your own key

### Your First API Pipeline
- Secure key management with `.env` and `python-dotenv`
- First API call: extract structured data from a real document
- Validate LLM output: Pydantic for clean, typed results
- From notebook to script: run the same code from the terminal

### 🔑 Boss Gate 2
Push a working Python script that calls the LLM API and returns structured output.

---

## Day 3 — The Cluster: SLURM & Batch Computing

**Theme:** Stop running big jobs on the shared kitchen — learn the scheduler.

### The Kitchen Analogy *(30-min live demo + class participation)*
- What is a compute cluster, really?
- Why shared resources need a scheduler — and what happens without one
- SLURM as head chef: stations, tickets, the queue
- Live demo: `userload`, `htop` — see who's using the Yens right now

### Measuring Before Requesting
- Run your Day 2 script interactively — observe time and memory
- `time`, `htop`, `userload`: your profiling toolkit
- Rule of thumb: set `--time` and `--mem` from measurements, not guesses
- Mystery script exercise: profile an unfamiliar script in real time

### Writing and Submitting a SLURM Job
- `#SBATCH` directives: time, memory, CPUs, email
- `sbatch`: hand the recipe to the head chef
- `squeue`, `sacct`, `scancel`: watch, cancel, and autopsy your jobs

### Understanding the Scheduler
- What happens if you ask for too much? Too little?
- Reading logs: where did your job fail, and why?
- Adjusting resource requests based on real profiling data
- The interactive Yens vs. a dedicated compute node: know when to use each

### 🔑 Boss Gate 3
Submit your Day 2 LLM script as a SLURM batch job; document the pipeline.

---

## Day 4 — Scaling Up: Arrays, GPUs & Local LLMs

**Theme:** One job is a proof of concept. A pipeline is research.

### Scaling Your Script
- How does your script scale? Sequential vs. parallel execution
- SLURM job arrays: run one script across hundreds of inputs simultaneously
- Resource considerations for large arrays: what changes at scale?

### GPU Computing on the Yens
- GPU tiers: A30, A40, H200 — what each is for and when to use it
- `--gres=gpu:1`: requesting a GPU in any SLURM script
- Submit a GPU job; verify it ran on real hardware with `nvidia-smi`

### Local LLMs with Ollama
- Pull and run a model locally on cluster hardware — no API key, no billing
- The OpenAI-compatible API: same Python code, only `base_url` changes
- Comparing options: Ollama (local) vs. Stanford AI Playground vs. third-party APIs

### Data Governance & Agent Safety
- The 3-bucket rule: public, restricted, PII — which tool is safe for which data?
- Agent failure modes: hallucination at scale, runaway loops, prompt injection, irreversibility
- Designing defensible research pipelines

### 🔑 Boss Gate 4
Scale the pipeline with a SLURM job array; run one job on the GPU; document everything.

---

*Questions? Reach out to the DARC team — we're here all week.*
