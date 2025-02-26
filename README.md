I) Discovery part 

We chose to make a sentiment analysis using two videos on Youtube discussing Elon Musk, given the current controversies surrounding him.
Elon Musk, the CEO of Tesla, SpaceX, and owner of X (formerly Twitter), is one of the most polarizing figures in modern business and technology. 
His management style, public statements on social media, acquisition and handling of Twitter, and often divisive political and social commentary are widely debated. 
His influence extends far beyond his companies, and more recently, Musk has become increasingly vocal about his political views, often aligning himself with conservative figures and ideologies. 
This includes his relationship with former President Donald Trump, his strained relationship with his transgender daughter, and the controversy surrounding accusations of him making a gesture resembling a Nazi salute during an interview.
Despite these controversies, Musk remains widely admired by many for his groundbreaking innovations and visionary projects. 
Given this polarizing nature, we chose two videos with highly polarized comment sections to conduct a sentiment analysis. 
This approach allows us to explore the diverse and often conflicting opinions about Musk, providing a deeper understanding of how the public perceives him. 
 We selected those 2 videos: 
Elon Musk: War, AI, Aliens, Politics… – a podcast discussing various topics related to Musk.
Jon Stewart on the Trump Inauguration – a segment that touches upon Musk in the context of political and economic discussions.
After exploring the polarized controversies on Elon Musk, we now turn our focus to YouTube. YouTube is  playing a central role in shaping public opinion: there are over 2.5 billion monthly active users and over 1 billion hours of content watched daily. 
The platform has become a dominant force in news, entertainment, and social discourse. The comment section is a key element which serves as a space for users to engage with content, express opinions, and interact with creators and other viewers. 
This comment section can provide valuable feedback, amplify misinformation,... It can reinforce biases, and influence public perception on a wide range of topics. 
That is why we’ll analyse the comments sections of the both videos to understand the public perception on Elon Musk.

To what extent does sentiment analysis of highly polarized comment sections capture the public's perception of Elon Musk? 
How do YouTube comment sections reflect the polarized public opinion surrounding Elon Musk?


SWOT for Youtube
Strengths

Global Audience
Strong Brand Recognition
Effective Recommendation Algorithm
Weaknesses

Content Moderation Challenges
Reliance on Advertising Revenue
Lack of Algorithm Transparency
Opportunities

Product Innovation
Partnerships
Threats

Increased Competition: tiktok, twitch…
Stricter Regulations



SWOT for Elon Musk
Strengths

Leadership
Proven Track Record
Risk-Taking Attitude
Weaknesses

Controversial Public Persona
Polarizing Figure
His management
Opportunities

Expansion into New Markets
Technological Advancement
Threats

Regulatory and Legal fields
Competition
Negative public sentiment


Sources:
https://en.wikipedia.org/wiki/Elon_Musk
https://www.lemonde.fr/pixels/article/2025/01/22/elon-musk-accuse-d-avoir-fait-un-salut-nazi-ou-comment-la-culture-4chan-entre-a-la-maison-blanche_6509600_4408996.html
https://fr.wikipedia.org/wiki/YouTube
https://theweek.com/elon-musk/1022182/elon-musks-most-controversial-moments
https://dalquestnews.org/22614/commentary/opinion-why-is-elon-musk-so-polarizing/


II) - Data preparation

First, to select the videos, we went on YouTube to identify potential videos for our sentiment analysis. We chose two videos that each had many views and over 23,000 comments. Next, we examined the comment sections to gauge the general public opinion: in the first video, we noticed a predominance of negative comments, which were also the most liked. Therefore, for our second video, we opted for one with relatively positive comments.

After selecting our videos, we used the Octoparse software to extract the data that interested us. Octoparse permitted us to use the web scraping techniques easier. By entering each video's link, Octoparse was able to analyze the corresponding data, but we only kept the elements likely to interest us ( the comment itself, the number of likes, the publication date, and the author's username.)

After selecting only the data that interested us, we exported the data table as an Excel file.

We chose to work on Google Collab and to code in R to clean our dataset and analyse it.


III) - Model Planning & Model building

Step 1 :  Presentation of our dataset
The dataset of our project is composed of 1453 youtube comments in total (676 from the podcast and 777 from the tv-Show). You can see attributes’ explanation below :

