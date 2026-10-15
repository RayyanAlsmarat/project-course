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

## 1. Project overview

A real-time demonstrator will generate a heightmap-based landscape, split it into chunks, stream chunks as the viewer moves, and adjust mesh detail. The central experiment compares a simple distance-based LOD policy with a policy that also considers local terrain roughness and estimated on-screen importance.

## 2. Terrain representation

- Each chunk covers a fixed world-space square and has a deterministic grid of height samples.
- A seeded, continuous 2D noise function determines heights from global coordinates so adjacent chunks share the same terrain surface.
- Meshes use multiple resolutions (for example, 65×65, 33×33, and 17×17 vertices, subject to profiling).
- Chunk identifiers are integer grid coordinates; terrain parameters and seeds are configurable.

## 3. Streaming pipeline

1. Determine required chunks around the camera using a configurable view radius.
2. Prioritize nearby or visible chunks for generation.
3. Generate height data and meshes incrementally, limiting work per frame.
4. Update the LOD of existing chunks when the selected policy requires it.
5. Reuse or release chunks outside the active radius and record loading latency.

If background generation is supported safely by the chosen framework, CPU-only height/mesh calculations may be scheduled off the main thread; otherwise the prototype will use a bounded incremental queue. Engine-specific rendering objects will be created on the appropriate thread.

## 4. LOD strategies

### A. Fixed distance bands (baseline)

Choose high, medium, or low mesh resolution using configurable camera-distance thresholds. This simple policy is easy to reproduce and measure.

### B. Roughness-aware priority (comparison)

Estimate a chunk's height variation or local geometric error, combine it with camera distance to produce a priority score, and allocate a higher mesh resolution when the projected benefit is larger. Thresholds and score normalization will be calibrated and reported.

Both policies operate on identical world seeds and chunk layouts. To avoid unstable switching, use hysteresis around LOD thresholds where needed.

## 5. Chunk boundary treatment

Adjacent chunks can have different mesh resolutions. Evaluate a practical boundary technique, such as mesh skirts or edge stitching, and inspect for gaps and abrupt transitions. Document any remaining artifacts and their conditions.

## 6. Functional requirements

- Start a world with selected seed and terrain parameters.
- Navigate with a movable camera.
- Load, update, and unload chunks automatically.
- Switch between the two LOD policies.
- Show or export basic statistics (active chunks, vertices/triangles, generation times, frame times).
- Run or replay the same camera route for fair comparison.

## 7. Experimental design

Use identical hardware, scene settings, seeds, chunk sizes, and camera paths for each policy. Test at least a few configurations of view radius, chunk resolution, and movement speed. Repeat measurements after warm-up and summarize distributions, not only single best values.

### Metrics

- Frame time (average, median, and high-percentile values) and frame-rate stability.
- Chunk height/mesh generation time and update count.
- Time from chunk request to visible display (loading latency).
- Active chunk count, vertex/triangle count, and approximate memory footprint.
- Visual difference against a higher-detail reference in selected viewpoints, where feasible.
- Number and severity of visible boundary artifacts, assessed with a documented procedure.

### Hypotheses

- The roughness-aware policy will allocate more detail to visually complex regions at similar geometry budgets.
- The adaptive policy may introduce additional CPU overhead and more frequent LOD changes.
- A bounded generation queue should reduce frame-time spikes at the cost of possible loading delays.

## 8. Validation and limitations

Check deterministic regeneration for a fixed seed, continuity of terrain heights at shared chunk borders, correct streaming after camera movement, and consistency of recorded metrics. Results will depend on hardware, camera route, scene complexity, and the chosen approximation of visual error; the project will not claim universal superiority of one policy.

## 9. Planned implementation milestones

1. Terrain sampling and single-chunk mesh prototype.
2. Multi-chunk streaming and camera navigation.
3. Baseline distance-based LOD.
4. Roughness-aware LOD and boundary handling.
5. Measurement collection and reproducible camera paths.
6. Parameter experiments, comparison, and final documentation.

**Technology decision:** The rendering framework and exact concurrency method will be finalized after an initial feasibility prototype. The methods and parameter values above are a proposed implementation plan, not already completed features.
