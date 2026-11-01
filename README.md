# Leaf_bLight_DL

Deep learning based potato leaf disease classification using a CNN built with TensorFlow/Keras.

## Dataset

This project uses the **PlantVillage** dataset.

- Source: https://www.kaggle.com/datasets/arjuntejaswi/plant-village
- The dataset is **not** included in this repository (it is listed in `.gitignore`).
- Download it from the link above and place the class folders inside a `PlantVillage/` directory at the project root.

Classes used in `model_traning.ipynb`:

| Class | Images |
| --- | --- |
| `Potato___Early_blight` | 1000 |
| `Potato___Late_blight` | 1000 |
| `Potato___healthy` | 152 |

Expected layout:

```
Leaf_bLight_DL/
├── PlantVillage/
│   ├── Potato___Early_blight/
│   ├── Potato___Late_blight/
│   └── Potato___healthy/
├── api/
│   └── main.py
├── saved_models/
│   └── 1/
├── model_traning.ipynb
├── pyproject.toml
├── uv.lock
├── README.md
└── .gitignore
```

## Model

`model_traning.ipynb` builds an image input pipeline with
`keras.preprocessing.image_dataset_from_directory`:

- Batch size: 32
- Image size: 256 x 256
- Channels: 3
- Epochs: 50
- Split: 80% train / 10% validation / 10% test

## Getting started

This project is managed with [uv](https://docs.astral.sh/uv/). Python 3.10 is required
(TensorFlow 2.10 is the last release with Windows DirectML support).

```bash
# create .venv and install everything from uv.lock
uv sync

# add / remove packages (updates pyproject.toml + uv.lock)
uv add <package>
uv remove <package>

# run the API
uv run uvicorn api.main:app --reload
```

To use the notebook, select the interpreter at `.venv\Scripts\python.exe`
(`ipykernel` is included in the `dev` dependency group) or run:

```bash
uv run jupyter notebook model_traning.ipynb
```

Dependencies live in `pyproject.toml`; `uv.lock` pins the exact versions.
`requirements.txt` is kept only for legacy/deployment reference.

## Repository notes

- Large binaries (datasets, trained weights, archives, the `.venv`/`ai-ml` environments) are ignored via `.gitignore`.
- To reproduce training, download the dataset first, then run the notebook from the project root.
- `tensorflow-io-gcs-filesystem` is constrained to `<=0.31.0` in `pyproject.toml` because later
  versions no longer ship Windows wheels.
