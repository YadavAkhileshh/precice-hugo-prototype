---
title: "Installation"
linkTitle: "Installation"
weight: 1
description: "How to install preCICE on various platforms"
---

## Installing preCICE

preCICE can be installed via various methods depending on your platform and needs.

### Using the preCICE Distribution

The **preCICE Distribution** bundles preCICE with commonly used adapters and tools.
This is the easiest way to get started with coupled simulations.

### Building from Source

```bash
git clone https://github.com/precice/precice.git
cd precice
mkdir build && cd build
cmake ..
make -j$(nproc)
make install
```

### Package Managers

- **Ubuntu/Debian**: Available via PPA
- **Arch Linux**: Available in AUR  
- **Spack**: `spack install precice`
- **Conda**: `conda install -c conda-forge precice`

### Language Bindings

preCICE provides bindings for multiple languages:

- **C++**: Native API
- **C**: `#include "precice/preciceC.h"`
- **Fortran**: Module-based interface
- **Python**: `import precice` (via `pyprecice`)
- **Matlab**: Matlab bindings available
