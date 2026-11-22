---
layout: page
title: LA-HRL for heterogeneous-fleet routing
description: Hierarchical reinforcement learning for the Fleet Size and Mix Vehicle Routing Problem
img: assets/img/projects/lahrl_framework.png
importance: 1
category: research
related_publications: true
---

**Problem.** In the Fleet Size and Mix Vehicle Routing Problem (FSMVRP) a planner decides which vehicle types to use, how many of each, and how to route them, trading fixed vehicle costs against travel costs.

**Approach.** A Lookahead-Aware Hierarchical Reinforcement Learning (LA-HRL) framework {% cite ngo2026lahrl %}. Each route independently selects its vehicle type, so the model never has to track individual vehicles:

- a **fleet decoder** chooses the vehicle type for the next route,
- a **route decoder** constructs that route customer by customer,
- a learned **future-cost estimate** gives both decisions a lookahead signal.

The encoder–decoders are attention-based (GAT, POMO-style) and trained end to end with PPO in PyTorch, using a POMO baseline.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/lahrl_framework.png" alt="Candidate vehicles, the employed fleet, and routes from a single depot" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    The FSMVRP setting: choose vehicle types from the candidate set, form the employed fleet, and route it from a single depot.
</div>
