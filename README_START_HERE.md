# Spatial Data Science with Python — complete Google Colab / Jupyter package

**Course:** MSc GIS / AGMS 1333, following Table 4 · **14 weeks**

## Package inventory

- **00_START_HERE.ipynb** — interactive installation, file-location and dataset check.
- **01_Core_Labs/** — 14 independent `.ipynb` notebooks for the 14 weeks.
- **02_Advanced_Experiments/** — 14 extension notebooks, each with four short, executable experiments (56 in total).
- **04_CAPSTONE_WebGIS.ipynb** — an end-to-end synthetic screening and GeoJSON export exercise.
- **data/** — all locally runnable CSV/GeoJSON/GeoTIFF/metadata inputs.
- **DATA_ONLY.zip** — compact data archive for Google Colab upload.
- **requirements.txt** — Python dependencies for Jupyter.

**Important:** the notebooks do not have to be run together. Every notebook has its own setup cell, imports, method explanation, executable Python and review questions. For a new Colab runtime, it will prompt for `DATA_ONLY.zip` when the data folder is missing.

## On Google Colab

1. Download and extract the package ZIP on your computer.
2. Open **https://colab.research.google.com** → **File → Upload notebook**.
3. Select `00_START_HERE.ipynb` first, then an individual notebook from `01_Core_Labs`.
4. When the first setup cell asks, upload **DATA_ONLY.zip** (not the large course ZIP).
5. Run **Runtime → Run all** or execute cells sequentially. Review tables, figures, and the scientific interpretation after each code block.
6. For method variations, open the matching Week_XX notebook in `02_Advanced_Experiments`.

**Colab session note:** Colab runtimes can reset; when that happens, upload `DATA_ONLY.zip` again (or keep it in Drive and manually copy it into the session). Notebooks do not automatically write to or access Google Drive.

## Local JupyterLab / VS Code

Extract the ZIP with its folders intact, open a terminal in this folder, then execute:

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
python -m pip install -r requirements.txt
python -m jupyter lab
```

Open `01_Core_Labs/Week_01_...ipynb`. The setup automatically discovers the `../data` folder. Use Python 3.11–3.13 with compatible dependencies. `rasterio` and `folium` are used in selected later labs.

## Academic integrity and methods

The synthetic grid is **144 cells at 250 m**, with **864 distinct cell-date observations** from January to June 2025, **24 simulated facilities**, CRS **EPSG:32647**. The dataset is not an official survey of Kuala Lumpur or anywhere else. Scientific numbers may differ from prior versions of the course handbook if datasets were regenerated. Do not use teaching data to claim real urban heat or service performance.

Some notebooks use simplified teaching baselines rather than production-grade spatial analysis. For example, Euclidean distance is not network travel time; a threshold mask is not a trained neural network; and geographic GroupKFold does not guarantee a buffer between folds. Each notebook includes this kind of interpretive caution.

## Troubleshooting

- **FileNotFoundError**: upload `DATA_ONLY.zip` when asked, or keep the extracted `data/` folder adjacent to notebook folders.
- **ModuleNotFoundError**: run `%pip install <package>` in a Colab notebook cell, or install `requirements.txt` in JupyterLab.
- **KeyError** for a column: check the exact field names with `df.columns` and inspect dataset metadata.
- **`NaN` in output**: inspect `isna().sum()`; missingness is not always zero.
- **Unrealistically high score**: inspect geographic split design and preprocessing leakage.
- **No visible plot**: run cells in order and ensure `plt.show()` executes.

## Instructor notes

Each Week_XX core notebook corresponds to the same Week_XX in the HTML presentation. Advanced notebooks provide parameter changes and small, separately executable examples, but do not replace independent field validation. The Capstone can be adapted to real spatial data only after checking schema, CRS, scale, completeness, and permissions.
