# F1 Circuits Hierarchical Clustering Analysis

This project performs hierarchical clustering analysis on Formula 1 circuits based on their physical characteristics and performance metrics. The analysis groups similar circuits together to identify patterns and relationships between different tracks.

## Overview

The analysis clusters F1 circuits using the following features:
- Full throttle percentage
- Number of turns
- Corner types (Sharp, Mid, Open)
- Average speed
- Corner speeds for different types

## Clustering Results Visualization

### Hierarchical Clustering Dendrogram
![Hierarchical Clustering Dendrogram](./figures/dendrogram.png)

The dendrogram above shows the hierarchical relationship between circuits, with the vertical axis representing the distance or dissimilarity between clusters. The colors indicate different main clusters identified in the analysis.

### Feature Importance Heatmap
![Feature Importance by Cluster](./figures/feature_importance.png)

The heatmap displays the relative importance of different features for each cluster, with darker blue indicating higher values and darker orange indicating lower values. This visualization helps understand what characteristics define each cluster.

### PCA Visualization
![Circuit Clusters PCA](./figures/pca_visualization.png)

The PCA plot shows the circuits projected onto two dimensions, with colors indicating cluster membership. This visualization helps understand the spatial relationships between circuits and clusters.

## Key Findings

The analysis identified 4 distinct clusters of circuits:

### Cluster 0 (High-Speed Technical Circuits)
- Largest group with 11 circuits including Circuit of the Americas, Silverstone, and Suzuka
- Characterized by:
  - Highest average full throttle percentage (61%)
  - Balanced mix of corner types
  - High average speed (225 km/h)
- Predominantly purpose-built race circuits (8 out of 11)

### Cluster 1 (Technical Circuits)
- 6 circuits including Monaco, Hungaroring, and Marina Bay
- Characterized by:
  - Lowest full throttle percentage (55%)
  - Lower average speeds (198 km/h)
  - More technical sections with emphasis on sharp corners
- Mix of street circuits and traditional race tracks

### Cluster 2 (High-Speed Circuits)
- 6 circuits including Monza, Barcelona, and Red Bull Ring
- Characterized by:
  - Highest full throttle percentage (69%)
  - Fewer total turns (13.5 average)
  - High average speed (241 km/h)
- Focus on speed with fewer technical sections

### Cluster 3 (Unique Case - Jeddah)
- Single circuit cluster
- Characterized by:
  - Extremely high number of turns (27)
  - Highest number of sharp corners (15)
  - Highest average speed (254 km/h)
- Unique combination of high-speed sections with technical complexity

## Code Structure

### Main Functions

1. `plot_dendrogram(X_scaled, df, max_d=None)`
   - Generates hierarchical clustering dendrogram
   - Helps visualize the clustering hierarchy
   - Optional cutoff line for cluster determination

2. `calculate_cophenetic_correlation(X_scaled, linkage_matrix)`
   - Evaluates clustering quality
   - Returns correlation coefficient between original and cophenetic distances

3. `perform_hierarchical_clustering(X_scaled, n_clusters)`
   - Executes the hierarchical clustering algorithm
   - Returns cluster labels for each circuit

4. `visualize_clusters_pca(X_scaled, df_clustered)`
   - Creates PCA visualization of clusters
   - Projects high-dimensional data onto 2D space
   - Includes circuit labels and color coding

5. `create_feature_importance_plot(X_scaled, numerical_columns, cluster_labels)`
   - Generates heatmap of feature importance by cluster
   - Helps interpret cluster characteristics

6. `analyze_clusters(df_clustered)`
   - Provides detailed statistical analysis of each cluster
   - Includes means, standard deviations, and circuit types

## Usage

```python
# Run the complete analysis
df_clustered = main(df, n_clusters=4)
```

## Dependencies

- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn

## Notes

- The analysis uses Ward's method for hierarchical clustering
- Features are scaled before clustering to ensure equal weighting
- PCA is used for visualization purposes only, clustering is performed on the full feature set

## Future Improvements

1. Include additional circuit characteristics:
   - Elevation changes
   - Weather conditions
3. Incorporate race performance statistics
4. Add interactive visualizations

## Contributing

Feel free to fork this repository and submit pull requests with improvements or additional analyses.
