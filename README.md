# CONFIGRE
## DATASETS
In our experiments, We used two ```datasets```, which are available in the ```Movies``` and ```Songs``` folders:
* (1) the **MovieLens-1M (Movies, ```items.csv```)** extended to integrate the continent and the country of production of each movie, it provides 1M ratings (range 1-5), provided by 6,040 users, to 3,600 movies, 54 countries, and 6 continents; 
* (2) a new created dataset called **DataSongs (Songs, ```songs.csv```)**, which contains 1,777,981 ratings (range 1-5), provided by 30,759 users, to 16,380 songs, 62 countries, and 6 continents. 

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
To evaluate recommendation effectiveness, we measure the ranking quality of the lists by measuring the Normalized Discounted Cumulative Gain (NDCG)

## CITATION
If you use our source datasets, and experiments for your research or development, please cite the following paper

@inproceedings{10.1145/3627043.3659552,  
author = {G\'{o}mez, Elizabeth and Contreras, David and Salamo, Maria and Boratto, Ludovico},  
title = {Bringing Equity to Coarse and Fine-Grained Provider Groups in Recommender Systems},  
year = {2024},  
isbn = {9798400704338},  
publisher = {Association for Computing Machinery},  
address = {New York, NY, USA},  
url = {https://doi.org/10.1145/3627043.3659552},  
doi = {10.1145/3627043.3659552},  
abstract = {Provider fairness aims at regulating the recommendation lists, so that the items of different providers/provider groups are suggested by respecting notions of equity. When group fairness is among the goals of a system, a common way is to use coarse groups since the number of considered provider groups is usually small (e.g., two genders, or three/four age groups) and the number of items per group is large. From a practical point of view, having few groups makes it easier for a platform to manage the distribution of equity among them. Nevertheless, there are sensitive attributes, such as the age or the geographic provenance of the providers that can be characterized at a fine granularity (e.g., one might group providers at the country level, instead of the continent one), which increases the number of groups and decrements the number of items per group. In this study, we show that, in large demographic groups, when considering coarse-grained provider groups, the fine-grained provider groups are under-recommended by the state-of-the-art models. To overcome this issue, in this paper, we present an approach that brings equity to both coarse and fine-grained provider groups. Experiments on two real-world datasets show the effectiveness of our approach.},
booktitle = {Proceedings of the 32nd ACM Conference on User Modeling, Adaptation and Personalization},  
pages = {18–23},  
numpages = {6},  
keywords = {Bias, Disparate Impact., Geographic Groups, Provider Fairness, Recommender systems},  
location = {Cagliari, Italy},  
series = {UMAP '24}  
}

## CONTACT
If you have any questions, do not hesitate to contact us by david.contreras@unap.cl or egomezy109@gmail.com, we will be happy to assist.
