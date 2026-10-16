---
project_outline: "[[01-project-outline]]"
---


<!-- 5xl -->
# Real-Time Procedural Terrain Generation and Level-of-Detail Management

Author: Rayyan Alsmarat  
Neptun: Y0J3P8  
Supervisor: Péter NOVÁK  
Project ID: 2026-NP-03

---

<!-- 2xl -->
[prmd.atom-forge.eu/docs](https://prmd.atom-forge.eu/docs)

---

## Problem

Large game worlds require terrain to be generated and displayed without keeping maximum-detail geometry everywhere at once.

This project aims to generate terrain procedurally, manage it in chunks or tiles, and select geometric detail according to the viewer's position and computational constraints. As the viewer moves, the system must load, update, and remove terrain chunks while remaining responsive.

The project will implement and compare at least two meaningful terrain-generation or level-of-detail (LOD) strategies, or variants. The comparison will investigate the trade-offs between visual fidelity, generation and update cost, memory use, loading responsiveness, and geometric complexity.

## Target users

The project is an experimental terrain demonstrator rather than a complete open-world game.

The main user is the person interacting with and evaluating the demonstrator. They should be able to move through the generated terrain, observe how chunks and LOD change, and run or review controlled comparisons of the selected strategies.

The project also supports technical evaluation by recording performance and complexity indicators and documenting the limits of the implementation.

## Planned scope

The planned demonstrator will include:

- procedural terrain height or geometry generation
- terrain chunk or tile management
- dynamic loading, updating, and removal of chunks as the viewer moves
- a custom LOD selection mechanism
- at least two meaningful terrain-generation or LOD strategies, or variants, for comparison
- incremental or asynchronous generation
- handling of neighbouring chunks with different LODs
- prevention of visible cracks or measurement and analysis of cracks and abrupt transitions
- controlled experiments varying view distance, camera movement, terrain size, chunk resolution, number of active chunks, LOD thresholds, and generation complexity
- reproducible measurements of generation time, frame or CPU cost, memory use, generated geometry size, and chunk-loading latency
- visual-fidelity and geometric/visual-error assessment where practical

The specific algorithms and implementation choices will be selected during the technical investigation before the main implementation. Building a complete open-world game is outside the scope.

## Initial user journeys

### Moving through the terrain

1. The viewer starts the demonstrator.
2. The system generates or loads the terrain chunks needed around the viewer.
3. The custom LOD policy selects the detail level for active regions.
4. The viewer moves through the terrain.
5. The system requests and generates newly needed chunks.
6. The system updates LOD and unloads chunks that are no longer needed.
7. The viewer observes the terrain and its responsiveness.

### Comparing terrain strategies

1. The operator selects an implemented terrain-generation or LOD strategy.
2. The operator chooses a documented test configuration.
3. The system displays the generated terrain.
4. A defined movement or observation scenario is performed.
5. The system records the selected performance and complexity measurements.
6. The experiment is repeated with another strategy under equivalent conditions.
7. The results are compared and the trade-offs are documented.

## Next steps

1. Research suitable procedural terrain-generation methods.
2. Research candidate LOD strategies and identify at least two meaningful approaches or variants to compare.
3. Choose an implementation environment that allows the project to make its own central terrain-generation and LOD contributions.
4. Define the terrain chunk representation and generation pipeline.
5. Define chunk loading, updating, unloading, and incremental/asynchronous generation.
6. Investigate how to handle boundaries between neighbouring chunks with different LODs.
7. Define the experiment parameters, test scenarios, metrics, and reproducibility procedure.
8. Build a small prototype to validate feasibility and establish baseline measurements.
9. Implement the selected approaches, run controlled experiments, and compare the results
