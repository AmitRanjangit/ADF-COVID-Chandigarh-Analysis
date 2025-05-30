# ADF-COVID-Chandigarh-Analysis
Azure Data Factory pipeline for processing COVID data from Chandigarh

## Project Overview
This project demonstrates key Azure Data Factory (ADF) concepts using a single CSV file containing COVID-19 case data from Chandigarh, India.

While the dataset is limited to one file and the pipeline is not fully automated end-to-end, this project showcases the use of several important ADF activities and features, including Copy Activity, Lookup, ForEach loops, Web Activity, Variables, and Parameters.

The main goal is to provide a clear example of how these components can be used together in data integration workflows within Azure Data Factory.

---

## Dataset Description
The dataset used contains the following fields:

| Column Name    | Description                                  |
| -------------- | --------------------------------------------|
| STATE          | Name of the state (Chandigarh)               |
| CITY NAME      | City within the state                         |
| SAMPLE ID      | Unique identifier for each COVID-19 sample   |
| AGE            | Age of the individual tested                  |
| GENDER         | Gender of the individual                       |
| SAMPLE RESULT  | Test result (e.g., Positive, Negative)        |
| RESULT DATE    | Date when the test result was reported         |
| CURRENT STATUS | Patient status (e.g., Recovered, Active, Deceased) |

---

## ADF Concepts Demonstrated

- Copy Activity: Copying the CSV data from Azure Blob Storage to a destination store or staging area.
- Lookup Activity: Retrieving metadata or performing conditional checks on the data.
- ForEach Activity: Iterating over rows or datasets for individual processing or validation.
- Web Activity: Calling external REST APIs or simulating notifications based on data.
- Variables and Parameters: Controlling dynamic pipeline behavior and passing values between activities.

---

## Pipeline Workflow Summary

1. Manual Upload of Data: The COVID-19 CSV file is manually uploaded to Azure Blob Storage as the data source.
2. Copy Activity: Copies the CSV data to a target location, demonstrating data movement capabilities.
3. Lookup Activity: Performs checks or data validations on the copied data.
4. ForEach Loop: Iterates over data entries for row-wise processing or logic demonstration.
5. Web Activity: Simulates external service calls, such as triggering alerts or APIs.
6. Use of Variables and Parameters: Demonstrates dynamic control and passing of runtime values within the pipeline.

> Note: This project is intended as a learning and demonstration exercise and does not include a fully automated pipeline triggered by events or schedules.
