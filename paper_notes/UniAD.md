# [Planning-oriented Autonomous Driving](https://arxiv.org/abs/2212.10156)


TL;DR: Proposes UniAD, a unified framework to propagate the queries from  perception to prediction and to planning, making the planning error differentiable to prediction and perception in training phase. 


## Overview
- propagate the query from perception to prediction/planning, instead of using the intermediate results (e.g., Agent Bboxes, lanelines, Prediction trajectories) as the input to the next stage.
- the planning error is differentiable to the perception and prediction modules in training phase.
- the perception and prediction modules are optimized with both their own supervisions and the supervision from planning module.

## Architecture
- backbone: 3D sparse convnet to extract BEV features from multi-view images.
- auxiliary tasks: 
  - dynamamic agent detection/tracking in BEV space. (input: image perspective features + BEV features, output: agent queries)    
  - map element detection/tracking in BEV space. (input: image perspective features + BEV features, output: map queries)
  - prediction of future trajectories of detected agents. (input: agent queries + map queries, output: agent future trajectories queries)
  - occupancy prediction in BEV space. (input: BEV features + agent queries, output: occupancy grid queries)

- planning (input: BEV features + agent queries + map queries + predicted agent future trajectories, output: planned trajectory queries)
  