# Parn Experiment Progress Summary

## Project Goal
Use Bayesian optimization (Ax) to identify the best process parameters (R, W, D) that minimize a weighted residual-stress objective.

Objective definition:
- 0.6 x mean(diff_sigma_x for AA5052)
- 0.3 x mean(diff_sigma_x for AA6061)
- 0.1 x mean(diff_sigma_x for Center)

## Work Completed
- Loaded and inspected experimental data from `S01_residual_stress_merge.xlsx`.
- Aggregated raw measurements by `sample_no` and computed one objective per sample.
- Configured Ax search space (integer parameters):
  - R: 1200 to 2000
  - W: 50 to 100
  - D: 0 to 50
- Attached all historical trials to Ax and marked them complete.
- Retrieved best parameterization from the fitted model.
- Built 3D visualization of historical parameter landscape.
- Generated 5 next-trial recommendations.

## Key Results
- Historical samples used: 54
- Objective statistics:
  - Min: -13.9143
  - Mean: 10.7786
  - Max: 34.8143

Best observed parameter set:
- R = 1500
- W = 70
- D = 10

Top 5 lowest-objective historical points:
1. sample 40: R=1500, W=70, D=10, objective=-13.9143
2. sample 6: R=1400, W=70, D=20, objective=-10.4000
3. sample 2: R=1400, W=60, D=15, objective=0.0143
4. sample 28: R=1400, W=60, D=10, objective=0.2143
5. sample 20: R=1600, W=60, D=15, objective=1.0286

## Suggested Next Experiments (Ax)
1. R=1600, W=75, D=25
2. R=1720, W=93, D=38
3. R=1200, W=50, D=0
4. R=1200, W=50, D=50
5. R=1200, W=100, D=50

## Findings for Presentation
- The optimization pipeline is working end-to-end from raw data to next experiment suggestions.
- Current best region is near moderate R and W with relatively low D.
- The wide objective spread (~48.73 from min to max) indicates strong sensitivity to parameter choices.
- Suggested next trials mix center-space and boundary-space probing, balancing exploitation and exploration.

## Notes and Caveats
- Notebook outputs are large; key metrics above are based on reproducible execution of the same notebook logic and data path.
- Sensitivity/importance cards in Ax may require generation strategy initialization (e.g., by requesting next trials before analysis rendering).
