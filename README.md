# Automated-end-to-end-data-pipeline-using-Python-and-AWS-services
Developed an automated end-to-end data pipeline using Python and AWS services to collect, process, and analyze data from the Spotify API

<img width="908" alt="Pasted Graphic 1" src="https://github.com/user-attachments/assets/146ba0b3-3897-4ecc-939a-173625b605a7">

The pipeline ranges from fetching raw JSON data from the Spotify API-right from track metadata, details on artists, up to information on playlists. Following this, we developed a Python AWS Lambda function to automate fetching the raw data from the API. This Lambda function is configured to run on a daily schedule using Amazon CloudWatch triggers to make sure that the collection of data is fresh in a continuous and timely manner.

After extraction of the raw data, it is safely written directly to an Amazon S3 bucket that plays the role of a data lake for our raw, unprocessed information. At this step, care is taken to make certain that the data is well stored and easily accessible for any downstream processing.

Following that, there will be another AWS Lambda function that automatically triggers every time there is a new data upload onto S3. This function will transform raw JSON into an optimized, structured format suitable for analysis. The function then extracts, transforms, and loads the data it receives from the source into an analytical form with Python and its wide variety of libraries, such as Pandas. It cleans, formats, and converts the JSON data into a table-like structure for analysis, like CSV or Parquet, and maps the data into meaningful columns while normalizing the data in a query/analysis-friendly format. Then, the transformed data is written back to a target S3 bucket holding processed data.

It has been configured to enable querying and analytics of this transformed data by automatically detecting the schema of the data stored in the S3 bucket using an AWS Glue Crawler. Using the crawler, a data catalog can be created that could, in turn, be used by AWS Athena-a serverless query service. With Athena, we are able to run SQL-like queries directly on S3-stored data, generate summaries, and extract valuable insights from the Spotify-processed data. This data can then be further elaborated for reporting, visualization, or machine learning purposes.

This project summarized the whole ETL process: from data ingestion through the Spotify API, to storage and transformation by AWS Lambda and S3, to the final analysis using AWS Glue and Athena, and finally, it should all be an efficiently scalable pipeline for daily analysis.
