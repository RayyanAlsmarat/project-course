---
project_outline: "[[01-project-outline]]"
---

<!-- 5xl -->
# Real-Time Procedural Terrain Generation and Level-of-Detail Management

**Rayyan Alsmarat · Y0J3P8**  
**Supervisor:** Péter Novák  
**Project ID:** 2026-NP-03

---

<!-- 2xl -->

## The Challenge

# Big worlds can't run at maximum detail everywhere

Large game worlds need terrain generated and displayed without maximum-detail geometry everywhere at once.

### 01 — Generate procedurally
Manage terrain in chunks or tiles.

### 02 — Select detail
Use viewer position and computational constraints.

### 03 — Stay responsive
Load, update, and remove chunks as the viewer moves.

---

## The Core Idea

# An experimental demonstrator, not an open-world game

**Main user:** the person interacting with and evaluating the demonstrator.

- Move through the terrain; observe chunks and LOD change.
- Run or review controlled comparisons of the strategies.
- Record performance and complexity indicators.
- Document the limits of the implementation.

---

## Comparison / Trade-Offs

# Two strategies, compared on their trade-offs

**At least two** terrain-generation or LOD strategies, or variants, will be implemented and compared.

The comparison will consider:

- Visual fidelity
- Generation and update cost
- Memory use
- Loading responsiveness
- Geometric complexity

---

## Planned Scope / Implementation

# Terrain, chunks, and LOD

### Procedural generation
Terrain height or geometry.

### Chunk or tile management
Dynamic loading, updating, and removal.

### Custom LOD selection
Choose the detail level for terrain regions based on the viewer and system constraints.

### Incremental or asynchronous generation
Generate terrain in manageable steps or background tasks.

### Neighbouring chunks with different LODs
Crack prevention or crack measurement.

---

## Planned Scope / Experiments

# Controlled, reproducible experiments

### Vary

- View distance
- Camera movement
- Terrain size
- Chunk resolution
- Number of active chunks
- LOD thresholds
- Generation complexity

### Measure

- Generation time
- Frame time or CPU cost
- Memory use
- Geometry size
- Chunk-loading latency

Assess visual fidelity and geometric error where practical.

**Out of scope:** a complete open-world game.

---

## Journey 1 / Viewer

# Moving through the terrain

### 01 — Start
The viewer starts the demonstrator.

### 02 — Generate or load
The system prepares chunks around the viewer.

### 03 — Select detail
The custom LOD policy sets detail for active regions.

### 04 — Move
New chunks are requested and generated.

### 05 — Update and unload
The system updates LOD and unloads chunks that are no longer needed.

### 06 — Observe
The viewer observes the terrain and its responsiveness.

---

## Journey 2 / Operator

# Comparing terrain strategies

1. Select a strategy and a documented test configuration.
2. Display terrain and run a defined movement scenario.
3. Record performance and complexity measurements.
4. Repeat with another strategy under equivalent conditions.
5. Compare results and document trade-offs.

---

## Next Steps / Research and Design

# To be researched…

### 01 — Research terrain generation
Investigate procedural terrain-generation methods.

### 02 — Research LOD
Pick at least two strategies to compare.

### 03 — Choose the environment
Select a development environment that leaves room for the project's own contributions.

### 04 — Define representation
Define the chunk representation and terrain-generation pipeline.

### 05 — Define chunk management
Plan loading, updating, unloading, and asynchronous generation.

---

## Next Steps / Validate, Build, Compare

# Validate, build, compare

### 01 — Investigate boundaries
Study neighbouring chunks with different LODs.

### 02 — Define experiments
Specify parameters, scenarios, metrics, and the reproducibility procedure.

### 03 — Build a small prototype
Validate feasibility and collect baseline measurements.

### 04 — Implement and compare
Implement the approaches, run controlled experiments, and compare the results.
