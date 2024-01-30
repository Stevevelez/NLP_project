Upload the picture here. 

# NLP Project: Sentiment analysis on Google Reviews

## Project Review

Often, when contemplating trying out a new restaurant or purchasing a new product, we turn to reviews to gauge the opinions of others on websites and Google. However, upon careful examination, we may discover that these opinions don't always align with the star ratings assigned to the respective site or item.

This realization sparked our interest in embarking on a project aimed at correlating the number of stars with sentiment analysis of the reviews. We chose to focus on Lambton College initially, but the methodology can be applied to any site or item featured in Google reviews.

## Chapters

**Problem Definition:** Not always a correlation between the reviews and the number of stars in Google reviews exists. <br>
<strong> Data Gathering: </strong> Webscrapping Google reviews.<br>
**Data Preparation:** ____ <br>
**EDA (Exploratory Data Analysis):** By graphing our data, we can find patterns, correlations, and unfair data. <br>
In the first stage, we did some plotting using Pyplot and Seaborn which allowed us to visualize our data and libraIn this step, I used heatmaps and correlation matrices to analyze the data. <br>
**Data Modelling:** In this project, we used Selenium for Webscapping and VADER and TextBlob for the Sentiment analysis. Furthermore, we used Pandas for dataset management and Seaborn and Pyplot for plotting our data. <br>
**Validate Model:** Revise this.... 

## Chapter 1: Problem definition

The prevalent issue in online reviews, particularly on platforms like Google, is the inconsistency between assigned star ratings and the sentiments conveyed in user reviews. When deciding on a new restaurant or product, users often find discrepancies between numerical ratings and the actual experiences described. This misalignment poses a significant challenge: the need for a more accurate correlation between quantitative ratings and qualitative sentiments. Our project, initially centered on Lambton College, aims to address this gap by developing a methodology applicable to any site or item on Google reviews. Our goal is to create a more reliable connection between star ratings and user sentiments, ultimately enhancing the reliability and usefulness of online reviews in decision-making processes.

## Chapter 2: Data Gathering

The Data Gathering process was done through Webscrapping on Lambton College's Google reviews. The data collected was later copied into a CSV file,  resulting in three columns and one-hundred twenty-eight rows. The column names are listed below:

Name: Name of the person who writes the review. 
Comment: Review
Rating: Number of stars given. 

## Chapter 3: Data Preparation

With the initial phase of data gathering centered on Lambton College's Google reviews, the subsequent step involved meticulous data preparation. The information extracted through web scraping was organized into a structured format within a CSV file. The dataset comprises three key columns: "Name," representing the reviewer's identity; "Comment," encapsulating the textual content of the reviews; and "Rating," indicating the numerical value of stars awarded by the respective users. This systematic arrangement ensures a coherent and standardized dataset, laying the groundwork for subsequent analyses and the development of our correlation methodology. The emphasis on meticulous data preparation is vital to guaranteeing the accuracy and reliability of insights drawn from the collected information, enabling us to effectively address the identified challenge in online reviews.

## Chapter 4: Web Scrapping

### 3.1 Import Libraries for Web Scrapping**


```python
import time
from time import sleep
import random
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By

```
### 3.2 Web scrapping Code
```python

scrollingScript = """ 
      document.getElementsByClassName('m6QErb DxyBCb kA9KIf dS8AEf')[0].scroll(0, 500000)
    """

# Create a Chrome options instance
options = Options()
# Set the user agent
options.add_argument("user-agent=Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.6045.200 Safari/537.36")

service = Service(executable_path="chromedriver.exe")
# Initialize the Chrome driver with the specified options
driver = webdriver.Chrome(service=service, options=options)

driver.get("https://www.google.com/maps/place/Lambton+College/@43.6274247,-79.6771064,17z/data=!4m8!3m7!1s0x882b409fb8a947f9:0x418640e93fdafd13!8m2!3d43.6274208!4d-79.6745315!9m1!1b1!16s%2Fg%2F11c1ldpfm2?entry=ttu")

time.sleep(random.uniform(4.0,5.0))

scrolls = 0
while scrolls != 20:
    driver.execute_script(scrollingScript)
    sleep(random.uniform(5,6))
    scrolls += 1

# Locating the 'More' links and clicking them to expand the review texts
more_links = driver.find_elements(By.XPATH, "//button[contains(text(), 'More')]")
for link in more_links:
    try:
        link.click()
        # Wait a bit for the content to load
        time.sleep(1)
    except Exception as e:
        print(f"Error clicking link: {e}")

# Locating the review comments elements
review_elements = driver.find_elements(By.XPATH, "//div[contains(@class, 'MyEned')]/span[@class='wiI7pd']")

# Locating the star rating elements
star_rating_elements = driver.find_elements(By.XPATH, "//span[contains(@class, 'kvMYJc')]")

```

### 3.3 Generating Dataframe
```python

import pandas as pd

# Locating the names are in an element with a specific class, find them
name_elements = driver.find_elements(By.XPATH, "//div[contains(@class, 'd4r55')]")

# Extracting names, complete reviews, and star ratings
data = []
for name_element, review_element, star_rating_element in zip(name_elements, review_elements, star_rating_elements):
    name = name_element.text  # Get the text directly since the name is the text content of the div
    review_text = review_element.text
    star_rating = star_rating_element.get_attribute('aria-label')
    data.append((name, review_text, star_rating))


# Creating a Pandas DataFrame
df = pd.DataFrame(data, columns=['Name', 'Comment', 'Rating'])

# Display the DataFrame
print(df)

# Optionally, save the DataFrame to a CSV file
df.to_csv('reviews.csv', index=False)


print(df.Comment)

```


Exploring our dataset through visual representation is a crucial step in uncovering patterns, correlations, and potential anomalies. In the initial phase of our analysis, we employed Pyplot and Seaborn to create insightful plots that allowed us to visually grasp the nuances of our data. By utilizing heatmaps and correlation matrices, we delved deeper into the relationships between different variables. These visual tools provided a comprehensive view, enabling us to identify patterns in the data and assess correlations among various attributes. Additionally, this approach facilitated the detection of any inconsistencies or biases in the dataset. Through this thorough exploration, we aim to gain a robust understanding of our data, laying the foundation for informed decision-making and the development of our correlation methodology.

## Chapter 5: Data Modelling

Within this project, our data modeling process involved leveraging specific tools to extract, analyze, and manage our dataset. Selenium played a key role in web scraping, allowing us to efficiently gather data from online sources. For sentiment analysis, we employed VADER and TextBlob, enabling us to delve into the emotional nuances expressed in the textual content of the reviews. In terms of dataset management, Pandas proved to be a robust tool, facilitating seamless organization and manipulation of our collected data. To visualize our findings, we utilized Seaborn and Pyplot, harnessing their capabilities to create informative plots that aid in the interpretation of patterns and correlations within the dataset. This holistic approach to data modeling ensures a comprehensive understanding of the information at hand and supports the subsequent stages of our project.

## Chapter 6: Conclusions

