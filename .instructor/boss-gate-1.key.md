# Boss Gate 1 — Solution Key

**Instructor use only.** This file is not served by GitHub Pages.  
Update `SIGNATURE_SPELL` and `SEAL` below to match what you staged in `/scratch/shared/rf-bootcamp-2026/boss1/`.

---

## Staged files

- `/scratch/shared/rf-bootcamp-2026/boss1/` — ~50 standard spell files + 1 signature spell
- Standard spells: 10 per element × 5 elements (`fire`, `ice`, `lightning`, `earth`, `wind`)
- Signature spell: `void_arcane_6_legendary_archmage.spell` (update filename as needed)
- Contents of signature spell:
  ```
  SIGNATURE: ARCHMAGE-SEAL-XXXX
  ```
  Replace `ARCHMAGE-SEAL-XXXX` with the real seal string.

---

## Full solution

```bash
# Step 1 — create workspace and copy vault
mkdir /scratch/shared/$USER/boss1
cp -r /scratch/shared/rf-bootcamp-2026/boss1/ /scratch/shared/$USER/boss1/
cd /scratch/shared/$USER/boss1
ls | wc -l           # should show 51

# Step 2 — sort into element directories
mkdir fire ice lightning earth wind
mv *_fire_*.spell fire/
mv *_ice_*.spell ice/
mv *_lightning_*.spell lightning/
mv *_earth_*.spell earth/
mv *_wind_*.spell wind/

# Step 3 — find the outlier
ls fire/ | wc -l     # 10
ls ice/ | wc -l      # 10
ls lightning/ | wc -l  # 10
ls earth/ | wc -l    # 10
ls wind/ | wc -l     # 10
ls *.spell           # one file remains: void_arcane_6_legendary_archmage.spell

# Step 4 — read the seal
cat void_arcane_6_legendary_archmage.spell
# SIGNATURE: ARCHMAGE-SEAL-XXXX

# Step 5 — record proof in repo
cd ~/rf-bootcamp-2026/
nano signature_spell.txt
# write exactly:
#   Spell found: void_arcane_6_legendary_archmage.spell
#   Signature: ARCHMAGE-SEAL-XXXX

# Step 6 — push
git add signature_spell.txt
git commit -m "Boss Gate 1: Archmage signature found"
git push
```

---

## Grader check

The auto-grader (`scripts/check_boss_gates.py`) checks that `signature_spell.txt` exists in the student's fork root and that line 2 matches the expected seal string. Update the expected string there if you change `ARCHMAGE-SEAL-XXXX`.
