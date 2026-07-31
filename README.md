<div align="center">

# BridgeSplat Reproduction Report

### [Bridging CT and Non-Rigid Gaussian Splatting for Deformable Intraoperative Surgical Navigation (MICCAI 2025)](https://papers.miccai.org/miccai-2025/paper/4699_paper.pdf)

</div>

---

## About This Repository

This repository contains **reproduction outputs** (trained results, visualizations, interactive HTML report) for BridgeSplat. It serves as a reference to inspect the method's behavior across 8 datasets.

> ⚠️ **Note:** The source code and original datasets in this repo are from the official release. This fork only adds reproduction outputs — all training was done from scratch with zero pretrained weights.

## Quick Links

- **Live Report:** https://linkx-known.github.io/ct-bridgesplat/report.html
- **Official Repository:** https://github.com/maxfehrentz/ct-informed-splatting
- **Official Dataset:** https://huggingface.co/datasets/maxfehrentz/BridgeSplat
- **Paper:** https://papers.miccai.org/miccai-2025/paper/4699_paper.pdf

## Getting Started

### Clone & Install

```bash
git clone --recursive https://github.com/maxfehrentz/ct-informed-splatting.git
cd ct-informed-splatting
conda env create -f environment.yaml
conda activate bridgesplat
```

Install submodules (navigate to each folder individually):

```bash
cd src/submodules/gaussian-rasterization && python setup.py install && cd ../../..
cd src/submodules/simple-knn && python setup.py install && cd ../../..
cd src/cpp_extensions/arap && python setup.py install && cd ../../..
```

### Download Dataset

Download from [HuggingFace](https://huggingface.co/datasets/maxfehrentz/BridgeSplat) and place in a top-level `data/` folder.

### Run

```bash
python run.py configs/SOFA/sofa_liver_in.yaml --visualize
```

## Reproduction Details

| Item | Detail |
|------|--------|
| Branch | Official `main`, unmodified |
| Pretrained weights | **None** — trained from scratch |
| Depth supervision | **None** — monocular RGB only (by design, consistent with paper) |
| Datasets trained | 8 (2 ATLAS clinical + 6 SOFA synthetic) |
| Frames per scene | 46–62 |
| Iterations per frame | 100 |
| Total iterations | ~44,000 across all 8 datasets |

## Included Outputs

- `output/` — All training outputs (splats, mapping diagnostics, mesh overlays, deformation fields, deformed OBJ meshes)
- `report.html` — Interactive browser-based report with image galleries and lightbox viewer
- `report_assets/` — Three.js for historical 3D viewer (currently not used in report)

## License

See official repository for license terms.

## Citation

```bibtex
@inproceedings{fehrentz2025bridgesplat,
  title={BridgeSplat: Bidirectionally Coupled CT and Non-rigid Gaussian Splatting
         for Deformable Intraoperative Surgical Navigation},
  author={Fehrentz, Maximilian and Winkler, Alexander and Heiliger, Thomas
          and Haouchine, Nazim and Heiliger, Christian and Navab, Nassir},
  booktitle={International Conference on Medical Image Computing
             and Computer-Assisted Intervention},
  pages={44--53},
  year={2025},
  organization={Springer}
}
```