Attribute
Explanation
comment
Comments from youtube users
user
Autor of the comment
posted_since
Time since the user posted a comment
number_of_likes
Number of likes received by each comment
number_of-response
Number of responses received by each comment


There are 1574 NA in total (any attribute included).  NAs from the “comments” column are empty comments. There are two of them. The others are NA’s values from “number_of_likes” and “number_of_response” columns. We have compared them with actual comments in youtube videos, and we interpret that they are all  comments without any follow-up comment or without any like.
Additionally, it is to note that the comments come from multiple languages, but are mostly english.
 

Step 2 : Cleaning
We chose to vertically join the comments of the two videos. Therefore we added a “source” column to prevent loss of information.
We changed the NAs in the number of likes and responses columns to zeros.
The comment section is the most important one for our analysis, so we focused our cleaning on it. First, we changed NAs to empty values and we removed rows containing non-Latin characters. Then, we turned the comment section into a corpus and added some other cleaning steps.





First model : Clustering, key steps
 First, we turn words into tokens, so that they are considered as separate entities.

 



We then created a document-term matrix, which gives the words of the comments and how often they occur in each comment.



We turned the matrix into a dataframe that displays the words and their frequency in comments.
For example, “people” appears in 131 comments.



Finally, we computed the distance matrix after some additional cleaning.




Here is the result of our clustering model, displayed as a graph.


2 clusters


Sparse = 97% 









Second model : Sentiment Analysis

To begin our sentiment analysis, we decided to install the package syuzhet which will permit to transform textual data into quantitative sentiment measures.



After calculating the average sentiment score and the standard deviation of sentiment scores, we applied the NRC analysis, which is used to identify and quantify the various emotions expressed in the text. 


Then, using the results of the NRC analysis, we decided to create two sentiment categories (positive and negative) and assign each identified emotion accordingly. 
For instance, in the positive emotions category, we included: joy, anticipation, trust, surprise, and positive, and in the negative emotions category, we included: anger, disgust, fear, sadness and negative.

 Next, we calculated how many times each emotion appeared in the videos by summing their occurrences. 

Finally, to illustrate our results, we created a barplot where the negative emotions were displayed in red and the positive ones in green.

These are the results:





IV) - Communicate results

Results on Elon Musk case
Word proximity is difficult to capture in these two videos. The words are barely connected according to our clustering model, and the vocabulary is not diversified. For example, here are two outputs of our model (we removed more words to build the second one) :

We can see that the words have an homogeneous euclidean distance (lack of distinct “groups of words”), in other words the users use a similar vocabulary regardless of their opinion on Elon Musk. Maybe this is due to users writing their comments quickly, which is explained by the format of the Youtube platform.


We can then study the frequency of words in the comments. As you can see from the word cloud, the most frequent words are related to users' feelings (like, love, great, etc.) and forms of hyperbole (never, always, best, way, etc…). So the opinions about Elon Musk are amplified on youtube, and the comments describe the emotions or feelings of the users. This is a good sign for a sentiment analysis.


Our sentiment analysis highlights that comments on these videos are mostly positive (almost two times more positive than negative). Additionally, the emotions that are most expressed are trust, joy, anticipation and fear. We can interpret that when it comes to Elon Musk, the polarisation of the community is around people's doubts. Some believe in him, while others express their fear.
General applicability

Finally, clustering doesn’t seem adapted to analysing Youtube comments, as people mainly use generic words. 
However, sentiment analysis is an encouraging lead, as comments are mainly used to express feelings. Additionally, they are often exaggerated which may help the model to capture the feelings of the community.
Besides, emotion analysis can be helpful in understanding the polarisation of the community. In our example, a businessman known for the numeric and innovative sectors is disruptive because some people trust him while others are afraid. The result would certainly be different if we studied other celebrities.

As a side note, we can consider Deep Learning techniques to improve our current sentiment analysis model. In fact, these techniques are able to memorise the words of a sentence, and thus they can differentiate contexts and avoid bias. For example, our model is not able to take into account negative sentences, but the frequency of the word "don't" is worrying (example: "don't like" should be labelled as negative). Also, it is possible that some opinions are not related to Elon Musk, but to the hosts of the video (here Lex Fridman and Jimmy Limmel) or to the videos themselves.
On the other hand, this increase in power may create a black box effect, and this alternative model would be more difficult to interpret and explain than our current one.
