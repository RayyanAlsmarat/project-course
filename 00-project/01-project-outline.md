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

## Problem

Large game worlds require terrain to be generated and displayed without keeping maximum-detail geometry everywhere at once.

The project aims to generate terrain procedurally at runtime, divide it into manageable chunks, dynamically load and unload those chunks as the viewer moves, and change the level of detail according to the viewer's position and computational constraints.

The main objective is not only to build a working terrain system, but to implement and compare different terrain-generation and/or level-of-detail strategies and analyse their trade-offs in a controlled and measurable way.

The project will focus on the relationship between visual quality, generation and update cost, memory use, loading responsiveness, and geometric complexity.

## Target users

The project is an experimental terrain demonstrator rather than a complete open-world game.

The main user of the demonstrator will interact with the generated terrain and use the system to evaluate different terrain-generation and level-of-detail approaches.

The system will support evaluation of:

- visual fidelity
- terrain-generation and update cost
- memory consumption
- loading responsiveness
- generated geometry size
- geometric or visual error where practical

## Planned scope

The system will provide a working, version-controlled demonstrator for generating and displaying large procedural terrain regions in real time.

The planned system will include:

- procedural terrain height or geometry generation
- terrain divided into chunks or tiles
- dynamic chunk loading, updating, and removal as the viewer moves
- a custom level-of-detail selection mechanism
- at least two meaningful terrain-generation or LOD strategies, or variants, for comparison
- incremental or asynchronous terrain generation
- handling of neighbouring chunks with different levels of detail
- prevention or measurement and analysis of visible cracks and abrupt transitions

The exact terrain-generation and LOD strategies will be selected as part of the technical investigation before the main implementation.

The experimental system will allow controlled variation of parameters including:

- view distance
- terrain size
- chunk resolution
- number of active chunks
- LOD thresholds
- camera movement
- generation complexity

The evaluation will include objective measurements such as:

- terrain-generation time
- frame or CPU cost
- memory consumption
- generated geometry size
- chunk-loading latency
- visual fidelity
- geometric or visual error where practical

The project will focus on the terrain system and its evaluation. Building a complete open-world game is outside the scope.

## Initial user journeys

### Moving through the terrain

1. The viewer enters the generated terrain.
2. Terrain chunks around the viewer are generated or loaded.
3. An appropriate level of detail is selected for active regions.
4. The viewer moves through the terrain.
5. New chunks are generated or loaded as required.
6. Chunks that are no longer required are updated or removed.
7. Level of detail changes according to the viewer's position.

### Evaluating terrain strategies

1. Select one of the implemented terrain-generation or LOD approaches.
2. Generate and display the terrain.
3. Move through the terrain and observe its behaviour.
4. Measure the selected performance and complexity indicators.
5. Repeat the experiment with another strategy or parameter configuration.
6. Compare the results under controlled conditions.
7. Analyse the trade-offs between visual fidelity, performance, memory use, loading responsiveness, and geometric complexity.

## Next steps

1. Investigate suitable procedural terrain-generation methods.
2. Investigate meaningful LOD strategies or variants that can be implemented and compared.
3. Decide which terrain-generation and LOD approaches will be used.
4. Define the chunk representation and terrain-generation pipeline.
5. Define how chunks will be generated, loaded, updated, and removed as the camera moves.
6. Define how incremental or asynchronous generation will be handled.
7. Define how neighbouring chunks with different LODs will be connected and how cracks or abrupt transitions will be handled.
8. Define the experimental parameters and controlled test conditions.
9. Define the objective measurements and comparison criteria.
10. Prepare a reproducible experimental setup.
11. Implement the selected approaches and the terrain demonstrator.
12. Compare the approaches and analyse their practical trade-offs.
