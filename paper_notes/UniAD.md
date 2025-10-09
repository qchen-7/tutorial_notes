# [Planning-oriented Autonomous Driving](https://arxiv.org/abs/2212.10156)


TL;DR: UniAD, a unified framework to propagate the queries from  perception to prediction and to planning, making the planning error differentiable to prediction and perception in training phase. 


## Overview
- propagate the query from perception to prediction/planning, instead of using the explicit intermediate results (e.g., Agent Bboxes, lanelines, Prediction trajectories) as the input to the next stage.
- the perception and prediction modules are optimized with both their own supervisions and the supervision from planning module.

## Architecture
- backbone: ResNet + FPN(perspective feature), to BEV feature: view transformer + deformable attention
- auxiliary tasks: 
  - dynamamic agent detection/tracking in BEV space. (input: image perspective features + BEV features, output: dynamamic agent queries)    
  - map element detection/tracking in BEV space. (input: image perspective features + BEV features, output: map queries)
  - prediction of future trajectories of detected agents. (input: agent queries + map queries, output: agent future trajectories queries)
  - occupancy prediction in BEV space. (input: BEV features + agent queries, output: occupancy grid queries)

- planning (input: BEV features + agent queries + map queries + predicted agent future trajectories, output: planned trajectory queries)

## Losses
- perception loss: detection + tracking losses
- prediction loss: $$L_1$$ loss between predicted trajectories and GT trajectories
- occupancy loss: $$BCE$$ loss between predicted occupancy grid and GT occupancy grid
- planning loss: $$L_1$$ loss between planned trajectory and GT trajectory + collision loss + smoothness loss
- total loss: weighted sum of all losses
  

## Highlights
- a good design of query propagation from perception to prediction and planning.
- utilize a dense occupancy representation of the environment to assist planning.
- the planning loss use a single modal trajectory output

## Notes
- the idea of query propagation is interesting
- the perception range is relatively small for autonomous driving.