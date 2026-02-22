---
title: "Adapters"
linkTitle: "Adapters"
weight: 3
description: "Available solver adapters for preCICE coupling"
---

## preCICE Adapters

Adapters connect existing simulation solvers to preCICE. They translate the solver's internal data structures to preCICE API calls.

### Official Adapters

| Adapter | Solver | Coupling Type |
|---------|--------|---------------|
| **OpenFOAM** | OpenFOAM (CFD) | Fluid-structure, conjugate heat transfer |
| **CalculiX** | CalculiX (FEM) | Structural mechanics |
| **FEniCS** | FEniCS (FEM) | General PDE solving |
| **deal.II** | deal.II (FEM) | Adaptive mesh refinement |
| **Nutils** | Nutils (FEM) | Isogeometric analysis |
| **SU2** | SU2 (CFD) | Compressible flow |
| **DUNE** | DUNE (FEM) | Multi-scale simulations |
| **code_aster** | code_aster (FEM) | Structural analysis |

### Community Adapters

The preCICE community has developed adapters for many additional solvers including
ANSYS Fluent, COMSOL, Elmer, MBDyn, and more.

### Writing Your Own Adapter

The preCICE API is designed to be minimally invasive. A basic adapter requires:

1. **Initialize** preCICE with your participant name and config file
2. **Define meshes** — provide your coupling boundary vertices
3. **Exchange data** — write and read coupling data each time step
4. **Advance** — let preCICE handle the coupling logic
5. **Finalize** — clean up at the end of the simulation

```cpp
precice::Participant participant("Fluid", "precice-config.xml", rank, size);
participant.initialize();

while (participant.isCouplingOngoing()) {
    participant.writeData("FluidMesh", "Forces", vertexIDs, forces);
    participant.advance(dt);
    participant.readData("FluidMesh", "Temperature", vertexIDs, dt, temperatures);
}

participant.finalize();
```
