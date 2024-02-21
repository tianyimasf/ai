---
layout: post
title: "Data cleaning and transformation in Python: Analyze LinkedIn Job Postings"
categories: [Data Cleaning, Data Manipulation, Data Tranformation]
excerpt: Data cleaning and transformation is usually the first step in the data analysis process. For each project's specific purpose, we might find data from multiple different data sources, in different formats, and need to be combined and cleaned so that later when we are analyzing, we have high quality data that is necessary for a good outcome.
---

Data cleaning and transformation is usually the first step in the data analysis process. For each project's specific purpose, we might find data from multiple different data sources, in different formats, and need to be combined and cleaned so that later when we are analyzing, we have high quality data that is necessary for a good outcome.

Since real life data are so messy, the data preparation steps are usually different from project to project. In this blog, we look at a specific application: analyzing LinkedIn job postings, especially jobs related to Data/AI. We'll look at the data cleaning and transformations we need to do, and in future blogs talks about further analysis. [The google colab for this is here](https://colab.research.google.com/drive/1X-l681ONO4KBlak7Pf4-JfGUloOP1549?usp=sharing). Feel free to make a copy, download the data, and play around with the code.

The notebook contains everything in this blog.

Now let's look at the data sources we got.

We are using 8 different datasets here. Below are their sources:

