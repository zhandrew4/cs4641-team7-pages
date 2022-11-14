---
layout: default
---

# Contributors:
<span style = "font-size:25px">
**_Andrew Zhang, Bickston Laenger, Blake Watson, Gillian Kearney, Nathan Miao_**
</span>

# Table of Contents

*  [**_Proposal_**](#proposal_header)
    *  [_Introduction/Background_](#intro_header)
    *  [_Problem Definition_](#problem_header)
    *  [_Methods_](#methods_header)
    *  [_Potential Results_](#results_header)
    *  [_Gantt Chart_](#gantt_header)
    *  [_Contribution Table_](#contributions_header)
    *  [_Proposal Video_](#prop_video_header)
    *  [_References_](#references_header)
   
*  [**_Midterm Report_**](#midterm_header)
    *  [_Introduction/Background_](#intro_midterm)
    *  [_Problem Definition_](#problem_midterm)
    *  [_Data Collection_](#data_midterm)
    *  [_Methods_](#methods_midterm)
    *  [_Results and Discussion_](#results_midterm)
    *  [_Contribution Table_](#contributions_midterm)
    *  [_References_](#references_midterm)

<h1 id = "proposal_header"> Proposal </h1>

<h2 id = "intro_header"> Introduction/Background </h2>

With the rise of digital music, large amounts of music have been made easily available and streaming platforms have made music discovery and sharing much more prevalent. With a large amount of music available, there arises a need for methods to sort through music. While songs can be easily categorized by album, artist, and genre, emotions are highly involved in the perception and enjoyment of music. Many people listen to songs that correspond to specific moods/feelings that they experience. Predicting the mood/sentiment of a song allows music to be sorted by its associated emotions, enabling users to easily discover and find songs and generate playlists suited to their different situations and moods. 

Existing work has been done on classifying songs based on lyrical content and genre, however, the emotions conveyed by a song remain an important aspect of how music is consumed. Previous works on classifying music moods have also used multilabel classification and convolutional neural networks to identify the mood of various songs. 

<h2 id = "problem_header"> Problem Definition </h2>

Given the various audio features and characteristics of a song, we aim to predict the overall mood of the song. Additionally, we wish to group songs of similar moods together to see how different combinations of audio/musical features result in different conveyed emotions. This would allow people to easily find music that suits their current situation/feelings, resulting in better overall enjoyment.

<h2 id = "methods_header"> Methods </h2>

We wish to apply neural networks and classification algorithms such as random forests or naive Bayes classifiers to classify music using more specific sentiment keywords, rather than more general mood categories. Additionally, we potentially want to use clustering algorithms such as K-Means, GMM, and/or DBScan to group songs by mood and see how different musical/audio features correspond to different sentiment keywords, and if sentiment keywords/tags are indeed consistent with audio features.

Our dataset sourced from Kaggle contains a song’s title and artist, in addition to sentiment labels derived from social tags on Last.fm. Each song is also associated with a unique Spotify ID, from which we can obtain more detailed musical features from Spotify’s API. 

<h2 id = "results_header"> Potential Results </h2>

We hope to predict the emotions/mood of a song based on its musical/audio features. Additionally, we hope to discover how different musical features contribute to the overall mood of a song. If successful, such a model can be used to create more effective music recommendation tools or playlist creation tools that can provide users with songs suited to their current moods.

<h2 id = "gantt_header"> Group Gantt Chart </h2>

![Gantt Chart](/Gantt Chart.png)

[Link to Full Gantt Chart](https://docs.google.com/spreadsheets/d/1LuajRhGWIpd4FIZey0VL58gxuJHQipyN/edit?usp=sharing&ouid=104478584403003139152&rtpof=true&sd=true)

<h2 id = "contributions_header"> Contributions </h2>

| Name             | Project Proposal                                                                | Midterm Report     | Final Presentation |
| :--------------: | :-----------------------------------------------------------------------------: | :----------------: | :----------------: |
| Andrew Zhang     | Data Sourcing <br> Project Research <br> Proposal Write-Up <br> Video Recording | TBD                | TBD                |
| Bickston Laenger | Proposal Write-Up <br> Note: Out Sick                                           | TBD                | TBD                |
| Blake Watson     | Project Webpage Creation <br> Video Recording                                   | TBD                | TBD                |
| Gillian Kearney  | Gantt Chart <br> Contribution Management                                        | TBD                | TBD                |
| Nathan Miao      | Project Webpage Creation <br> Video Recording                                   | TBD                | TBD                |

<h2 id = "prop_video_header"> Proposal Video </h2>

[Link to Youtube Video](https://www.youtube.com/watch?v=H-87kh8yuE4)

<h2 id = "references_header"> References </h2>

Bischoff, K., Firan, C. S., Paiu, R., Nejdl, W., Laurier, C., & Sordo, M. (2009) Music Mood and Theme Classification - A Hybrid Approach. Proceedings of the 10th International Society for Music Information Retrieval Conference, ISMR 2009, 657-662. https://www.researchgate.net/publication/220723819_Music_Mood_and_Theme_Classification_-_a_Hybrid_Approach

Laurier, C., Grivolla, J., & Herrera, P. (2018). Multimodal Music Mood Classification Using Audio and Lyrics. Seventh International Conference on Machine Learning and Applications, 2018, 688-693. https://doi.org/10.1109/ICMLA.2008.96

Pyrovolakis, K., Tzouveli P. ,& Stamou, G. (2022). Multi-Modal Song Mood Detection with Deep Learning. Sensors, 22(3), 1065. https://doi.org/10.3390/s22031065

Veas, C. (2020, August 15). Predicting the Music Mood of a Song with Deep Learning. Towards Data science. https://towardsdatascience.com/predicting-the-music-mood-of-a-song-with-deep-learning-c3ac2b45229e


<h1 id = "midterm_header"> Midterm Report </h1>

<h2 id = "intro_midterm"> Introduction/Background </h2>

With the rise of digital music, large amounts of music have been made easily available and streaming platforms have made music discovery and sharing much more prevalent. With more and more music becoming accessible, there arises a need for methods to sort through music. While songs can be easily categorized by album, artist, and genre, emotions are highly involved in the perception and enjoyment of music. Many people listen to songs that correspond to specific moods/feelings that they experience. Predicting the mood/sentiment of a song allows music to be sorted by its associated emotions, enabling users to easily discover and find songs and generate playlists suited to their different situations and moods. 

Existing work has been done on classifying songs based on lyrical content and genre, however, the emotions conveyed by a song remain an important aspect of how music is consumed. Previous works on classifying music moods have also used multilabel classification and convolutional neural networks to identify the mood of various songs. 

<h2 id = "problem_midterm"> Problem Definition </h2>

Given the various audio features and characteristics of a song, we aim to predict the overall mood of the song. Additionally, we wish to group songs of similar moods together to see how different combinations of audio/musical features result in different conveyed emotions. This would allow people to easily find music that suits their current situation/feelings, resulting in better overall enjoyment.

<h2 id = "data_midterm"> Data Collection </h2>

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

The original Kaggle dataset also contains some songs without Spotify IDs, which are presumed to not be available on Spotify. Additionally, some of the provided Spotify IDs were invalid. These entries were removed from the dataset, as their audio features could not be obtained. Additionally, the dataset also contained duplicate songs with multiple sentiment labels. These entries were consolidated and the duplicates were removed to clean the dataset. Overall, the final working dataset contained 48,391 songs.

<h2 id = "methods_midterm"> Methods </h2>

The data and its features will be analyzed using the unsupervised Principal Component Analysis (PCA) to determine which of the original audio features are most relevant. PCA will also be used to potentially perform dimensionality reduction and remove any irrelevant features. 

The dataset also has too many labels. Out of 265 total different sentiment labels, the top 30 most common labels are shown below, with the number of occurrences and the percentage of total songs that have that label (Fig. 1). The top label “sleazy” contains a measly 725 songs, accounting for only a little under 1.5% of the total dataset of 48,391 songs. 

![Top 30 Labels](/Top 30 Labels.png)

Many of the labels, however, are very similar to each other, such as “cheerful”, “uplifting”, and “happy”. Such labels can potentially be consolidated into more general labels that each contain more data points which can then be learned. We plan to first use unsupervised clustering methods such as K-Means (and/or DBScan) to group similar songs together and consolidate labels to later use in supervised classification models such as naive Bayes and random forests.

<h2 id = "results_midterm"> Results and Discussions </h2>

<h3><ins> PCA </ins></h3>

PCA was first performed with no dimensionality reduction to analyze the features and all of the principal components (12 components). The figure below shows the percentage of the variance in the data explained by each principal component. 

![Figure 2](/Figure 2.png)

The first principal component explains about 25% of the overall variance, while the last principal component only explains about 1%. Adding up the percentages, we can see that using the first 7 principal components retains about 79% (~80%) of the total variance.

Furthermore, looking at the components themselves, we can determine which of the original features are most influential in forming the characteristics of a song. Listed below are the original audio features alongside the absolute values of the first four principal components in each row to better convey magnitudes. 

![Figure 3](/Figure 3.png)

From this, we can see that the first principal component incorporates mainly energy, loudness, and acousticness, the second component mainly involves danceability and valence, the third component deals with the key and mode (major/minor), and the fourth component focuses on whether or not a track is a live recording with an audience (cheering and talking in the background). Overall, it seems that the energy, loudness, and acousticness of a song are most impactful in determining its characteristics, followed closely by danceability and valence. 


<h3><ins> K-Means </ins></h3>

Using the 7 features derived from PCA, we first run K-Means as an unsupervised clustering method to group songs together and consolidate the many labels within our original dataset. To determine the optimal number of clusters, we created 9 different K-Means models ranging from 2 to 10 clusters and evaluated each one using both the elbow method and silhouette coefficients. 

The inertia value used in the elbow method is simply the sum of the squared distances from each point to its cluster center. From the graph below (Fig. 4), we can see that while the “elbow” is not very well defined, it seems to occur at around 4 or 5 clusters. 

![Figure 4](/Figure 4.png)

For the silhouette coefficients, we first note that all silhouette coefficients are quite low across the board. However, according to the graph below (Fig. 5), the model with 4 clusters has the maximum silhouette coefficient. 

![Figure 5](/Figure 5.png)

Even with some feature reduction using PCA, the dataset is still 7-dimensional, and thus cannot be easily visualized. However, we can plot 2-dimensional “slices” to observe the clusters with respect to 2 features at a time. 

![Figure 6](/Figure 6.png)

![Figure 7](/Figure 7.png)

![Figure 8](/Figure 8.png)

We can see that while K-Means successfully forms 4 clusters, they are not very distinct from each other and have a lot of overlap. This is also reflected in the low silhouette coefficient of about 0.150, indicating that the clusters are very close to one another without much significant separation. 

This poor performance of K-Means can be attributed to 2 possible factors. First, as mentioned before, the data is in 7-dimensions with 7 features. K-Means and euclidian distances are known to perform poorly in higher dimensions, and the model could be suffering from the curse of dimensionality. Second, from the plots above, we can see that the data do not form clear, circular clusters that work well with K-Means. Moving forwards, it would be best to try other clustering models such as DBScan and/or GMM that can better handle different cluster shapes. 

Despite the poor clustering, however, it seems that K-Means did successfully consolidate some of the original labels. With the clusters assigned by K-Means, we can see which of the original labels are contained in each cluster. Below are the 4 most common labels in each cluster, each listed with their number of occurrences (Fig. 9), and it seems each cluster does have an overall theme. The top labels within each cluster generally match each other to a certain extent.

![Figure 9](/Figure 9.png)

<h2 id = "contributions_midterm"> Contributions </h2>

| Team Member      | Project Proposal                                                                | Midterm Report     | Final Presentation |
| :--------------: | :-----------------------------------------------------------------------------: | :----------------: | :----------------: |
| Andrew Zhang     | Data Sourcing <br> Project Research <br> Proposal Write-Up <br> Video Recording | Data Collection <br> Data Cleaning <br> Feature Reduction/Analysis (PCA) <br> Report Write-Up | TBD |
| Bickston Laenger | Proposal Write-Up <br> Note: Out Sick                                           | Data Visualization <br> Data Analysis | TBD                |
| Blake Watson     | Project Webpage Creation <br> Video Recording                                   | Website Updates | TBD                |
| Gillian Kearney  | Gantt Chart <br> Contribution Management                                        | Train and Validate First Model (KMeans) | TBD                |
| Nathan Miao      | Project Webpage Creation <br> Video Recording                                   | Data Cleaning <br> Website Updates | TBD                |


References

Bischoff, K., Firan, C. S., Paiu, R., Nejdl, W., Laurier, C., & Sordo, M. (2009) Music Mood and Theme Classification - A Hybrid Approach. Proceedings of the 10th International Society for Music Information Retrieval Conference, ISMR 2009, 657-662. https://www.researchgate.net/publication/220723819_Music_Mood_and_Theme_Classification_-_a_Hybrid_Approach

Laurier, C., Grivolla, J., & Herrera, P. (2018). Multimodal Music Mood Classification Using Audio and Lyrics. Seventh International Conference on Machine Learning and Applications, 2018, 688-693. https://doi.org/10.1109/ICMLA.2008.96

Pyrovolakis, K., Tzouveli P. ,& Stamou, G. (2022). Multi-Modal Song Mood Detection with Deep Learning. Sensors, 22(3), 1065. https://doi.org/10.3390/s22031065

Veas, C. (2020, August 15). Predicting the Music Mood of a Song with Deep Learning. Towards Data science. https://towardsdatascience.com/predicting-the-music-mood-of-a-song-with-deep-learning-c3ac2b45229e