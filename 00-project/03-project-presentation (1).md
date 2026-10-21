---
project_outline: "[[01-project-outline]]"
---

<!-- 3xl -->
# Real-Time Procedural Terrain Generation and Level-of-Detail Management

Rayyan Alsmarat · Y0J3P8

Supervisor: Péter NOVÁK  
Project ID: 2026-NP-03

---

<!-- 2xl -->
## The Challenge

Large worlds cannot keep every terrain area at maximum detail.

- Generate terrain procedurally
- Load and update nearby chunks
- Choose detail based on viewer position
- Keep rendering responsive

---

<!-- 2xl -->
## The Core Idea

Build an **experimental terrain demonstrator**, not a complete open-world game.

- Move through generated terrain
- Observe chunks and level of detail (LOD) changing
- Run controlled tests
- Record performance and limitations

---

<!-- 2xl -->
## Comparison and Trade-Offs

Compare at least **two terrain-generation or LOD strategies/variants**.

Evaluate:

- Visual fidelity
- Generation and update cost
- Memory use
- Chunk-loading responsiveness
- Geometry complexity

---

<!-- 2xl -->
## Planned Scope: Implementation

- Procedural terrain height or geometry
- Chunk/tile management
- Custom LOD selection
- Incremental or asynchronous generation
- Load, update, and remove chunks as the viewer moves
- Handle boundaries between chunks with different LODs

---

<!-- 2xl -->
## Planned Scope: Experiments

Run repeatable tests while varying:

- View distance and camera movement
- Terrain size and chunk resolution
- Number of active chunks
- LOD thresholds and generation complexity

**Measure:** generation time, frame/CPU cost, memory, geometry size, and chunk-loading latency.

Assess visual/geometric error where practical.

---

<!-- 2xl -->
## User Journey 1: Explore Terrain

1. Start or reset the demonstrator.
2. Generate or load nearby chunks.
3. Select LOD for active chunks.
4. Move through the terrain.
5. Generate new chunks and unload distant ones.
6. Observe visual quality and responsiveness.

---

<!-- 2xl -->
## User Journey 2: Compare Strategies

1. Select a strategy and test configuration.
2. Run a defined movement scenario.
3. Record performance and complexity metrics.
4. Repeat with another strategy under the same conditions.
5. Compare results and document trade-offs.

---

<!-- 2xl -->
## Next Steps: Research and Design

- Research procedural terrain methods
- Identify at least two LOD strategies or meaningful variants
- Choose a suitable language and environment
- Define chunk representation and generation pipeline
- Investigate transitions between different LOD levels

---

<!-- 2xl -->
## Next Steps: Build and Validate

- Define test scenarios, parameters, and metrics
- Prototype the terrain and chunk pipeline
- Establish baseline measurements
- Implement the selected approaches
- Run controlled experiments
- Compare results and document limitations