1. [LinkedIn-Tech-Job-Data](https://github.com/Mlawrence95/LinkedIn-Tech-Job-Data): A compilation of job posts and metadata scraped from various tech categories on LinkedIn

2. [Data Analyst Jobs](https://www.kaggle.com/datasets/andrewmvd/data-analyst-jobs): This dataset was created by picklesueat and contains more than 2000 job listing for data analyst positions

3. [US Job Postings from 2023-05-05](https://www.kaggle.com/datasets/techmap/us-job-postings-from-2023-05-05): This dataset is an excerpt of our web scraping activities at Techmap.io and contains a sample of 33k Job Postings from the USA on May 5th 2023.

4. [LinkedIn Job Postings Dataset](https://www.kaggle.com/datasets/rajatraj0502/linkedin-job-2023?select=job_postings.csv): This dataset contains information about job postings on LinkedIn.

5. [LinkedIn Job Postings - Machine Learning Data Set](https://www.kaggle.com/datasets/adampq/linkedin-jobs-machine-learning-data-set?select=LinkedInJobs_MLDataset.csv): The data comprises job-related information from LinkedIn job postings scraped over a 2-day period.

6. [Linkedin Canada: Data Science Jobs 2024](https://www.kaggle.com/datasets/kanchana1990/linkedin-canada-data-science-jobs-2024): The "LinkedIn Canada: Data Science Jobs 2024" dataset presents an insightful overview of the data science job market in Canada as sourced from LinkedIn.

7. [Data Scientist - Linkedin Job Postings](https://www.kaggle.com/datasets/asaniczka/data-scientist-linkedin-job-postings): This dataset provides valuable insights into data science job postings, including the required skills and software proficiency sought by employers.

8. [LinkedIn Job Postings Dataset](https://www.kaggle.com/datasets/rajatraj0502/linkedin-job-2023): This dataset contains information about job postings on LinkedIn.

They come in different formats, some are CSV files, while others are in JSON format. Let's load them in and combine them together, and do some data cleaning.

# Load the Data

## Check the datasets' paths

The reason we want the paths is so we could copy paste the printed results, delete the paths we don't want, and load the data iteratively later.

To print and load the paths we use the `os` module. The OS module in Python provides functions for interacting with the operating system. OS comes under Python's standard utility modules.

We use the `os.walk` method. Python method `os.walk` generates the file names in a directory tree by recursively walking the tree. We concatenate the paths so that we can access the files later.

```python
import os

paths = []
for dirname, _, filenames in os.walk('data'):
    for filename in filenames:
        paths.append(os.path.join(dirname, filename))
paths
```

## Peek at relevant csv files to see what field we should use

As mentioned before, I copy-pasted the printed array above and manually removed the ones irrelevant to our analysis. We can then loop through those paths, read them into a dataframe using pandas (`pd.read_csv(path)`), and peek at the first 5 rows of the dataset using `df.head()`. Because we are printing the head in a loop, we need to use the function `display`.

```python
import pandas as pd
import numpy as np
from IPython.display import display
```

```python
paths_csv = ['data\\DataAnalyst.csv',
 'data\\jobs.csv',
 'data\\LinkedInJobs_MLDataset.csv',
 'data\\linkedin_canada.csv',
 'data\\postings.csv',
 'data\\1\\job_postings.csv',
 'data\\1\\job_details\\job_skills.csv',
 'data\\1\\maps\\skills.csv',
 'data\\2\\job_postings.csv',
 'data\\2\\job_skills.csv']

for p in paths_csv:
    df = pd.read_csv(p)
    display(df.head())
```

As you can see reading through the head rows, the description column can be called "job_desc" or "job_summary". Here we can therefore concatenate all description by getting column names of each dataframe, convert them to lower cases, check if they include the substring "desc" or "summary", and match the columns that are job descriptions. Then we access values of that column and concatenate them together.

```python
def get_job_desc(df):
    columns = list(df.columns.values)

    # return the first matching name of column if name contains "desc" or "summary" as substring
    # works since we know there's only one such matching name for each dataframe
    column_name = [name for name in columns if ("desc" in name.lower()) | ("summary" in name.lower())][0]
    return df[column_name]
```

Try the below code block, and you'll see it prints out the first job description of the first file in our paths. We can get almost 100k descriptions by looping through files and concatenate the descriptions.

```python
df = pd.read_csv(paths_csv[0])
print(get_job_desc(df)[0])
```

## Filter Only Data/AI Job Postings

Wait...what's the goal of this analysis again? Yes, we only need descriptions for Data/ML/AI jobs. So we should filter for those titles. Here, we can modify the `get_job_desc()` function to only return the column name, and use another function to filter the titles.

```python
def get_desc_column_name(df):
    columns = list(df.columns.values)

    # return the first matching name of column if name contains "desc" or "summary" as substring
    # works since we know there's only one such matching name for each dataframe
    column_name = [name for name in columns if ("desc" in name.lower()) | ("summary" in name.lower())][0]
    return column_name
```

To get title values, we first need a function to extract the column name of the title values, so that we can access title values. The how-to is similar to how we get column name for job descriptions.

```python
def get_title_column_name(df):
    columns = list(df.columns.values)

    # return the first matching name of column if name contains "title" or "ttl" as substring
    # works since we know there's only one such matching name for each dataframe
    column_name = [name for name in columns if ("title" in name.lower()) | ("ttl" in name.lower())][0]
    return column_name
```

Then, we create a function that will be applied to every title value to determine if it's a data/ML/AI job, since pandas/python doesn't have such function built in. Here, we create a list of keywords that will appear in the title if they job is related to Data/AI. We also create a list of abbreviation terms, since if we don't then we'll get titles like "therapy [ai]de", which include the term ai but is not really a tech job.

Then we loop through the keyword lists to see if any of it is contained in the title string. If we found at least 1, we say that the job title is a tech job title.

```python
def is_tech_job(title):
    job_titles = ["data", "machine learning", "artificial intelligence", "computer vision", "search",
                  "vision", "research", "analyst", "analysis", "mlops", "stat", "natural language processing",
                 "large language model", "generative ai", "genai", "deep learning", "analytics"]
    job_titles_abbr = ["AI", "ML", "LLM", "NLP"]
    matching_title = [t for t in job_titles if t in title.lower()]
    matching_title_abbr = [t for t in job_titles_abbr if t in title]

    return len(matching_title) > 0 or len(matching_title_abbr) > 0
```

Combining the functions `get_title_column_name()`, `get_desc_column_name()`, `is_tech_job()`, we use `df.loc[]` and `apply` to apply the `is_tech_job()` function to values in the title column. This will give us a dataframe with only tech jobs listed. Then we get the title and description, and standardize the column names by assigning the names "title", "description" to `df.columns`.

```python
def get_relevent_jobs(df):

    # Get relevant column names
    title_column_name = get_title_column_name(df)
    desc_column_name = get_desc_column_name(df)

    # Get tech job listings
    df_filtered = df.loc[df[title_column_name].apply(is_tech_job)]

    # Get only the title and description columns and standardize column naming
    columns_renamed = {title_column_name: "title", desc_column_name: "description"}
    df_new = df_filtered[[title_column_name, desc_column_name]]
    df_new.columns = ["title", "description"]

    return df_new
```

Try the code below to test using one dataframe with general job titles:

```python
df = pd.read_csv(paths_csv[2])
df = get_relevent_jobs(df)
df.shape
```

We see that the dataframe has shape `(2993, 2)`, much lower than what we would have with all job descriptions.

## Collate all CSV files

First, we create an empty dataframe(`df`) with the standardized column names we defined. Then, we get tech job listings(`df_p`) from each csv files, and concatenate `df` with `df_p` using `pd.concat()`. The first argument of that function is the list of dataframes you want to concatenate, and `axis=0` means you are adding `df_p`'s rows to `df`. If `axis=1`, then you are adding `df_p`'s column to `df`.

```python
df = pd.DataFrame(columns=['title', 'description'])

for p in paths_csv:
    df_p = pd.read_csv(p)
    df_p = get_relevent_jobs(df_p)
    df = pd.concat([df, df_p], axis=0)

df.shape
```

We get `(17439, 2)`, 17.5k rows of data points in total for csv files (remember we still need to process JSON files!).

We can shuffle rows of data and check out different job titles and their descriptions.

By sampling with `frac=1`, you are basically resampling the whole dataset. Then we use `reset_index()` and setting `drop=True` to prevents `.reset_index` from creating a column containing the old index entries.

```python
df = df.sample(frac=1).reset_index(drop=True)
df.head()
```
