---
layout: page
title: Learning-guided ALNS
description: Warm-starting and guiding Adaptive Large Neighborhood Search with learned policies
img: assets/img/projects/alns.png
importance: 2
category: research
related_publications: true
---

**Idea.** Construction policies learned by reinforcement learning produce good solutions quickly, while Adaptive Large Neighborhood Search (ALNS) is strong at improving them. Combining the two lets the metaheuristic start from a better point and converge faster.

**Applications.**

- _Heterogeneous-fleet routing:_ the trained LA-HRL policy serves as a warm-start seed generator for ALNS on the FSMVRP {% cite ngo2026hybridalns %}.
- _Batch scheduling:_ deep reinforcement learning guides ALNS for parallel batch processing machine scheduling with incompatible job families {% cite ngo2026bpm %}.

**ALNS design for the FSMVRP.** Destroy operators include random, Shaw-similarity, worst-detour, route, neighbour-route and vehicle-type removal; repair uses regret-based insertion and cross-exchange. Operators are picked by a segmented roulette wheel, and moves are accepted by simulated annealing with exponential cooling.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/alns.png" alt="ALNS removes customers from routes and reinserts them during repair" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Illustration only: customers removed by a destroy operator and reinserted by a repair operator.
</div>
