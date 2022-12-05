---
layout: default
---

# Welcome to our Final Report (YAY!)

[Back To Main Site](./)

# Table of Contents

*  [_Introduction/Background_](#intro_final)
*  [_Problem Definition_](#problem_final)
*  [_Data Collection_](#data_final)
*  [_Methods_](#methods_final)
*  [_Results and Discussion_](#results_final)
*  [_Conclusion_](#conclusion_final)
*  [_Contribution Table_](#contributions_final)
*  [_References_](#references_final)

<h2 id = "intro_final"> Introduction/Background </h2>

With the rise of digital music, large amounts of music have been made easily available and streaming platforms have made music discovery and sharing much more prevalent. With more and more music becoming accessible, there arises a need for methods to sort through music. While songs can be easily categorized by album, artist, and genre, emotions are highly involved in the perception and enjoyment of music. Many people listen to songs that correspond to specific moods/feelings that they experience. Predicting the mood/sentiment of a song allows music to be sorted by its associated emotions, enabling users to easily discover and find songs and generate playlists suited to their different situations and moods. 

Existing work has been done on classifying songs based on lyrical content and genre, however, the emotions conveyed by a song remain an important aspect of how music is consumed. Previous works on classifying music moods have also used multilabel classification and convolutional neural networks to identify the mood of various songs. 

<h2 id = "problem_final"> Problem Definition </h2>

Given the various audio features and characteristics of a song, we aim to predict the overall mood of the song. Additionally, we wish to group songs of similar moods together to see how different combinations of audio/musical features result in different conveyed emotions. This would allow people to easily find music that suits their current situation/feelings, resulting in better overall enjoyment. 

<h2 id = "data_final"> Data Collection </h2>

Our dataset is sourced from Kaggle and contains a song’s title and artist, in addition to sentiment labels derived from social tags on Last.fm. Each song is also associated with a unique Spotify ID, from which we can obtain more detailed musical features from Spotify’s API. 

Spotify’s API provides 12 musical features described below: danceability, energy, key, loudness, mode, speechiness, acousticness, instrumentalness, liveness, valence, tempo, and time signature

* Danceability describes how suitable a track is for dancing, based on characteristics such as tempo, rhythm stability, and beat strength. Danceability ranges from 0 to 1, where a value of 0 is the least danceable and 1 is the most danceable.
* Energy describes the perceived intensity of a song, ranging from 0 to 1, where 0 indicates low energy and 1 indicates high energy. 
* Key represents the music key of the song, ranging from 0 to 11 to include all possible pitch classes from A to G. 
* Loudness indicates the average loudness of a track in decibels (dB), typically running from -60 to 0 dB. 
* Mode indicates whether a song is in a major or minor musical mode, with 1 indicating major and 0 indicating minor.
* Speechiness describes the prevalence of spoken words (rather than sung words) throughout the track. Speechiness ranges from 0 to 1, with values below 0.33 mostly representing musical songs and values above 0.66 mostly representing non-musical tracks such as talk shows/podcasts.
* Acousticness is a confidence measure of whether or not a track is acoustic, ranging from 0 to 1. A value of 1 indicates that the song is highly likely to be acoustic, while a value of 0 indicates that the song likely contains a lot of audio processing.
* Instrumentalness measures the amount of vocal presence in the song, ranging from 0 to 1. A higher value close to 1 indicates a lack of vocal content, containing mostly instruments/noise only. 
* Liveness measures how likely a song contains an audience in the recording, ranging from 0 to 1. A value above 0.8 indicates that the song is very likely a live recording performed in front of an audience. 
* Valence describes the overall “positivity” of a track, ranging from 0 to 1. A high valence indicates that the song sounds happy and uplifting, while a low valence indicates a more sad and angry sound. 
* Tempo is measured in beats per minute (BPM) and describes the overall speed and pace of the song.
* Time Signature ranges from 3 to 7, representing time signatures from 3/4 to 7/4. 

The original Kaggle dataset also contains some songs without Spotify IDs, which are presumed to not be available on Spotify. Additionally, some of the provided Spotify IDs were invalid. These entries were removed from the dataset, as their audio features could not be obtained. Additionally, the dataset also contained duplicate songs with multiple sentiment labels. These entries were consolidated and the duplicates were removed to clean the dataset. Overall, the final working dataset contains 48,391 songs.

<h2 id = "methods_final"> Methods </h2>

The data and its features will be first analyzed using the unsupervised Principal Component Analysis (PCA) to determine which of the original audio features are most relevant. PCA will also be used to perform dimensionality reduction and remove any irrelevant features. 

One glaring issue with the dataset is that it contains too many different labels. Out of 265 total different sentiment labels, the top 30 most common labels are shown below, with the number of occurrences and the percentage of total songs of each label (Fig. 1). The top label “sleazy” contains a measly 725 songs, accounting for only a little under 1.5% of the total dataset of 48,391 songs. These labels are not well-suited for learning.

![Figure 1](/Final Figure 1.png)

Upon closer observation, however, many of the labels are very similar to each other, such as “cheerful”, “uplifting”, and “happy”. Such labels can potentially be consolidated into more general labels that each contain more data points which can then be learned. We plan to first use unsupervised clustering methods such as K-Means and DBScan to group similar songs together and consolidate the labels into more learnable categories. We then aim to use supervised classification models including Logistic Regression, Naive Bayes, and Random Forests to learn the newly consolidated labels and predict which mood category a song belongs in. 

<h2 id = "results_final"> Results and Discussions </h2>

<h3><ins> PCA </ins></h3>

PCA was first performed with no dimensionality reduction to analyze the features and all of the principal components (12 components). The figure below shows the percentage of the variance in the data explained by each principal component. 

![Figure 2](/Final Figure 2.png)

The first principal component explains about 25% of the overall variance, while the last principal component only explains about 1%. Adding up the percentages, we can see that using the first 7 principal components retains about 79% (~80%) of the total variance. Moreover, the first 3 principal components together retain about 47% (~50%) of the total variance while being much easier to visualize.

Furthermore, looking at the components themselves, we can determine which of the original features are most influential in forming the characteristics of a song. Listed below are the original audio features alongside the absolute values of the first four principal components in each row to better convey magnitudes. 

![Figure 3](/Final Figure 3.png)

From this, we can see that the first principal component incorporates mainly energy, loudness, and acousticness, the second component mainly involves danceability and valence, the third component deals with the key and mode (major/minor), and the fourth component focuses on whether or not a track is a live recording with an audience (cheering and talking in the background). Overall, it seems that the energy, loudness, and acousticness of a song are most impactful in determining its characteristics, followed closely by danceability and valence. 

<h3><ins> Unsupervised Learning </ins></h3>

Both K-Means and DBScan were used with both 3 PCA features and 7 PCA features in order to cluster the data points and consolidate sentiment labels. The model with the best results is then used to create new consolidated ground truth labels to be later used in the supervised learning models.

<h3><ins> K-Means </ins></h3>

First, using the 7 features derived from PCA, we run K-Means as an unsupervised clustering method to group songs together and consolidate the many labels within our original dataset. To determine the optimal number of clusters, we created 9 different K-Means models ranging from 2 to 10 clusters and evaluated each one using both the elbow method and silhouette coefficients. 

![Figure 4](/Final Figure 4.png)

![Figure 5](/Final Figure 5.png)

The inertia value used in the elbow method is simply the sum of the squared distances from each point to its cluster center. From the graph above (Fig. 4), we can see that while the “elbow” is not very well defined, it seems to occur at around 4 or 5 clusters. 
For the silhouette coefficients, all values are quite low across the board, however, according to the graph above (Fig. 5), the model with 4 clusters has the maximum silhouette coefficient. 

Since there are 7 features, the data is 7-dimensional and cannot be easily visualized. However, we can plot 2-dimensional “slices” to observe the 4 clusters with respect to two features at a time.

![Figure 6](/Final Figure 6.png)

![Figure 7](/Final Figure 7.png)

![Figure 8](/Final Figure 8.png)

We can see that while K-Means successfully forms 4 clusters, they are not very distinct from each other and have a lot of overlap. This is also reflected in the low silhouette coefficient of about 0.150, indicating that the clusters are very close to one another without much significant separation. 

This poor performance of K-Means can be attributed to 2 possible factors. First, as mentioned before, the data is in 7-dimensions with 7 features. K-Means and euclidian distances are known to perform poorly in higher dimensions, and the model could be suffering from the curse of dimensionality. Second, from the plots above, we can see that the data do not form clear, circular clusters that work well with K-Means.

Despite the poor clustering, however, it seems that K-Means did successfully consolidate some of the original labels. With the clusters assigned by K-Means, we can see which of the original labels are contained in each cluster. Below are the 4 most common labels in each cluster, each listed with their number of occurrences (Fig. 9), and it seems each cluster does have an overall theme. The top labels within each cluster generally match each other to a certain extent.

![Figure 9](/Final Figure 9.png)

Since K-Means is known to perform poorly in higher dimensions, we also ran K-Means using the 3 main components given by PCA, rather than 7. This also allows the data and clusters to be visualized much more easily as well. Same as before, we created 9 different K-Means models ranging from 2 to 10 clusters and evaluated each one using both the elbow method and silhouette coefficients. 

![Figure 10](/Final Figure 10.png)

![Figure 11](/Final Figure 11.png)

While the “elbow” in the graph above (Fig. 10) seems to occur at around 2-3 clusters, the silhouette coefficient spikes significantly at 4 clusters (Fig. 11). Therefore, 4 clusters were used in the K-Means model to cluster and consolidate the labels. These clusters are shown below from 3 different angles. 

![Figure 12](/Final Figure 12.png)

![Figure 13](/Final Figure 13.png)

![Figure 14](/Final Figure 14.png)

In a lower dimension with fewer features, K-Means performs much better, separating the dataset into 4 distinct clusters. This clustering has a higher silhouette coefficient of about 0.271, which is an improvement over the 7-dimensional clusters, but still relatively low. Visually, this is because the clusters are large and relatively close to each other. This naturally results in higher intra-cluster distances, and lower inter-cluster distances, yielding a lower silhouette coefficient, despite the clear separation of the data points. 

Similar to the earlier case, despite the relatively low silhouette coefficient, it seems that the clustering successfully consolidates similar labels together. Shown below are the top labels contained within each cluster (Fig. 15). While there are some overlaps, such as “sexy” and “sleazy” occurring in multiple clusters, each cluster still has an overall theme. It could be the case that tags like “sleazy” are not musically distinctive, and end up split into sleazy songs that feel aggressive/angry and those that are more suggestive/sexy. 

![Figure 15](/Final Figure 15.png)

<h3><ins> DBScan </ins></h3>

First, DBScan was used to create clusters based on the 7 features given by PCA. DBScan uses 2 hyperparameters, MinPts (Min_Samples) and Eps. The value of MinPts is taken as twice the number of features. In this case, we took MinPts as 14. The value of Eps was determined using the elbow method, comparing the distances to the 14th nearest neighbor for each point. As shown in the graph below (Fig. 16), the “elbow” or “knee” occurs at a distance of 2.229, which we then use as the value of Eps.

![Figure 16](/Final Figure 16.png)

Running DBScan with MinPts of 14 and Eps of 2.229 results in 2 clusters along with outliers. Again, with 7 features, the clusters are 7-dimensional. Therefore we take 2-dimensional “slices” of the data with respect to 2 features at a time. The resulting clusters are displayed below (Fig. 17 - 19).

![Figure 17](/Final Figure 17.png)

![Figure 18](/Final Figure 18.png)

![Figure 19](/Final Figure 19.png)

DBScan is able to separate the data points into 2 clusters, however, one of the clusters is significantly larger than the other. The 2 clusters do seem to be much more separated and distinct than those given by K-Means, which is reflected in the relatively higher silhouette coefficient of 0.475. While the clusters given by DBScan have better metrics, they are very unbalanced, and therefore are less useful for the supervised learning models we plan to use. We can also examine the labels contained within each cluster as shown below (Fig. 20). While the smaller cluster seems to form a distinct category of labels with a soft and mysterious mood, the larger cluster lacks a specific theme that ties the labels together.

![Figure 20](/Final Figure 20.png)

We then try DBScan using 3 PCA features instead of 7. Here, we take MinPts as 5 and use the same elbow method to determine the optimal value for Eps by comparing the distance to the 5th nearest neighbor of each point. As shown in the graph below (Fig. 21), the “elbow” occurs at a distance of 0.375, which we then take as the value of Eps. 

![Figure 21](/Final Figure 21.png)

Running DBScan with MinPts of 5 and Eps of 0.375 results in 3 clusters with outliers. The resulting clusters are then displayed below (Fig. 22).

![Figure 22](/Final Figure 22.png)

Notably, the clusters given by DBScan with 3 features are even more skewed than the clusters using 7 features.  Cluster 1 is much larger, containing the majority of the data points while the remaining two clusters only each contain a small portion of points. However, the clusters have a silhouette coefficient of 0.398 and are relatively separated and distinct, even with unbalanced sizes. Despite the higher silhouette coefficient in comparison to its K-Means counterpart, the clusters fail to properly consolidate the initial labels, leaving almost all labels in the main cluster. Additionally, as shown below, there is no clear pattern/similarity between the labels contained in the clusters. 

![Figure 23](/Final Figure 23.png)

Overall, comparing DBScan to K-Means, the clusters given by DBScan have higher silhouette coefficients and are indeed more separated and distinct than those given by K-Means, as shown below (Fig. 24). However, despite the poor metrics, the clusters given by K-Means do a much better job of consolidating the original sentiment labels into similar categories. The categories given by K-Means seem much more learnable for the supervised models we plan to use. Since K-Means performed better with only 3 PCA features, we will use the clusters given by that K-Means as the ground-truth labels to be learned using supervised learning methods.

![Figure 24](/Final Figure 24.png)

This phenomenon could be due to the fact that our initial dataset does not form any distinct clusters, and all the data points instead seem to form one large cluster. This is especially apparent when the dataset is visualized using the 3 PCA features (Fig. 14 and 21). Therefore, a density-based algorithm like DBScan will end up fitting almost all of the data points into one cluster, since they are all relatively close to each other, leaving the remaining points as outliers or small clusters. On the other hand, with its predetermined number of centers, K-Means ends up simply partitioning the data set into 4 separate sections. As previously mentioned, the clusters given by K-Means are then relatively larger and closer together, resulting in a lower silhouette coefficient. However, K-Means is able to partition the data points evenly based on their similarity and successfully consolidates the original sentiment labels into 4 new categories.

<h3><ins> Supervised Learning </ins></h3>

Instead of the original 265 different sentiment labels in the dataset, we used K-Means on 3 PCA features to cluster labels into 4 more general mood categories. The labels from the K-Means clusters are then used as the ground truths to be learned by the supervised learning models. All three models were evaluated using accuracy, precision, and F-score for comparison.

<h3><ins> Logistic Regression </ins></h3>

Two Logistic Regression models were run, one using 3 PCA features/components and the other using 7 PCA features. Both used the labels given by the K-Means clustering as ground truths. The dataset was split into training and testing sets, with 80% of songs in the former, and 20% in the latter.

The accuracy, precision, and F-scores for both Logistic Regression models are shown below (Fig. 25). The confusion matrices for both models are also displayed below (Fig. 26). Notably, all three metrics are exceptionally high for both Logistic Regression models, with an accuracy of 99.8%. Additionally, there seems to be very little difference between the model using only 3 features and the model using 7 features. This is a likely indicator that only the 3 main PCA components are sufficient to capture the information needed to fully separate the different mood categories apart.

![Figure 25](/Final Figure 25.png)

![Figure 26](/Final Figure 26.png)

The high accuracy of Logistic Regression could be due to how the clusters are formed by K-Means. As shown below (Fig. 27), the clusters formed by K-Means separate the dataset into four distinct sections. Visually, the clusters are linearly separable, so clear decision boundaries can be learned by the Logistic Regression model.  

![Figure 27](/Final Figure 27.png)

<h3><ins> Random Forest </ins></h3>

Two Random Forest models were trained using both 3 PCA features and 7 PCA features. Once more, we separated the dataset using 80% for training and 20% for testing. For Random Forests, we tuned two hyperparameters to improve the model performance: n_estimators and max_depth. This was done using Randomized Search Cross Validation (courtesy of sklearn), where K-fold cross-validation is repeatedly performed with randomly sampled hyperparameter values. We used 5-fold cross-validation, with 10 iterations of randomized search, which resulted in the optimal values of 180 for n_estimators and 70 for max_depth. 

The accuracy, precision, and F-scores of both Random Forest models are shown below (Fig. 28), along with the confusion matrices (Fig. 29). Both models have very high metrics, performing extremely well with around 98% accuracy. It should be noted that the model using 7 features performed slightly worse, with a very small 0.01% decrease in accuracy. This could be attributed to how easily susceptible Random Forest classifiers are to overfitting, with the extra features introducing unnecessary noise. This could also simply be attributed to random chance, as a 0.01% decrease in accuracy is barely noticeable and could likely not be reproduced.

![Figure 28](/Final Figure 28.png)

![Figure 29](/Final Figure 29.png)

<h3><ins> Naive Bayes </ins></h3>

Using a similar process as before, two Naive Bayes models were trained, one using 3 PCA features and the other using 7 PCA features. Again, the dataset was split into a testing set and a training set with an 80/20 split respectively. Specifically, Gaussian Naive Bayes was used, with the assumption that all features are independent, and follow a Gaussian distribution. 

We then fit the data and predicted the labels using fit and predict methods respectively on the instance of the GaussianNB made from the data for both sets of components. 
While still above 90%, the accuracies are the lowest of the 3 approaches we used and are pictured below. Again, the accuracy_score, precision_score, and f1_score methods from sklearn were used.

![Figure 30](/Final Figure 30.png)

![Figure 31](/Final Figure 31.png)

<h2 id = "conclusion_final"> Conclusion </h2>

<h2 id = "contributions_final"> Contributions Table </h2>

| Team Member      | Project Proposal                                                                | Midterm Report     | Final Presentation |
| :--------------: | :-----------------------------------------------------------------------------: | :----------------: | :----------------: |
| Andrew Zhang     | Data Sourcing <br> Project Research <br> Proposal Write-Up <br> Video Recording | Data Collection <br> Data Cleaning <br> Feature Reduction/Analysis (PCA) <br> Report Write-Up | Report Write-Up <br> DBScan <br> Logistic Regression <br> Data Visualization |
| Bickston Laenger | Proposal Write-Up <br> Note: Out Sick                                           | Data Visualization <br> Data Analysis | Report Write-Up <br> Logistic Regression |
| Blake Watson     | Project Webpage Creation <br> Video Recording                                   | Website Updates | Random Trees <br> Project Webpage |
| Gillian Kearney  | Gantt Chart <br> Contribution Management                                        | Train and Validate First Model (KMeans) | Naive Bayes |
| Nathan Miao      | Project Webpage Creation <br> Video Recording                                   | Data Cleaning <br> Website Updates | Random Trees <br> Project Webpage |

<h2 id = "references_final"> References </h2>

Bischoff, K., Firan, C. S., Paiu, R., Nejdl, W., Laurier, C., & Sordo, M. (2009) Music Mood and Theme Classification - A Hybrid Approach. Proceedings of the 10th International Society for Music Information Retrieval Conference, ISMR 2009, 657-662. https://www.researchgate.net/publication/220723819_Music_Mood_and_Theme_Classification_-_a_Hybrid_Approach

Laurier, C., Grivolla, J., & Herrera, P. (2018). Multimodal Music Mood Classification Using Audio and Lyrics. Seventh International Conference on Machine Learning and Applications, 2018, 688-693. https://doi.org/10.1109/ICMLA.2008.96

Pyrovolakis, K., Tzouveli P. ,& Stamou, G. (2022). Multi-Modal Song Mood Detection with Deep Learning. Sensors, 22(3), 1065. https://doi.org/10.3390/s22031065

Veas, C. (2020, August 15). Predicting the Music Mood of a Song with Deep Learning. Towards Data science. https://towardsdatascience.com/predicting-the-music-mood-of-a-song-with-deep-learning-c3ac2b45229e