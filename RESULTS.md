# Reported results and interpretation

Source: dissertation Section 4, Table 1, Figures 9-14, Tables 2-3 and Section 5. Timing and synthetic-check summaries were cross-checked against local evaluation records. Values below use the dissertation's rounded presentation. No new benchmarks were executed for this release.

## Benchmark efficiency

- **100 x 100:** research planner 1.1 ms and 76 expanded nodes; Euclidean A* 12.9 ms and 1,456 nodes. Approximately 11.7x speed-up.
- **200 x 200:** research planner 0.9 ms and 50 expanded nodes; Euclidean A* 5.0 ms and 624 nodes. Approximately 5.6x speed-up.
- **500 x 500:** research planner 3.7 ms and 231 expanded nodes; Euclidean A* 95.0 ms and 12,101 nodes. Approximately 25.7x speed-up.

Across these three recorded cases, rounded planning times total 5.7 ms versus 112.9 ms, approximately a 95.0% reduction. Expanded nodes total 357 versus 14,181, approximately a 97.5% reduction. These totals describe the selected benchmark cases, not an estimate of general field performance. The smaller runtime at 200 x 200 than at 100 x 100 also illustrates why grid size alone does not determine difficulty.

## Route quality and collision checks

Mean path-length deviation from Dijkstra was 0.33% across 15 random maps, compared with 0.00% for Euclidean A*. The evidence supports near-shortest routes on this sample, without proving universal optimality.

All seven synthetic scenario types passed the reported raw-route and accepted-smoothed-route occupancy checks. The separate fixed-configuration UAV evaluation reported feasible routes for all 12 tiles and collision-free accepted smoothing.

## Route smoothing

Mean waypoint count changed from 145 to 14, approximately a 90.3% reduction. Mean peak heading change changed from 41.3 to 24.6 degrees, approximately a 40.4% reduction. These metrics indicate simpler routes and less abrupt local turns; they do not by themselves demonstrate feasible vehicle dynamics or controller tracking accuracy.

## Inflation sensitivity

In the separate 12-tile sensitivity sweep:

- Zero-cell inflation: 12/12 routes (100%); mean clearance approximately 2.92 grid cells.
- One-cell inflation: 8/12 routes (66.7%); mean clearance approximately 5.31 grid cells.
- Two-cell inflation: 5/12 routes (41.7%); mean clearance 7.50 grid cells.
- Three-cell inflation: 3/12 routes (25%); mean clearance 10.00 grid cells.

Larger margins can close narrow corridors. Clearance values accompany different numbers of successful routes, so they should not be interpreted as identical-route paired improvements.

**Unit correction:** the local sensitivity CSV labels a clearance field as metres, but the dissertation explicitly reports grid cells because a resolution conversion is not documented. This public summary follows the dissertation. The original CSV is not redistributed.

**Distinct evaluations:** the one-cell sensitivity result (8/12) and the separate fixed-configuration feasibility result (12/12) must remain separately attributed. The released material does not establish an exact configuration-level reconciliation, so neither result is used to overwrite the other.

## Map density and simulation

The dissertation describes an overall positive association between occupied-area ratio and both planning latency and path length across the 12 UAV tiles, with substantial scatter and a latency outlier. No causal model or confidence interval is asserted here.

Reported Unity validation runs reached their goals without reported runtime collisions or field exits. A run count suitable for estimating reliability is not provided in this summary. Physical lateral error, heading error and hardware controller-tracking performance were not measured.

## Interpretation

The evidence supports a promising software prototype with reduced search effort in the selected benchmarks and a measurable clearance-versus-feasibility trade-off. It does not establish production readiness, physical robot safety, statistical generalisation or an algorithmic complexity guarantee.
