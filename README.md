# pdi-Pentaho-Data-Integration

# ETL Process: Sales Data Pipeline

## Project Overview

This project involves building an ETL (Extract, Transform, Load) process that extracts sales data from a CSV file, cleanses and transforms the data, and loads it into a MySQL database for reporting purposes.

## Project Goal

- **Extract**: Read sales data from a CSV file.
- **Transform**: Cleanse and transform the data, including filtering out invalid records and calculating new fields.
- **Load**: Load the transformed data into a MySQL database for further analysis and reporting.

## Steps

### Step 1: Extract Data from CSV

- **Input Step**: Use the CSV File Input step to read data from the CSV file.
- **Configuration**: Define the file path, delimiter, and metadata, including columns like `OrderID`, `Product`, `Quantity`, and `Price`.

### Step 2: Transform the Data

- **Data Cleansing**:
  - **Filter Rows Step**: Filter out records with missing or invalid data. Conditions include filtering out rows where `Quantity` is null and `Price` zero
  - **Output Paths**: Define paths for rows that meet the conditions (valid data) and those that don’t (invalid data).

- **Data Calculation**:
  - **Calculator Step**: Perform calculations, such as computing the `Amount` by multiplying `Quantity` and `Price`.
  - **Additional Operations**: The Calculator step can also handle other mathematical operations like addition, subtraction, and percentage calculations.

### Step 3: Load Data into MySQL

- **Output Step**: Use the Table Output step to load the cleaned and transformed data into a MySQL database.
- **Configuration**: Set up the MySQL connection, select the target table, and map the input fields to the table columns.

### Step 4: Run the Transformation

- **Save Transformation**: Save the transformation.
- **Execute Transformation**: Run the transformation and monitor the execution results to ensure data is loaded successfully.

## Tools Used

- **Pentaho Data Integration (PDI)**: For designing and running the ETL process.
- **MySQL**: As the target database for storing the transformed sales data.


