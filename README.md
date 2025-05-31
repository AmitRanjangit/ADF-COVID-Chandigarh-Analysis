# ADF-COVID-Chandigarh-Analysis
Azure Data Factory pipeline for processing COVID data from Chandigarh

## Project Overview
Split and Export COVID Records by Age Group and Gender

## Overview
This Azure Data Factory (ADF) pipeline processes a CSV dataset containing COVID records with fields such as AGE and GENDER. The objective is to split the dataset into four distinct categories and export each subset into a separate file:

### Output Files

- **minor_male.csv** – Records with `AGE < 18` and `GENDER = Male`  
- **minor_female.csv** – Records with `AGE < 18` and `GENDER = Female`  
- **adult_male.csv** – Records with `AGE >= 18` and `GENDER = Male`  
- **adult_female.csv** – Records with `AGE >= 18` and `GENDER = Female`

What This Pipeline Does
Uses a Mapping Data Flow instead of Copy Data to handle complex row-level filtering and to create multiple outputs.
Source transformation reads the original CSV file from Azure Blob Storage.
Conditional Split transformation divides the incoming dataset into four branches based on age and gender conditions.
Each branch is connected to a Sink that writes filtered data to a unique output location.

ADF Components Used
Source: Azure Blob Storage (CSV file with AGE, GENDER)
Mapping Data Flow: Includes conditional logic to split data
Sinks: One for each age and gender category

Pipeline: Executes the Mapping Data Flow

## Mapping Data Flow Design

The Mapping Data Flow is the core of this pipeline and handles the data filtering and file creation.

### Steps in the Data Flow

1. **Source**  
   Reads the original CSV file containing COVID data with columns such as `AGE` and `GENDER`.

2. **Conditional Split**  
   Splits the data stream into four branches based on the following conditions:

   - **Minor Male**: `AGE < 18` and `GENDER == 'Male'`  
   - **Minor Female**: `AGE < 18` and `GENDER == 'Female'`  
   - **Adult Male**: `AGE >= 18` and `GENDER == 'Male'`  
   - **Adult Female**: `AGE >= 18` and `GENDER == 'Female'`

3. **Sink for Each Branch**  
   Each branch writes to a separate folder in the Azure Blob Storage output container, e.g.,

   - `output/minor/male/`  
   - `output/minor/female/`  
   - `output/adult/male/`  
   - `output/adult/female/`

   The files are saved as CSV with names like `part-00000.csv`. No explicit file name is set to allow auto-scaling and partitioning.

### Benefits of This Design

- Scalable and efficient for large datasets  
- Easy to maintain and extend for additional categories  
- Uses ADF’s native data flow capabilities for in-memory filtering and writing  
- Avoids multiple copy activities and manual filtering steps  

### Summary

This Mapping Data Flow efficiently separates and exports COVID data into age and gender-specific files, stored in a structured directory hierarchy for easy access and analysis.
