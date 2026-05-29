# Co-localization Analysis of Slc39a9 and Lipid Rafts

This repository contains a single Jupyter Notebook that performs quantitative whole-cell expression and spatial co-localization analysis of Slc39a9 and lipid raft markers from multi-channel wide-field fluorescence microscopy images.

## Analysis Overview
As outlined in the project's methodology, the notebook automates the following steps:
1. **Normalization:** Image channels are normalized via intensity percentile clipping (3rd to 99.9th percentiles).
2. **Segmentation:** Whole-cell bodies are segmented using the `Cellpose` deep learning framework.
3. **Filtering:** Artifacts and border-touching cells are removed using `scikit-image`.
4. **Background Correction:** Image-wide background medians are calculated from non-masked regions and subtracted from raw pixel intensities.
5. **Quantification & Co-localization:** Whole-cell mean intensities are extracted, and a per-pixel `Spearman` rank correlation coefficient is calculated inside each individual single-cell mask via `SciPy` to evaluate spatial co-distribution independent of channel scaling or intensity variation.

---

## Getting Started

This project uses `uv` for fast, reproducible dependency management. The exact environment state is locked in `uv.lock` and configured via `pyproject.toml`.

### Prerequisites
Make sure you have `uv` installed.

### Environment Replication & Running the Notebook

1. Clone the repository:

```Bash
git clone https://github.com/kAirdLab/2026_rbg_colocalization.git
cd 2026_rbg_colocalization
```

2. Recreate and sync the environment:

Run the following command in the project root. This will automatically create a local `.venv`:

```bash
uv sync
```

3. Run the jupyter notebook within the recreated environment