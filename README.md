# Comparative Analysis of Google BigQuery and MySQL

## Project Overview

This project aims to conduct a comparative analysis between Google BigQuery and MySQL regarding their performance in handling datasets of varying sizes. The analysis focuses on operational efficiency, speed, scalability, and overall efficacy of both platforms through the execution of six distinct queries on datasets of different scales.

## Introduction

The project evaluates the performance of Google BigQuery and MySQL across two datasets: a large dataset comprising 13 million rows and a smaller dataset of 0.1 million rows. By executing six queries on each platform for both dataset sizes, the project aims to uncover insights into their strengths and weaknesses.

## Database Tools

### Google BigQuery

Google BigQuery is a serverless, cloud-based data warehouse known for its scalability and high-speed processing capabilities. It operates with SQL-based queries, offers built-in machine learning features, and facilitates cross-cloud analytics.

### MySQL

MySQL is an open-source relational database management system recognized for its reliability, cost-effectiveness, and flexibility in cloud deployment. It is widely used in diverse web applications and offers robust performance for transactional operations and smaller datasets.

## Dataset Description

The project utilizes a dataset detailing reported crimes in London, encompassing various crime types categorized by major and minor categories, boroughs, and Lower Layer Super Output Areas (LSOAs). The dataset provides insights into crime trends, locations, and types, facilitating detailed analysis.

This dataset is publicly accessible and can be directly queried using GoogleSQL on the BigQuery platform (bigquery-public-data.london_crime.crime_by_lsoa). The dataset was exported to a CSV file, in order to load it into MySQL.

We have also derived a subset of the London Crimes dataset, containing approximately 0.1 million rows, by executing a select query within the BigQuery platform. The results of this query were exported to a CSV file, constituting our smaller dataset.

## Experiment Environment Setup

Google BigQuery and MySQL were employed for storing and querying the datasets. The setup process for both platforms involved importing CSV files, creating tables, and configuring Python environments for querying.

## Evaluation Metrics

Query processing time serves as the primary evaluation metric, reflecting the duration taken by each system to execute queries and retrieve results. It provides insights into system efficiency, user experience, resource utilization, and scalability.

Query processing time can differ significantly between Google BigQuery and MySQL due to their distinct architectures and underlying mechanisms. The differences in how these systems handle data storage, query optimization, and parallel processing contribute significantly to variations in query processing times observed between Google BigQuery and MySQL.

## Experiment Design

To compare the query performance between Google BigQuery and MySQL, we have set up a simple experiment using two datasets and running similar queries on both platforms.

1. A predefined list of six queries is stored in ‘query_list’, representing various types of queries that commonly occur in data analysis scenarios.
2. Each query is executed 10 times to ensure a robust assessment of querying time.
3. The start time is recorded before the query execution, and the end time is recorded after the query is completed. The querying time for each run is calculated as the time elapsed during query execution.
4. For each query, the querying times from the 10 runs are averaged to obtain a representative average query time. The average querying times for all queries are stored in the ‘avg_query_times’ list.
5. These queries were executed on two datasets, both stored on two different platforms, thereby offering a comparative analysis of the performance between Google BigQuery and MySQL.

Any number of queries in the ‘query_list’ can be accommodated by the experiment's adaptable structure. In order to account for possible differences in querying time and to create a robust average, the design takes into consideration the significance of repeated runs.

## Results

## Query Processing Time Comparison

### Large Dataset (13 million rows)

| Query ID |                Query Description                | Avg Query Time (sec) MySQL | Avg Query Time (sec) BigQuery |
|:--------:|:----------------------------------------------:|:-----------------------:|:--------------------------:|
|     1    |      Crime Counts by Major Category and Year   |          14.75          |            1.15            |
|     2    |     Crime Counts by Borough in the Year 2016   |           6.95          |            1.21            |
|     3    | Monthly Crime Trend for Westminster (borough) in 2013 |         6.55          |            1.19            |
|     4    |   Crime Counts per Minor Category in Camden (borough) |       6.61          |            1.19            |
|     5    | Top 10 Boroughs with the Highest Crime Counts for Major Category 'Violence Against the Person' | 8.61 | 1.15  |
|     6    |   Percentage Distribution of Crimes Across Major Categories |     14.8         |            1.04            |

