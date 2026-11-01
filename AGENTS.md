# AGENTS.md

Instructions for AI agents working in this repository.

## Push workflow

When the user says **"push"** or **"push updated"** (or any close variant), do this without further questions:

1. `git add -A`
2. Review `git status --short` and confirm no dataset/binaries are being staged (see "Ignored content").
3. Commit with a short, descriptive message.
4. `git push` to `origin main`.

If the working tree is already clean and in sync, just report `Everything up-to-date`.

## Repository facts

- Remote: `https://github.com/ShubhamKumarSahu-svg/Leaf_bLight_DL.git`
- Default branch: `main` (tracks `origin/main`)
- Author identity: `ShubhamKumarSahu-svg <shubhamisok@gmail.com>` (from global git config)
- Credential helper: Windows `manager`

## Ignored content

`PlantVillage/` (the ~37.6 MB image dataset) and trained model artifacts are intentionally
excluded via `.gitignore`. Never commit them; if a new large artifact appears, add a matching
`.gitignore` entry instead of staging it.

## Project

- `model_traning.ipynb` — TensorFlow/Keras CNN training notebook for potato leaf disease
  classification (Early blight / Late blight / healthy), 256x256 inputs, batch 32, 50 epochs,
  80/10/10 split.
- Dataset source: https://www.kaggle.com/datasets/arjuntejaswi/plant-village
  (download manually into `PlantVillage/` at the project root).
