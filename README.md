# AirPulse-AQI-Data-Pipeline-on-AWS  ( In Developement )
A serverless ETL pipeline on AWS that ingests air quality (AQI) data for Indian cities, stores it in S3, transforms it into an analytics-friendly format, and makes it queryable with SQL.



# Status: In development (planning / design stage). The architecture and repository structure are defined. The pipeline is not built or deployed yet. This README describes the intended design and will be updated as each stage is completed.

# Goal 
Build a small, end-to-end data engineering project to practice the core AWS data stack:

1.Ingest raw AQI data on a schedule
2.Store raw and processed data in separate S3 layers
3.Clean and convert data to a columnar format (Parquet)
4.Query the results with SQL using Athena

# Planned Architecture
AQI data source (API)
        |
        v
AWS Lambda (ingest.py)         -- fetch + write raw JSON
        |
        v
S3 (raw/)                      -- raw JSON, as received
        |
        v
AWS Glue (ETL job)             -- clean, standardise, convert to Parquet
        |
        v
S3 (processed/)                -- partitioned Parquet
        |
        v
Glue Data Catalog --> Amazon Athena   -- SQL analysis

# Tech Stack

- **Ingestion:** AWS Lambda (Python)
- **Storage:** Amazon S3
- **Transformation:** AWS Glue, pandas, Parquet
- **Querying:** Amazon Athena (SQL)
- **Access control:** AWS IAM
- **Visualisation (optional):** Amazon QuickSight

# Repository Structure
aqi-data-pipeline-aws/
├── README.md
├── .gitignore
├── lambda/
│   └── ingest.py            # Lambda function to fetch AQI data and write to S3
├── sql/
│   └── athena_queries.sql   # Athena table definitions and analysis queries
├── docs/
│   └── notes.md             # Design notes and learnings
└── sample_data/
    └── sample_aqi.json      # Sample of the raw data format


## Progress

- [x] Choose the AQI data source
- [ ] Set up S3 bucket (raw and processed folders)
- [ ] Write Lambda function to fetch AQI data
- [ ] Set up IAM roles
- [ ] Schedule Lambda to run automatically
- [ ] Build Glue job to clean data and save as Parquet
- [ ] Create Athena table and write queries
- [ ] Add QuickSight dashboard (optional)
- [ ] Document results and lessons learned
      
    
## Notes

- This project is built to stay within the AWS free tier. I plan to delete all resources after the build to avoid charges.
- No AWS credentials or API keys are stored in this repo.

## Author
Reema Saleem
