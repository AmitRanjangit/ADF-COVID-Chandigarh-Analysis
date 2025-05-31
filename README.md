# ADF-COVID-Chandigarh-Analysis
Azure Data Factory pipeline for processing COVID data from Chandigarh

## Project Overview
Split and Export COVID Records by Age Group and Gender

## Overview
This Azure Data Factory (ADF) pipeline processes a CSV dataset containing COVID records with fields such as AGE and GENDER. The objective is to split the dataset into four distinct categories and export each subset into a separate file:

minor_male.csv – AGE < 18 and GENDER = Male
minor_female.csv – AGE < 18 and GENDER = Female
adult_male.csv – AGE >= 18 and GENDER = Male
adult_female.csv – AGE >= 18 and GENDER = Female

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

Output Directory Structure
Example output directory structure in the Blob container:
output/
├── minor/
│   ├── male/
│   │   └── part-00000.csv
│   └── female/
│       └── part-00000.csv
├── adult/
│   ├── male/
│   │   └── part-00000.csv
│   └── female/
│       └── part-00000.csv
Each file contains only the records relevant to that specific group.
