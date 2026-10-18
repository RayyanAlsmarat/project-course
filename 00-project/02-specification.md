---
project_outline: "[[01-project-outline]]"
---
# Real-Time Procedural Terrain Generation and Level-of-Detail Management

## 1. Actors and permissions

| Role | Needs | Responsibility / access |
| --- | --- | --- |
| Viewer / experiment operator | Navigate generated terrain and observe chunk and LOD behaviour | Moves the camera/viewer and selects available test configurations |
| Student / developer | Implement and evaluate the terrain system | Designs the algorithms, runs experiments, records results, and maintains the repository |
| Project supervisor / evaluator | Assess the implementation and evidence | Reviews the technical decisions, reproducibility, and experimental findings |

## 2. Use cases / user stories

### Explore a procedural terrain region

- **Actor:** Viewer / experiment operator
- **Precondition:** The terrain demonstrator is running and a test configuration is available.
- **Main flow:**
  1. The viewer starts or resets a terrain session.
  2. The system generates or loads the terrain chunks needed around the viewer.
  3. The system selects a level of detail for active chunks according to the implemented LOD policy.
  4. The viewer moves through the terrain.
  5. The system requests and generates newly needed chunks.
  6. The system updates LOD where required and unloads chunks that are no longer needed.
  7. The viewer observes terrain appearance and responsiveness.
- **Alternative / error flows:** If a chunk is not ready immediately, the system should handle the pending work without corrupting the terrain state; the exact fallback behaviour is a design decision to specify.
- **Postcondition:** The terrain around the viewer is updated, and the session can provide data for evaluation.

### Run and compare terrain/LOD strategies

- **Actor:** Student / experiment operator
- **Precondition:** At least two meaningful strategies or variants have been implemented and the test parameters are defined.
- **Main flow:**
  1. The operator selects a strategy and experiment configuration.
  2. The system generates or displays terrain using that configuration.
  3. The operator runs the defined camera/view scenario.
  4. The system records the selected performance and complexity metrics.
  5. The experiment is repeated for the other strategy under equivalent conditions.
  6. Results are compared by visual fidelity, generation/update cost, memory use, loading responsiveness, and geometric complexity.
- **Alternative / error flows:** If a run is interrupted or its measurements are incomplete, the run is marked invalid and repeated rather than compared as a complete result.
- **Postcondition:** The experiment produces comparable records and documented observations.

## 3. Functional requirements

| Requirement | Acceptance criteria | Priority |
| --- | --- | --- |
| The system generates terrain procedurally. | Given a valid terrain configuration, the system produces and displays terrain height or geometry without relying on built-in terrain generation as the central contribution. | Must |
| The system represents terrain in chunks or tiles. | The generated terrain is divided into identifiable regions that can be managed independently. | Must |
| The system loads, updates, and removes chunks as the viewer moves. | During a movement scenario, newly needed chunks are requested and chunks no longer required can be removed or unloaded. | Must |
| The system uses a custom LOD selection mechanism. | Active terrain regions receive a detail level according to a documented policy implemented by the project. | Must |
| The system supports at least two strategies or meaningful variants. | The operator can run both approaches under defined test configurations. | Must |
| The system supports incremental or asynchronous generation. | Chunk generation work can be scheduled or processed incrementally/asynchronously according to the selected design. | Must |
| The system addresses transitions between neighbouring chunks with different LODs. | Cracks/abrupt transitions are prevented, or their occurrence is measured and analysed. | Must |
| The system supports controlled experiments. | Relevant parameters can be changed systematically, including view distance, camera movement, terrain size, chunk resolution, active chunk count, LOD thresholds, and generation complexity. | Must |
| The system records performance and complexity indicators. | Each valid run records generation time, frame or CPU cost, memory consumption, generated geometry size, and chunk-loading latency. | Must |
| The system supports visual/geometric comparison where practical. | The evaluation defines and applies a suitable method for assessing visual fidelity or geometric/visual error, or documents the practical limits if a measure is not feasible. | Should |
| The project is maintained in version control. | Source code and experiment instructions are maintained in a Git-based repository without secrets or access tokens. | Must |

Priority: **Must** = required for the project scope; **Should** = required where practical or important to the evaluation.

## 4. Business rules and constraints

