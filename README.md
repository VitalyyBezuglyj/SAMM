# Semantic Aware Map Metrics

This is the repository of the paper Reconstruction of 3D Semantic Map and Its Quality Estimation.

Here are several tools for calculating quality metrics to reconstruct 3D surface maps with/without semantics described in the paper. There are also several scripts for visualizing map quality.


Here is an example comparison of the quality of two different maps in the same places:

![Comparison of the quality of two different maps in the same places](pictures/map_quality_visualization.png)



## Metrics

For map evaluation, the following metrics are used:

- Precision

- Recall

- F-Score

- Chamfer Distance

- Hausdorf Distances

The mathematical calculations are as follows

### Basics

The quality evaluation of a 3D map comes down to evaluating the proximity of two point clouds. LiDAR data (randomly selected from) is used as gt, points randomly selected on the map are used as "Map points".

The shortest distances between the point clouds are used as the base values for calculating the metrics. Namely, the following values are calculated:

- Array of shortest distances from map points to the gt points $$D_{forward} = d(m,G_l) d(m,G_l) \gets \min_{g\in G}\|m-g\|_2$$

- Array of shortest distances from gt points to the map points $$D_{backward} = d(g,M_l) = d(g,M_l)\gets \min_{m\in M}\|m-g\|_2$$

### Metrics itself

- Precision $$P = \frac{100}{|M_l|}\cdot \sum_{m\in M_l}\left[ d\left(m,G_l\right) < d \right]$$

- Recall $$R = \frac{100}{|G|}\cdot \sum_{g\in G}\left[d\left(g,M\right) < d\right]$$

- F-Score $$F = \frac{2\cdot P(d)\cdot R(d)}{P(d)+R(d)}$$

- Chamfer Distance $$CD = \frac{1}{2|G|}\cdot \sum_{g\in G}\left(g,M\right)^2 + \frac{1}{2|M|}\cdot \sum_{m\in M}\left(m,G\right)^2$$

- Forward Hausdorff Distance $$HD^{forward} = \max_{m\in M}d\left(m,G\right)$$

- Backward Hausdorff Distance $$HD^{backward} = \max_{g\in G}d\left(g,M\right)$$


Each metric is calculated separately for each semantic class.

_More details, requirements and HOW-TO will be available soon_
