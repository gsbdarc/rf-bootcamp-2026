---
layout: default
title: "The Arcane Notebook"
parent: "Day 2 — The Alchemist's Lab"
nav_order: 2
permalink: /day2/arcane-notebook/
---

# The Arcane Notebook

<div data-room-id="d2-arcane-notebook"></div>

*You push open a heavy oak door and step into a firelit study. The shelves stretch floor-to-ceiling, stacked with glowing notebooks that hum with quiet power — each one running not on your laptop, but on the dungeon's own iron engines deep below. Every page is a cell. Every cell is a spell: conjure charts, interrogate data, summon results from thousands of rows in a breath. The warmth in the air comes from the Yens. You're just the one holding the quill.*

---

## 🔰 Warm-Up: SSH Check

Before opening any notebooks, confirm you're on the Yens.

```bash
ssh SUNetID@yen.stanford.edu
```

Once connected:

```bash
hostname          # which Yen did you land on?
whoami            # are you logged in as yourself?
pwd               # what directory are you in?
ls                # do you see files from Day 1?
```

You should see your home directory and the `rf-bootcamp-2026` folder you cloned yesterday.

---

## 🗡️ Main Quest

{: .important }
> **Quest:** Open JupyterHub on the Yens, run your first Python cells in a notebook, write and execute a script from the terminal, and explore files using the Jupyter terminal.

---

### Step 1 — Open JupyterHub

JupyterHub is a browser-based interface to the Yens. Choose any node:

| Node | URL |
|------|-----|
| Yen1 | [yen1.stanford.edu/jupyter/hub/home](https://yen1.stanford.edu/jupyter/hub/home) |
| Yen2 | [yen2.stanford.edu/jupyter/hub/home](https://yen2.stanford.edu/jupyter/hub/home) |
| Yen3 | [yen3.stanford.edu/jupyter/hub/home](https://yen3.stanford.edu/jupyter/hub/home) |
| Yen4 | [yen4.stanford.edu/jupyter/hub/home](https://yen4.stanford.edu/jupyter/hub/home) |
| Yen5 | [yen5.stanford.edu/jupyter/hub/home](https://yen5.stanford.edu/jupyter/hub/home) |

Log in with your SUNet credentials. You should see the same files as your home directory on the Yens.

---

### Step 2 — Start a Notebook and a Terminal

- Click the **blue "+"** to open the Launcher
- Start a **Python 3** notebook
- Also open a **Terminal** tab — you'll switch between the two throughout Day 2

---

### Step 3 — First Notebook Cells (Exercise 1.1)

Type each block into a **separate cell** and run with **Shift+Enter**:

```python
# Cell 1
print("Hello, World!")
```

```python
# Cell 2
import math
print(math.pi)
```

```python
# Cell 3
numbers = [1, 2, 3, 4, 5]
print(sum(numbers))
```

Expected output: `Hello, World!`, `3.141592653589793`, `15`

---

### Step 4 — Save and Run a Python Script (Exercise 1.2)

In the **terminal tab**, create an empty file:

```bash
touch interactive.py
```

Find `interactive.py` in the JupyterHub file browser, open it, and paste the three code blocks from Step 3. Save the file.

Now run it from the terminal:

```bash
python interactive.py
```

Verify you get the same output as the notebook cells. This is how you move from exploring in a notebook to running standalone scripts.

---

### Step 5 — Terminal Basics (Exercise 1.3)

In the **terminal tab**:

```bash
# List your home directory
ls

# Navigate into your bootcamp repo
cd rf-bootcamp-2026

# List its contents
ls

# Which python are you using?
which python3
```

Note the python path — compare it to what you see in the notebook.

---

### Step 6 — Read a File in the Notebook (Exercise 1.4 — Placeholder)

{: .note }
> 🚧 **Coming soon:** This exercise will use files from your grimoire to explore reading data into the notebook and navigating paths. For now, try this on your own:
> 
> ```python
> # Pick any .spell file from your grimoire on the Yens
> with open("/scratch/shared/SUNetID/grimoire/fire/some_spell.spell", "r") as f:
>     print(f.read())
> ```
> 
> What does the file contain? Can you print just the first line?

<label class="quest-check"><input type="checkbox" data-room="d2-arcane-notebook" data-key="main"> Main Quest complete</label>

---

## 🧠 Skills Learned

- You can open JupyterHub on the Yens and run Python from any browser — no SSH required for code
- You know how to run cells in a notebook (`Shift+Enter`) and move working code into a `.py` script
- You understand that the Jupyter terminal and the SSH terminal are both shells on the same machine — the same files are visible in both
