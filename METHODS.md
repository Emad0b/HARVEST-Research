# Evaluation methods

This document describes the public experimental design without disclosing the private planner's implementation, formulae, tuning parameters or internal interfaces.

## Scope

The study evaluated a software prototype linking agricultural occupancy mapping, global route planning and simulated execution. It used synthetic field geometry and pre-labelled UAV crop/weed segmentation masks. It did not train or validate an end-to-end field perception system.

## Computational efficiency

Compare the research planner and Euclidean A* on 100 x 100, 200 x 200 and 500 x 500 benchmark grids. Record planning latency in milliseconds and the number of expanded nodes. The available timing record describes a single start-goal query per benchmark with 15% obstacles. These records do not establish runtime variance or statistical confidence across repeated hardware-controlled trials.

## Path-length quality

Compare route length with a Dijkstra reference under the same grid movement costs on 15 small random maps. Report percentage deviation from the reference length. The dissertation's target was less than 1% mean deviation; a low observed mean does not establish an optimality bound on unseen maps.

## Synthetic collision checks

Evaluate concave-field, corridor, crop-row, farm-plot, maze, obstacle-course and scattered-obstacle scenarios. Audit both raw routes and accepted smoothed routes against occupied grid cells. The unit of the published summary is scenario type, not a claim of seven statistically independent field trials.

## UAV-map feasibility and density

Evaluate 12 UAV tiles after conversion to crop-protective occupancy maps. Report whether routes exist and whether accepted smoothing passes occupancy-grid collision validation. Inspect occupied-area ratio alongside planning latency and path length. Density trends are descriptive associations; connectivity and obstacle arrangement also matter.

## Smoothing and clearance sensitivity

Compare waypoint count and peak heading change before and after smoothing. Separately vary obstacle inflation over zero, one, two and three cells, measuring route success and minimum clearance. The inflation sweep and the fixed-configuration feasibility evaluation are different records and must not be combined into one success rate.

Clearance in the public summary is expressed in grid cells. The dissertation notes that the sensitivity record does not document a reliable conversion to metres.

## Integration

Assess response completeness, goal completion, collision events and field-exit events during Python/Unity simulation. ROS-compatible offline map/path exports demonstrate an integration pathway, not live ROS hardware deployment.

## Reproducibility boundary

The source code, private planner details, exact experiment configurations, raw logs and original datasets are not released. This repository permits inspection of the reported experimental design and outcomes, but cannot reproduce the experiments independently. Results are attributed to the dissertation rather than represented as independently verified field performance.
