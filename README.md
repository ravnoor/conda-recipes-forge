# conda-recipes-forge

A collection of conda recipes for MINC (Medical Image NetCDF) toolkit and related scientific computing packages.

## Overview

This repository contains conda package recipes for building and distributing scientific computing tools, with a focus on medical imaging and the MINC ecosystem. The recipes are designed to work with both traditional conda-build and the modern rattler-build system.

## Packages

### MINC Ecosystem

- **[minc-toolkit-v2](minc-toolkit-v2.1.9.18/)** - Complete toolkit for processing MRI scans
  - Versions: 1.9.18.4, 1.9.19.1
  - Variants: `noblas`, `legacy`, `openblas`
  - Visual options: `novisual`, `full`

- **[mni_minctools](mni_minctools/)** - Core tools for working with MINC files
  - Version: 2.4.06
  - Essential MINC utilities and converters

- **[pyezminc](pyezminc/)** - Python library for MINC I/O
  - Version: 1.3.01
  - Python bindings using Cython and MINC1 API

### Scientific Computing

- **[antspyx](antspyx/)** - ANTs (Advanced Normalization Tools) Python bindings
  - Version: 0.5.4
  - Medical imaging registration and segmentation

- **[tslearn](tslearn/)** - Time series machine learning toolkit
  - Version: 0.6.3
  - Specialized algorithms for time series analysis

## Build System

### Requirements

- [rattler-build](https://prefix-dev.github.io/rattler-build/) (recommended)
- Or traditional conda-build

### Building Packages

#### Using rattler-build (Recommended)

```bash
# Build all packages
rattler-build build --recipe-dir . \
  --channel conda-forge \
  --channel https://repo.prefix.dev/nrx-forge

# Build specific package
rattler-build build --recipe-dir pyezminc \
  --channel conda-forge \
  --channel https://repo.prefix.dev/nrx-forge
```

## Recipe Structure

### Modern Recipes (rattler-build)
- `recipe.yaml` - Main recipe definition
- `variants.yaml` - Build variants and configurations
- `build.sh` - Build script (if needed)


## CI/CD

The repository includes GitHub Actions workflows for automated building and publishing:

- **Triggers**: Push to main, pull requests, manual dispatch
- **Platforms**: Linux (x64, ARM64), macOS (ARM64)
- **Publishing**: Packages are uploaded to `nrx-forge` channel on repo.prefix.dev

### Workflow Features
- Multi-platform builds
- Skip existing packages
- Automatic upload on push to main
- Integration with private conda channels



### Recipe Guidelines

- Use `recipe.yaml` format for new packages
- Include comprehensive tests
- Follow conda-forge standards
- Document any special build requirements
- Use semantic versioning

## Channels

The recipes are configured to use these channels in order:
1. `conda-forge/label/rust_dev`
2. `conda-forge`
3. `https://repo.prefix.dev/nrx-forge`
4. `minc-forge`

## License

Individual packages maintain their respective licenses:
- MINC tools: NGPL (Non-commercial GPL)
- ANTsPyx: Apache-2.0
- TSLearn: BSD-2-Clause

## Support

For issues related to:
- **Package builds**: Open an issue in this repository
- **MINC toolkit**: Visit [BIC-MNI GitHub](https://github.com/BIC-MNI)
- **Individual packages**: Refer to their respective repositories

## Links

- [MINC Toolkit Documentation](http://bic-mni.github.io/man-pages)
- [Conda Build Documentation](https://docs.conda.io/projects/conda-build/)
- [Rattler Build Documentation](https://prefix-dev.github.io/rattler-build/)

