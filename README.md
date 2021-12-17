# Movies-ETL

## Overview of Project

Given source data in the form of a .JSON file from Wikipedia and two large .CSV files from Kaggle.com, our goal was to extract, transform and load the cleaned and combined data into a PostgreSQL database.  Using Python functions, RegEx expressions, and Pandas DataFrames, the data was thoroughly cleaned before final upload to the database.

### Deliverable 1: [ETL_function_test.ipynb](https://github.com/ZeroDarkHardy/Movies-ETL/blob/main/ETL_function_test.ipynb)

- Function "extract_transform_load" is created to read the Wikipedia JSON file and both Kaggle CSVs into Pandas dataframes.
- Dataframes "wiki_movies_df", "kaggle_metadata", and "ratings" read and cofirmed correct format.

### Deliverable 2: [ETL_clean_wiki_movies.ipynb](https://github.com/ZeroDarkHardy/Movies-ETL/blob/main/ETL_clean_wiki_movies.ipynb)

- Function "extract_transform_load" appended:
    - TV shows removed with list comprehension targeting "No. of episodes".
    - IMDb ID numbers extracted, and duplicate values dropped.
    - Nested function "parse_dollars" created to extract box office and budget values.
- RegEx created to recognize and extract release dates and running time of movies.

### Deliverable 3: [ETL_clean_kaggle_data.ipynb](https://github.com/ZeroDarkHardy/Movies-ETL/blob/main/ETL_clean_kaggle_data.ipynb)

- Previous code appended to clean metadata from Kaggle files.
- Previously inspected data informed our decision of which redundat columns to drop, while filling gaps in data between sources where applicable.
- Columns in "movies_df" filtered and renamed for readability.

### Deliverable 4: [ETL_create_database.ipynb](https://github.com/ZeroDarkHardy/Movies-ETL/blob/main/ETL_create_database.ipynb)

- Once again appending previously generated code, movies without "Director/Directed by" information, or without an IMDb Link, are dropped from the data.
- Ratings data is parsed, and transformed into incremental groups before being merged with our Kaggle and Wikipedia data.
- A connection to a local Postgres database server is established.
- 26,024,289 rows, containing metadata from 6,052 movies, are cleaned and imported into the SQL server.

![movies_query.png](https://github.com/ZeroDarkHardy/Movies-ETL/blob/main/Queries/movies_query.png)

![ratings_query.png](https://github.com/ZeroDarkHardy/Movies-ETL/blob/main/Queries/ratings_query.png)