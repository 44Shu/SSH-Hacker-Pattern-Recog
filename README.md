# ssh-readme
### Abstract:
#### Use the following methodology
* PCA
* K-means Clustering
* Hamming Distance
* Damerau–Levenshtein distance
 	
  This project determines the password’s security by comparing its patterns with the dataset using the K-means process to sort out 8 clusters and found their corresponded central passwords. We present our results in a visualized distance comparison to the 8 centers through the use of Damerau–Levenshtein distance and Hamming Distance. 
 
### Contributors:
Anthony Yang <br />
Weijie Chen<br />
Shuyun Tang <br />
Jonathan Lin <br />
Ximei Wu <br />

### Motivations:
For cybersecurity purposes, we want to analyze the hackers' passwords patterns and give the users reasonable and reliable feedback on their passwords settings based on our patterns comparison. 
Worldwide spending on cybersecurity is forecasted to reach $133.7 billion in 2022. (Gartner)
62% of businesses experienced phishing and social engineering attacks in 2018. (Cybint Solutions)
68% of business leaders feel their cybersecurity risks are increasing. (Accenture)
Only 5% of companies’ folders are properly protected, on average. (Varonis)
Data breaches exposed 4.1 billion records in the first half of 2019. (RiskBased)


### Methodology: Visualization the password pattern
The data was gathered from (https://www.kaggle.com/lako65/ssh-brute-force-ipuserpassword). The dataset was from an exposing SSH server, enabled the password authentication and exposed port 22 to the internet in a week to collect around 50,000 hackers using usernames and passwords. The dataset looks like this after converting it to a data frame and cleaning the passwords with excessive digits (more than 20 in particular): 



We use a 94-dimensional matrix to present a password. Each column represents a character from "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ~!@#$%^&*()_+-={}|:\"<>?[]\\;',./ " (0 if the corresponding char, not present and 1 if present)
We use PCA to find the 20 important PCA variables to determine those passwords’ patterns like the following: 

### Methodology: clustering and centering:
A brief overview of K-mean:  k-means clustering aims to partition n observations into k clusters in which each observation belongs to the cluster with the nearest mean, serving as a prototype of the cluster. This results in a partitioning of the data space into Voronoi cells. 
To decide how many clusters we want to use in a most efficient manner, we visualize the clustering from 2 clusters to 20 clusters as following:
We use K-mean to find our set 8 clusters, which is the approximated saddle point, and then find the closest actual password related to those 8 clusters’ centers, which may not be the actual highest frequency password.
We use the Hamming distance to calculate the new input password to those 8 clusters’ centering passwords. Then we can give a measurement of the distance between the inserted password to the closet center of the cluster. (We insert a new password then predict the frequency of the times this inserted password will appear in the data set we gathered, then we will measure the outcome in terms of strong, which means the prediction outcome will be relatively small, medium, weak)

### Key result:


### Future Work:
