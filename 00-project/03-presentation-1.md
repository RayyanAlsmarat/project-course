---
project_outline: "[[00-project/01-project-outline]]"
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

## Procedural terrain generation

- Generates terrain automatically from algorithms and parameters.
- Uses a deterministic world seed for repeatable experiments.
- This project uses a heightmap divided into chunks.

---

## Problem

- Large worlds cannot efficiently keep every region at maximum detail.
- Moving viewers require new terrain to appear quickly.
- Abrupt LOD changes can create visual artifacts and frame-time spikes.
- We need measurable comparisons between terrain detail policies.

---

## Target users

- Game developers exploring large-world rendering.
- Students and researchers studying procedural generation.
- Developers comparing performance and visual quality.

---

## Planned scope

- Seeded procedural heightmap terrain.
- Chunk-based loading and unloading around a moving camera.
- Multiple mesh resolutions and configurable view distance.
- Two LOD strategies, boundary handling, and performance logging.

---

## Terrain and chunk model

- The world is split into square chunks identified by grid coordinates.
- Global noise coordinates help neighbouring chunks align.
- Each chunk can be displayed at high, medium, or low resolution.

---

## Strategy 1: Distance-based LOD

- High detail near the camera.
- Medium detail at intermediate distances.
- Low detail farther away.
- Provides a simple baseline for comparison.

---

## Strategy 2: Roughness-aware LOD

- Considers camera distance and terrain height variation.
- Gives extra detail to complex terrain where useful.
- May improve visual allocation but adds selection overhead.

---

## Streaming and transitions

- Request new chunks as the camera moves.
- Limit generation work per frame to avoid large stalls.
- Unload chunks outside the active area.
- Test skirts or edge stitching for different-resolution neighbours.

---

## Evaluation metrics

- Frame time and frame-time spikes.
- Chunk generation time and loading latency.
- Number of active chunks and mesh triangles.
- Approximate memory usage.
- Visual differences and boundary artifacts.

---

## Research question

Can a roughness-aware LOD policy preserve more visible terrain detail than fixed distance bands at a comparable rendering budget, and what additional CPU or loading cost does it introduce?

---

## Experiment plan

1. Keep the same world seed, hardware, and camera path.
2. Run both LOD policies under matching settings.
3. Repeat for different view distances and chunk resolutions.
4. Compare distributions of performance and visual-quality measures.
5. Explain trade-offs and limitations.

---

## Next steps

1. Choose the rendering framework and prototype one terrain chunk.
2. Add camera-based chunk streaming.
3. Implement both LOD policies.
4. Test boundaries and collect repeatable measurements.
5. Analyze results and prepare the final demonstration.