| Rule or constraint | Rationale |
| --- | --- |
| At least two meaningful terrain-generation or LOD strategies, or variants, must be compared. | A central objective is to analyse trade-offs rather than only demonstrate one approach. |
| The LOD selection mechanism must be implemented as part of the project. | Built-in automatic LOD must not provide the central thesis contribution. |
| Built-in terrain generation must not provide the central thesis contribution. | The project must demonstrate and explain its own terrain-generation decisions. |
| Chunk loading, updating, and unloading must respond to viewer movement. | Dynamic terrain management is a required part of the demonstrator. |
| Transitions between different LODs must be addressed. | Neighbouring chunks with different detail levels can show cracks or abrupt transitions. |
| Experiments must be controlled and reproducible. | Results from different strategies need to be comparable. |
| The project is a terrain demonstrator, not a complete open-world game. | Keeps the implementation focused on terrain generation, LOD management, and evaluation. |
| The student must understand and be able to modify submitted work. | AI-assisted development is permitted, but the implementation must be explainable and modifiable. |

## 5. User interface and workflow

The demonstrator should provide a view of the generated terrain and allow the viewer/operator to move the camera through it. The workflow should make it possible to observe terrain chunks being generated, updated, or removed and to see the effect of the selected LOD policy.

An experimental workflow should allow the operator to select a strategy and configure relevant parameters, run a repeatable scenario, and inspect the resulting measurements. The exact interface controls and visual presentation remain design decisions.

A practical workflow is:

1. Choose a strategy and parameter configuration.
2. Start or reset the terrain session.
3. Run a defined camera movement or observation scenario.
4. Record performance, memory, geometry, and loading measurements.
5. Repeat with another strategy or configuration.
6. Compare results and document limitations.

## 6. Non-functional requirements

| Requirement | How it will be verified |
| --- | --- |
| Real-time responsiveness | Record frame-time or CPU-cost behaviour during defined movement scenarios. Establish acceptable thresholds after an initial baseline test. |
| Bounded resource use | Measure memory consumption and generated geometry size under different terrain and chunk configurations. |
| Loading responsiveness | Measure chunk-loading latency during repeatable camera movement. |
| Visual continuity | Inspect and/or measure boundaries between neighbouring chunks at different LODs; document whether cracks are prevented or analysed. |
| Reproducibility | Document the tested configuration, strategy, parameters, scenario, and measurement procedure so runs can be repeated. |
| Comparability | Run strategies under equivalent conditions and use the same measurement definitions for each. |
| Maintainability | Keep source code and experiment instructions in a Git-based repository. |
| Explainability | Document the main algorithms and design decisions so the student can explain and modify them. |

Numerical performance targets are not set yet; they should be defined after an initial prototype and baseline measurements rather than invented before the implementation environment is known.

## 7. Open questions and risks

| Question / risk | Impact | Owner | Resolution / decision |
| --- | --- | --- | --- |
| Which procedural terrain-generation method should be used? | Affects terrain appearance, generation cost, and implementation effort | Student | Research candidate methods and compare their suitability before implementation. |
| Which two LOD strategies or meaningful variants should be compared? | Defines the main experimental comparison | Student | Evaluate candidate approaches by visual fidelity, update cost, memory use, responsiveness, and complexity. |
| What chunk size and representation should be used? | Affects geometry size, scheduling overhead, and loading behaviour | Student | Prototype candidate chunk configurations and include chunk parameters in experiments. |
| How should LOD be selected? | Affects visual quality and computational cost | Student | Define and document a custom selection policy based on the investigated approach. |
| How will neighbouring LOD levels connect? | Poor transitions may create cracks or visible discontinuities | Student | Investigate transition techniques; select a method or define how defects will be measured and analysed. |
| How should incremental/asynchronous generation be scheduled? | Affects responsiveness and chunk-loading latency | Student | Prototype a suitable work-scheduling approach and measure its impact. |
| How will visual/geometric error be measured? | Affects the objectivity of quality comparisons | Student | Research feasible metrics and document the chosen method and its limits. |
| Which engine and language should be used? | Affects development workflow and measurement options | Student | Choose a suitable environment while ensuring built-in terrain/automatic LOD is not the central contribution. |
| How will experiments remain repeatable? | Uncontrolled runs can make comparisons unreliable | Student | Fix and record test scenarios, parameter settings, and measurement procedures. |
