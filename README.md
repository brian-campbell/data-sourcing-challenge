# AI Bootcamp - Data Sourcing Challenge - Module 6 Challenge

## Table of Contents
*  [**Overview**](#overview)
*  [**Background**](#background)
*  [**Files**](#files)
*  [**Technical Requirements**](#technical-requirements)
*  [**Run the code**](#run-the-code)
*  [**Requirements and Solution**](#requirements-and-solution)

## Overview
This repository contains the source code for the OSU AI Bootcamp data sourcing challenge for Module 6. This challenge focuses on pulling data from online API's, specifically the New York Times and the Movie Database.

## Background
The background on this challenge, provided by the course instructors is as follows:
>"..prepare some data for a recommendation system to help people find movie reviews and related movies. You will extract data from two different sources: The New York Times API and The Movie Database, then merge the data together. The text extracted from these APIs can later be used with natural language processing methods."

## Files
This repository contains four files:
* `retrieve_movie_data.ipynb` - the file that contains the solution for the challenge. This is a Jupyter Notebook.
* `retrieve_movie_data_orig.ipynb` - the original starter file for the challenge. This is for reference only.
* `movies_data.csv` - an export of the data as required by the last step in the Challenge.
* `README.md` - a README file for the repo.

## Technical requirements
The code for the Challenge is in `retrieve_movie_data.ipynb`. This file is a Jupyter Notebook and requires an appropriate jupyter, pandas, and python tooling installed. This can include environmental containers such a anaconda, etc. It can also be executed inside of an IDE such as Visual Studio Code. The code requires python 3.10 or greater.

The file `athletic_sales_analysis.ipynb` is the original starter file provided for the challenge. It is part of the project for reference only. The directory Resources contains the data file client_dataset.csv provided for the challenge.

## Run the code
Assuming a python interpreter is installed and is at least version 3.10 or greater and they jupyter notebook runtime, the program can be executed by calling the jupyter notebook runtime in the directory: E.g., $> jupyter notebook. Once the notebook is running you run each code fragment individually or click on the "Run All" button.

Alternatively it can be executed from within and IDE if the IDE is configured to run python code and is at least 3.10 compatible and a jupyter notebook runtime is installed.

## Requirements and Solution
### Part 1: Access the New York Times API (35 points)
| Requirement | My Results | Required Results |
| ----------- | ---------- | ---------------- |
| `query_url` is correctly constructed | | |
| An empty list `reviews_list` is created| | |
| A `for` loop is created to loop through 20 times | | |
| The query_url is extended to include a `page` | | |
| A `GET` request is made to retrieve results and the JSON data is stored in a variable called `reviews` | | |
| A 12-second interval is used between queries | | |
| A `try-except` clause is used | | |
| Inside the `try` clause, there is a loop to loop through the `reviews["response"]["docs"]` list | | |
|  The reviews results are correctly appended to `reviews_list` | | |
| The query page number is printed | | |
| The `except` clause prints out the page number that had no results, then breaks from the loop | | |
| `json.dumps` with the argument `indent=4` is used to preview the first five results | | |
| `reviews_list` is converted to a Pandas DataFrame using `json_normalize()` | | |
| The title is extracted from the `"headline.main"` column and is saved in a new column `"title"` | | |
| The `"keywords"` column is correctly converted to string data using the supplied `extract_keywords` function | | |
| A list called `titles` is created from the "title" column using `to_list()` | | |


### Part 2: Access The Movie Database API (40 points)
| Requirement | My Results | Required Results |
| ----------- | ---------- | ---------------- |
| An empty list called `tmdb_movies_list` is created | | |
| A variable called `request_counter` is created and assigned the value of `1` | | |
| A `for` loop is created to loop through the `titles` list | | |
| `request_counter` is incremented by `1` | | |
| `time.sleep(1)` when `request_counter` reaches a multiple of `50` | | |
| A `GET` request that sends the title to The Movie Database search is performed, and the JSON results are retrieved | | |
| A `try-except` clause is used | | |
| The `except` clause prints out a statement if a movie is not found | | |
| The movie ID is collected from the first result and saved as a variable | | |
| A `GET` request is made using the movie query URL and movie ID to retrieve the full movie details in JSON format | | |
| The genre names are extracted from the results into a list called `genres` | | |
| The `spoken_languages`' English names are extracted from the results into a list called `spoken_languages` | | |
| The `production_countries`' names are extracted from the results into a list called `production_countries` | | |
| A dictionary is created with the specified 15 fields | | |
| The results dictionary is appended to the `tmdb_movies_list` list | | |
| A message is printed with the name of the movie to indicate that the title was found. | | |
| The first five results are previewed using `json.dumps` with the argument `indent=4` | | |
| The results are converted to a DataFrame called `tmdb_df` with `pd.DataFrame()` | | |


### Part 3: Merge and Clean the Data for Export (25 points)
| Requirement | My Results | Required Results |
| ----------- | ---------- | ---------------- |
| The New York Times reviews and TMDB DataFrames are merged on the title column | | |
| A list called `columns_to_fix` is created to store the names of the `genres`, `spoken_languages`, and `production_countries` columns | | |
| A list is created called `characters_to_remove` containing `[`, `]`, and `'` | | |
| A `for` loop is created to loop through `columns_to_fix` | | |
| The columns to fix are converted to the string data type | | |
| `characters_to_remove` is looped through to remove the characters from the string using the Pandas `str.replace()` method | | |
| The head of the updated DataFrame is displayed to confirm the list characters were removed | | |
| The `byline.person` column is dropped | | |
| Duplicate rows are deleted | | |
| The DataFrame index is reset | | |
| The DataFrame is exported to a CSV file without the index | | |

