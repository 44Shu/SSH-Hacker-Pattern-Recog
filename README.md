# ssh-readme
### Abstract:
#### Use of the Following Methodology
* PCA
* K-means Clustering
* Hamming Distance
* Damerau–Levenshtein distance
* Machine Learning
 	
  This project determines the password’s security by comparing its patterns within the dataset using the K-means clustering process to sort out 8 clusters and finding out their corresponded central passwords(the medoids). We present our results in a visualized distance comparison to the 8 medoids through the use of Damerau–Levenshtein distance and Hamming Distance. 
 
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


### Methodology: Visualization of Password Patterns
The data was gathered from (https://www.kaggle.com/lako65/ssh-brute-force-ipuserpassword). The dataset was collected by exposing an open port secured SSH server to the internet and logging the attempted attacks’ usernames and passwords guesses for around a week. The dataset looks like this after converting it to a data frame and cleaning the passwords with excessive digits (more than 20 in particular): 

Inline-style: 
![alt text](https://github.com/44Shu/ssh-readme/blob/master/SSH%20DATASET%20PIC.png)


We used a 94-dimensional matrix to present a password. Each column represents a character from "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ~!@#$%^&*()_+-={}|:\"<>?[]\\;',./ " (0 if the corresponding char, not present and 1 if present)
We used Principal Component Analysis(PCA) to find the 20 most important PCA variables to determine those passwords’ patterns like the following: 

![alt text](https://github.com/44Shu/ssh-readme/blob/master/PCA%20chart.png)

### Methodology: Clustering and Finding Medoids:
* A brief overview of K-mean:  k-means clustering aims to partition n observations into k clusters in which each observation belongs to the cluster with the nearest mean, serving as a prototype of the cluster. This results in a partitioning of the data space into Voronoi cells. 
* To decide how many clusters we want to use in the most efficient manner, we visualize the clustering from 2 clusters to 20 clusters as following:

![alt text](https://github.com/44Shu/ssh-readme/blob/master/Kmean_clustering.png)

* We used K-mean to find our 8 clusters, which is the approximated saddle point, and then find the closest actual password related to those 8 clusters’ centers.
We used the Damerau–Levenshtein distance and a slightly modified Hamming distance to calculate the new input password to those 8 clusters’ centering passwords. The Hamming distance we choose to implement considers the extra characters between two strings as differing. We can calculate the distance between an inserted password to the medoids of the cluster. We insert a new password then predict the frequency this inserted password will appear in the data set we gathered using a machine learning model we trained, then we measure the outcome in terms of the passwords' strength, which mean that the prediction outcome will be along the lines of strong, medium, or weak.

### Key Result:
Successfully determine the strengh for an inserted password.(Planned)
### Future Work:
Building a machine learning model to predict an inputted password's frequency based on our data of passwords' distances.
