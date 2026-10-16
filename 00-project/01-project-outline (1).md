---
name: [Your Name]
neptun: [Your Neptun]
id: 2026-NP-03
github: [Your GitHub repository URL]
github_project: [Your GitHub project URL, if applicable]
supervisor: Péter NOVÁK
---
# Real-Time Procedural Terrain Generation and Level-of-Detail Management

This project investigates how large procedural terrain regions can be generated and displayed in real time without maintaining maximum-detail geometry everywhere. The system will generate terrain, manage it in chunks or tiles, load and remove chunks as the viewer moves, and select geometric detail according to viewer position and computational constraints. The result will be a working, version-controlled terrain demonstrator for comparing terrain-generation and level-of-detail (LOD) strategies under controlled conditions.

## Objectives
- **Primary objective:** Implement a real-time procedural terrain demonstrator with chunk management and a custom LOD selection mechanism.
- **Research objective:** Implement and compare at least two terrain-generation or LOD strategies, or meaningful variants, and analyse their visual and performance trade-offs.
- **Target users / stakeholders:** The student developing the system and the people evaluating the demonstrator and its experimental results.
- **Measurable success criteria:** The demonstrator generates and displays terrain, loads/updates/removes chunks as the viewer moves, selects LOD for active regions, and supports reproducible comparisons using performance and complexity measurements.
- **Required measurements:** Generation time, frame or CPU cost, memory consumption, generated geometry size, and chunk-loading latency. Visual fidelity and geometric/visual error will also be considered where practical.
- **Constraints:** Use a suitable implementation language and optionally a game engine for visualization and scene management. Built-in terrain generation or automatic LOD must not provide the central thesis contribution. Maintain the source in a Git-based repository and make experiments reproducible.

## Scope
### In scope
- Procedural terrain height or geometry generation.
- Terrain chunk/tile representation and management.
- Dynamic chunk loading, updating, and unloading as the viewer moves.
- A custom LOD selection mechanism.
- At least two meaningful terrain-generation or LOD strategies, or variants, for comparison.
- Incremental or asynchronous generation.
- Handling of continuity between neighbouring chunks with different LODs.
- Prevention of visible cracks/abrupt transitions, or measurement and analysis of them.
- Controlled experiments varying view distance, camera movement, terrain size, chunk resolution, active chunk count, LOD thresholds, and generation complexity.
- Reproducible performance and complexity measurements.

### Out of scope
- Building a complete open-world game.
- Treating an engine's built-in terrain generation or automatic LOD as the central project contribution.
- Optional extensions that are not needed to meet the required scope, such as additional strategies beyond the comparison set or more extensive error analysis.

## Notes
The specific terrain-generation methods, LOD strategies, chunk representation, transition technique, and asynchronous-generation approach are decisions to be made during the technical investigation before the main implementation. Candidate approaches must be evaluated for feasibility and suitability rather than presented as already-final decisions.
