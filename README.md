# conda-recipes-forge

> **Note**
> This repository provides modern, reproducible conda and rattler-build recipes for scientific computing and medical imaging, with a focus on the MINC ecosystem and related tools.

## Overview

**conda-recipes-forge** is a curated collection of build recipes for open-source scientific and medical imaging software. It supports both [rattler-build](https://prefix-dev.github.io/rattler-build/) and traditional conda-build workflows, enabling cross-platform, automated builds and CI/CD.

---

## Recipes Included

### MINC & Medical Imaging
- **minc-toolkit-v2.1.9.18/**, **minc-toolkit-v2.1.9.19/**  
  Complete MRI processing toolkit (multiple versions/variants)
- **mni_minctools/**  
  Core MINC file utilities and converters
- **pyezminc/**  
  Python bindings for MINC I/O (Cython-based)
- **antspyx/**  
  ANTs (Advanced Normalization Tools) Python bindings

### Scientific & Data Tools
- **tslearn/**  
  Time series machine learning toolkit
- **bws/**  
  Bitwarden Secrets Manager CLI (Rust)
- **yazi/**  
  Blazing fast terminal file manager (Rust)
- **simdjson/**  
  SIMD-accelerated C++ JSON parser

---

## Quickstart

```sh
# Build all packages (recommended)
rattler-build build --recipe-dir . \
  --channel conda-forge \
  --channel https://repo.prefix.dev/nrx-forge

# Build a specific package
drattler-build build --recipe-dir antspyx \
  --channel conda-forge \
  --channel https://repo.prefix.dev/nrx-forge
```

- Each recipe defines its own tests (see `tests:` in each `recipe.yaml`).
- Output artifacts are placed in each package's `output/` directory.

---

## Project Structure & Conventions

- Each package has its own directory (see above).
- Modern recipes use `recipe.yaml` (main), `variants.yaml` (build variants), and optional `build.sh` (custom steps).
- Rust-based recipes (e.g., `bws`, `yazi`) use bundled C libraries if system libraries are missing/incompatible.
- Channels are prioritized: `conda-forge/label/rust_dev`, `conda-forge`, `https://repo.prefix.dev/nrx-forge`, `minc-forge`.
- See `.github/copilot-instructions.md` for AI agent guidelines and advanced conventions.

---

## CI/CD & Automation

- GitHub Actions (`.github/workflows/build.yaml`) builds all packages on Linux (x64, ARM64) and macOS (ARM64).
- Packages are uploaded to the `nrx-forge` channel on push to `main`.
- Multi-platform, skip-existing, and private channel integration supported.

> [!TIP]
> For more details, see the root `README.md` and each package's directory for specific patterns and exceptions.

---

## Resources

- [MINC Toolkit Documentation](http://bic-mni.github.io/man-pages)
- [Conda Build Documentation](https://docs.conda.io/projects/conda-build/)
- [Rattler Build Documentation](https://prefix-dev.github.io/rattler-build/)

