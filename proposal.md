---
layout: default
---

# Welcome to our Project Proposal

[Back To Main Site](./)

# Table of Contents

*  [_Introduction/Background_](#intro_header)
*  [_Problem Definition_](#problem_header)
*  [_Methods_](#methods_header)
*  [_Potential Results_](#results_header)
*  [_Gantt Chart_](#gantt_header)
*  [_Contribution Table_](#contributions_header)
*  [_Proposal Video_](#prop_video_header)
*  [_References_](#references_header)

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