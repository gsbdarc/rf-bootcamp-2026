---
layout: default
title: "The Path Labyrinth"
parent: "Day 2 — The Alchemist's Lab"
nav_order: 3
permalink: /day2/path-labyrinth/
---

# The Path Labyrinth

<div data-room-id="d2-path-labyrinth"></div>

*Corridors fracture in every direction, each passage marked with the same name: "python." You call out and five doors crack open at once — five different Pythons, each certain it is the one you want. The labyrinth does not guess. It follows a strict protocol: check the first corridor, then the second, then the third, until it finds a match and stops. The researcher who understands the order commands the maze. The one who ignores it stumbles through cryptic failures, wrong versions, and errors that appear from nowhere. You are about to learn the order.*

---

## 🗡️ Main Quest

{: .important }
> **Quest:** Explore `$PATH` — understand how the shell finds commands — load and unload modules, and compare how the environment differs between JupyterHub and SSH terminals.

---

### Step 1 — See Your Current Path (Exercise 2.1)

In the **JupyterHub terminal**:

```bash
which python
which python3
echo $PATH
```

The `$PATH` variable (anything prefixed with `$` is a variable) is a colon-separated list of directories the shell searches left to right. The first match wins. Find where `python` and `python3` live in your `$PATH`.

---

### Step 2 — Load a Module and Watch PATH Change

```bash
module load imagemagick
which magick        # where is it now?
echo $PATH          # compare to before — a new directory was prepended
```

`module load` works by prepending a directory to `$PATH`. The `magick` command is now findable.

```bash
module list         # what modules are currently loaded?
```

Now unload it:

```bash
module unload imagemagick
which magick        # is it still there?
echo $PATH          # what changed?
```

Try using `magick` after unloading — you should get "command not found."

---

### Step 3 — Explore Available Modules (Exercise 2.2)

```bash
module avail        # list everything available on the Yens
module avail python # filter by name
```

Load a specific version of Python or R:

```bash
module load python/3.11
which python3
python3 --version
```

Why does the version matter? If your code uses a library that changed behavior between Python 3.9 and 3.11, `module load` gives you control over exactly which interpreter runs.

Unload when done:

```bash
module unload python/3.11
```

---

### Step 4 — Compare JupyterHub Terminal vs SSH Terminal (Exercise 2.3)

Open a **new SSH terminal** on your laptop (not the Jupyter terminal):

```bash
ssh SUNetID@yen.stanford.edu
which python3
echo $PATH
```

Now compare that output to what you see in the **JupyterHub terminal**.

Are they the same? Why might they differ? (Hint: JupyterHub starts with its own environment.)

---

### How PATH Lookup Works

```
  You have tools installed in different folders:

  /usr/bin/             python3  (system python)
  /apps/python/3.11/   python3  (module version)  ← not in PATH yet
  .venv/bin/            python3  (your venv)       ← not in PATH yet

  ──────────────────────────────────────────────────────────────
  Situation 1 — default shell (only /usr/bin/ in PATH):

  $ python3  →  shell finds /usr/bin/python3  →  runs system version

  ──────────────────────────────────────────────────────────────
  Situation 2 — after  module load python/3.11:
                adds /apps/python/3.11/ to the FRONT of PATH

  $ python3  →  shell finds /apps/python/3.11/python3 FIRST  ✓

  ──────────────────────────────────────────────────────────────
  Situation 3 — after  source .venv/bin/activate:
                adds .venv/bin/ to the FRONT of PATH

  $ python3  →  shell finds .venv/bin/python3 FIRST  ✓
```

Both `module load` and `source .venv/bin/activate` win by going first.

<label class="quest-check"><input type="checkbox" data-room="d2-path-labyrinth" data-key="main"> Main Quest complete</label>

---

## 🧠 Skills Learned

- `$PATH` is the map your shell uses to find every command you type — leftmost entry wins
- `module load` prepends a directory to `$PATH`; `module unload` removes it
- `module avail` shows everything available; loading a specific version pins the interpreter you use
- The Jupyter terminal and SSH terminal may have different environments — always check `which` when debugging
