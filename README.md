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
├── model_traning.ipynb
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

```bash
pip install tensorflow matplotlib jupyter
jupyter notebook model_traning.ipynb
```

## Repository notes

- Large binaries (datasets, trained weights, archives) are ignored via `.gitignore`.
- To reproduce training, download the dataset first, then run the notebook from the project root.
