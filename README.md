Upload the picture here. 

# NLP Project: Sentiment analysis on Google Reviews

## Project Review

Often, when contemplating trying out a new restaurant or purchasing a new product, we turn to reviews to gauge the opinions of others on websites and Google. However, upon careful examination, we may discover that these opinions don't always align with the star ratings assigned to the respective site or item.

This realization sparked our interest in embarking on a project aimed at correlating the number of stars with sentiment analysis of the reviews. We chose to focus on Lambton College initially, but the methodology can be applied to any site or item featured in Google reviews.

## Chapters

**Problem Definition:** Not always a correlation between the reviews and the number of stars in Google reviews exists. 
<strong> Data Gathering: </strong> Webscrapping Google reviews.
<br> Data Preparation: ____
EDA (Exploratory Data Analysis): By graphing our data, we can find patterns, correlations, and unfair data. 
In the first stage, we did some plotting using Pyplot and Seaborn which allowed us to visualize our data and libraIn this step, I used heatmaps and correlation matrices to analyze the data.
Data Modelling: In this project, we used Selenium for Webscapping and VADER and TextBlob for the Sentiment analysis. Furthermore, we used Pandas for dataset management and Seaborn and Pyplot for plotting our data. 
Validate Model: Revise this....

## Chapter 1: Problem definition

The prevalent issue in online reviews, particularly on platforms like Google, is the inconsistency between assigned star ratings and the sentiments conveyed in user reviews. When deciding on a new restaurant or product, users often find discrepancies between numerical ratings and the actual experiences described. This misalignment poses a significant challenge: the need for a more accurate correlation between quantitative ratings and qualitative sentiments. Our project, initially centered on Lambton College, aims to address this gap by developing a methodology applicable to any site or item on Google reviews. Our goal is to create a more reliable connection between star ratings and user sentiments, ultimately enhancing the reliability and usefulness of online reviews in decision-making processes.

## Chapter 2: Data Gathering

The Data Gathering process was done through Webscrapping on Lambton College's Google reviews. The data collected was later copied into a CSV file,  resulting in three columns and one-hundred twenty-eight rows. The column names are listed below:

Name: Name of the person who writes the review. 
Comment: Review
Rating: Number of stars given. 

## Chapter 3: Data Preparation

With the initial phase of data gathering centered on Lambton College's Google reviews, the subsequent step involved meticulous data preparation. The information extracted through web scraping was organized into a structured format within a CSV file. The dataset comprises three key columns: "Name," representing the reviewer's identity; "Comment," encapsulating the textual content of the reviews; and "Rating," indicating the numerical value of stars awarded by the respective users. This systematic arrangement ensures a coherent and standardized dataset, laying the groundwork for subsequent analyses and the development of our correlation methodology. The emphasis on meticulous data preparation is vital to guaranteeing the accuracy and reliability of insights drawn from the collected information, enabling us to effectively address the identified challenge in online reviews.

## Chapter 4: EDA (Exploratory Data Analysis)

Exploring our dataset through visual representation is a crucial step in uncovering patterns, correlations, and potential anomalies. In the initial phase of our analysis, we employed Pyplot and Seaborn to create insightful plots that allowed us to visually grasp the nuances of our data. By utilizing heatmaps and correlation matrices, we delved deeper into the relationships between different variables. These visual tools provided a comprehensive view, enabling us to identify patterns in the data and assess correlations among various attributes. Additionally, this approach facilitated the detection of any inconsistencies or biases in the dataset. Through this thorough exploration, we aim to gain a robust understanding of our data, laying the foundation for informed decision-making and the development of our correlation methodology.

## Chapter 5: Data Modelling

Within this project, our data modeling process involved leveraging specific tools to extract, analyze, and manage our dataset. Selenium played a key role in web scraping, allowing us to efficiently gather data from online sources. For sentiment analysis, we employed VADER and TextBlob, enabling us to delve into the emotional nuances expressed in the textual content of the reviews. In terms of dataset management, Pandas proved to be a robust tool, facilitating seamless organization and manipulation of our collected data. To visualize our findings, we utilized Seaborn and Pyplot, harnessing their capabilities to create informative plots that aid in the interpretation of patterns and correlations within the dataset. This holistic approach to data modeling ensures a comprehensive understanding of the information at hand and supports the subsequent stages of our project.

## Chapter 6: Conclusions

