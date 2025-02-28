# Premier League Player Clustering

## Overview

This project uses Principal Component Analysis (PCA) and K-means clustering to split Premier League players into clusters based on their detailed playing statistics. I created clusters both within the overall player dataset and within smaller datasets of players from each outfield position.

## Table of Contents

- Overview
- Dataset
- Model Training
- Evaluation
- Results
- Contributing
- License

## Dataset

I used individual player data from the 2024/25 Premier League season, collected from the following site: https://fbref.com/en/comps/9/Premier-League-Stats

The data is taken after 25 matches of the season and all statistics are on a per 90 minutes basis.

There were separate datasets on the following types of metrics: standard, shooting, possession, passing_types, passing, miscellaneous, goal creation, defensive.

I merged all of the individual datasets into one master dataset with 99 features.

## Model Training

I standardised my features and used PCA to reduce the dimensionality of the dataset. I then applied K-means clustering to split the players into clusters, using the elbow chart and silhouette score to inform the most appropriate number of clusters. 

I carried out PCA and K-means clustering both on the dataset as a whole and separately for players in each position. The reason for this is that by using players of all positions the clusters are likely to simply encode playing position, whereas creating clusters within a single position could provide insight into player attributes and tactical differences.

In each case, I chose to use a number of principal components to explain 80% of the variation in the dataset. This resulted in reducing the dimensinality from 99 features to between 14 and 17 principal components. Using the ful dataset, I found that the silhouette score using the same number of clusters was higher when using the dataset with reduced dimensionality as this reduced a lot of the unecessary nouise.

![image](https://github.com/user-attachments/assets/a3526fb1-06d0-45b7-bb88-540c5a869b95)


## Evaluation

I evaluated the quality of separation achieved using the silhouette score, however this was generally optimised by using k=2 and I wanted to gain more insight by using a larger number of clusters. Asides from my analysis of midfielders (where I used k=2) the silhouette score was always under 0.25, indicating a fairly poor level of separation.

I used a pair plot to visualise the separation between clusters in my overall dataset by plotting values of my first three principal components against each other. There was reasonable separation between clusters, especially when plotting PC1 against PC2, however also significant overlap.

![image](https://github.com/user-attachments/assets/dfc3eae0-99a4-4974-926b-075a8c2c53b1)


## Results

The heatmaps for the clusters in each of my datasets are shown below.

![image](https://github.com/user-attachments/assets/2ef2bdff-1590-4cd5-9cd5-17a93ed2d8ac)

![image](https://github.com/user-attachments/assets/c1494b1f-b68d-4a0a-97ef-2cf64dc4e433)

![image](https://github.com/user-attachments/assets/ec94dd1a-6116-4fd2-b6b0-a0e34c319bf1)

![image](https://github.com/user-attachments/assets/dfd2af57-fee5-4e1d-a3d6-05ab47b52f44)

For the overall dataset, the clusters largely encode a player's position. For the individual position, the clusters encode a more specific position (e.g. centre backs vs full backs, central strikers vs wide forwards). My most interesting finding was that centre backs could be separated quite clearly based on the team that they play for - better teams' centre backs tend to play out from the back and complete more mid-distance and progressive passes, whereas bottom half teams' centre backs make more clearances and block more shots. The split between clusters 0 and 1 for defenders by team is shown below.

![image](https://github.com/user-attachments/assets/e6abffe4-af6e-4651-8b65-ebae8c908258)


## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes.

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.


