<!-- <div id="top">   -->
# [Diffusion-ES: Gradient-free Planning with Diffusion for Autonomous Driving and Zero-Shot Instruction Following](https://arxiv.org/abs/2402.06559)


TL;DR: initial proposal(use diffusion model)--> score smaples(R(x)) --> samples selection([[MPPI]](https://arxiv.org/abs/1509.01149)) --> mutate samples(renoise and denoise using trucated diffusion model) --> repeat


## Overview
- reward-gradient guided denoise requires a differentiable reward function, which is not always available in real-world scenarios.
- propose Diffusion-ES,  combines
  -  gradient-free optimization 
  -  trajectory denoising 
  -  to achieve planning without a differentiable reward function.
-  diffusion-based generative models & sample-based optimization methods
  -  diffusion models: learn to generate samples from a data distribution by iteratively denoising from Gaussian noise.
  -  sample-based optimization methods: optimize a set of samples by iteratively updating them based on their rewards.

## Architecture


## Losses


## Highlights
  

## Notes
  