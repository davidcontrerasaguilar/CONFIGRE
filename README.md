# CONFIGRE
## DATASETS
We used two datasets:
* (1) the **MovieLens-1M (Movies)** extended to integrate the continent and the country of production of each movie, it provides 1M ratings (range 1-5), provided by 6,040 users, to 3,600 movies, 54 countries, and 6 continents; 
* (2) a new created dataset called **DataSongs (Songs)**, which contains 1,777,981 ratings (range 1-5), provided by 30,759 users, to 16,380 songs, 62 countries, and 6 continents. 

## EXPERIMENTAL SETUP
To run the recommendation models presented in the paper, we used the Cornac framework, which generated the recommendations for each user and it generates consistently formatted lists that can be fed to CONFIGRE, P-Fair, and CP-Fair. In addition, datasets were randomly separated into a test set (20%) and a train set (80%).

We have performed a grid search of the hyper-parameters for each recommendation model in the two datasets. 
In Movies and Songs, for the ItemKNN and UserKNN:
* **ItemKNN**. *neighbors*=50, *similarity*=cosine, and *implementation*=classical.
* **UserKNN**. *neighbors*=50, *similarity*=cosine, and *implementation*=classical.

We defined a different configuration for **BPR** and **SVD** on each dataset.
* **BPR in Movies**. *epochs* = 10, *batch size* = 1, *factors* = 10, *learning rate* = 0.1, *bias regularization* = 0.01, *user regularization* = 0.01, *positive item regularization* = 0.01, *negative item regularization* = 0.01
* **SVD in Movies**. *epochs* = 10, *batch size* = 512, *factors* = 10, *learning rate* = 0.001, *bias regularization* = 0.001, *user regularization* = 0.001, *positive item regularization* = 0.01, *negative item regularization* = 0.01,

* **BPR in Songs**. *epochs* = 10, *batch size* = 1, *factors* = 10, *learning rate* = 1.346, *bias regularization* = 1.326, *user regularization* = 1.575, *positive item regularization* = 1.376, *negative item regularization* = 1.624
* **SVD in Songs**. *epochs* = 10, *batch size* = 512, *factors* = 10, *learning rate* = 0.01, *bias regularization* = 0.01, *user regularization* = 0.01, *positive item regularization* = 0.01, *negative item regularization* = 0.01,

For each user, we generated the *top-1000* recommendations (denoted in the paper as the top-𝑛) to then re-rank the *top-𝑘* (set up to 10) through the proposed CONFIGRE algorithm.
To evaluate recommendation effectiveness, we measure the ranking quality of the lists by measuring the Normalized Discounted Cumulative Gain (NDCG) [19]
