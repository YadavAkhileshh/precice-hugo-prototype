---
title: "Configuration"
linkTitle: "Configuration"
weight: 2
description: "Configuring preCICE for coupling scenarios"
---

## preCICE Configuration

Every preCICE simulation is configured through an XML file, typically named `precice-config.xml`.

### Basic Structure

```xml
<precice-configuration>
  <solver-interface dimensions="3">
    <data:scalar name="Temperature"/>
    <data:vector name="Forces"/>
    
    <mesh name="FluidMesh">
      <use-data name="Temperature"/>
      <use-data name="Forces"/>
    </mesh>
    
    <participant name="Fluid">
      <provide-mesh name="FluidMesh"/>
      <write-data name="Forces" mesh="FluidMesh"/>
      <read-data name="Temperature" mesh="FluidMesh"/>
    </participant>
  </solver-interface>
</precice-configuration>
```

### Coupling Schemes

- **Serial explicit** — simplest approach for weak coupling
- **Serial implicit** — strong coupling with convergence acceleration
- **Parallel explicit/implicit** — simultaneous data exchange

### Data Mapping Methods

- **Nearest-neighbor** — simple, fast
- **Nearest-projection** — better accuracy for non-matching meshes
- **Radial basis function (RBF)** — best accuracy, configurable basis functions

### Acceleration Methods

For implicit coupling, preCICE supports:
- **Aitken** under-relaxation
- **IQN-ILS** (quasi-Newton with inverse least-squares)
- **IQN-IMVJ** (multi-vector quasi-Newton)