**Table 1:** Query Processing Time for Large Dataset

BigQuery demonstrates superior performance compared to MySQL across all queries when handling the large dataset, displaying notably reduced average query times. On MySQL, the query processing time is roughly six times longer than on BigQuery. The efficiency gap between BigQuery and MySQL is more pronounced for complex queries involving multiple categories and year-wise aggregations.

### Small Dataset (0.1 million rows)

| Query ID |                Query Description                | Avg Query Time (sec) MySQL | Avg Query Time (sec) BigQuery |
|:--------:|:----------------------------------------------:|:-----------------------:|:--------------------------:|
|     1    |      Crime Counts by Major Category and Year   |           0.07          |            1.7             |
|     2    |     Crime Counts by Borough in the Year 2016   |           0.03          |            1.4             |
|     3    | Monthly Crime Trend for Westminster (borough) in 2013 |         0.02          |            1.48            |
|     4    |   Crime Counts per Minor Category in Camden (borough) |       0.02          |            1.45            |
|     5    | Top 10 Boroughs with the Highest Crime Counts for Major Category 'Violence Against the Person' | 0.05 | 1.41 |
|     6    |   Percentage Distribution of Crimes Across Major Categories |     0.07          |            1.29            |

**Table 2:** Query Processing Time for Small Dataset

BigQuery is showing longer query processing times for a smaller dataset compared to a larger one, despite the inherent expectation that smaller datasets should generally process more quickly. One potential reason could be related to the storage structure and optimization. BigQuery is optimized for handling massive datasets and parallel processing. When dealing with the large publicly available dataset (13 million rows), it likely benefits from its optimized storage and processing infrastructure. However, when a smaller dataset is stored as a new table manually, it might not utilize the same level of optimization as the pre-existing larger dataset. Also, differences in how the data is stored, partitioned, or indexed between the large publicly available dataset and the manually stored smaller dataset can influence query processing times on BigQuery.

Contrary to the trend observed in the large dataset, MySQL demonstrates much better performance than BigQuery for the small dataset. MySQL exhibits faster query processing times, indicating that for smaller datasets, MySQL may offer advantages in terms of efficiency.

While BigQuery consistently outperforms MySQL in handling large-scale datasets, the analysis reveals that MySQL may exhibit better performance for smaller datasets. The choice between BigQuery and MySQL should consider the specific characteristics of the dataset size and the nature of the queries to be executed.

## Conclusion

The project's findings illuminate the importance of considering dataset size when selecting a database management tool. While Google BigQuery excels in handling large datasets, MySQL proves to be a competitive choice for smaller datasets. The choice between Google BigQuery and MySQL depends on specific organizational requirements, dataset sizes, and query complexities. These insights can offer valuable guidance for decision-makers and database administrators in tailoring their tool selection to the specific demand. Regular monitoring and optimization efforts will contribute to maintaining an efficient and effective data processing infrastructure.

The choice between Google BigQuery and MySQL depends on specific organizational requirements, dataset sizes, and query complexities. While BigQuery excels in handling large datasets, MySQL proves competitive for smaller datasets. Regular monitoring and optimization efforts are essential for maintaining an efficient data processing infrastructure.

## References

1. Google BigQuery Documentation - [Link](https://cloud.google.com/bigquery/docs)
2. Hossain, M. A. (2021). Big data analysis using BigQuery on cloud computing platform.
3. Kashyap, R. (2023). Machine learning in Google Cloud BigQuery using SQL.
4. Sinha, G., & Ambhaikar, A. (2021). Scalable Data Processing for Prediction, Batch Computation, and Analysis using Google BigQuery.
5. Trenčeva, Ž., et al. (2022). BigQuery for Big Data Analysis.

## Appendix

Python notebooks used for the experiment are included. However, the credentials.json file required for accessing BigQuery from Python has not been included for security reasons.
