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
















# ETL Process: Multi-Source Sales Data Pipeline

## Project Overview

This project involves building an ETL (Extract, Transform, Load) process to combine sales data from multiple sources, clean and enrich the data, and load it into a MySQL database for reporting purposes.

## Objective

- **Extract**: Retrieve sales data from CSV and Excel files, and currency exchange rates via a REST API.
- **Transform**: Cleanse and enrich the data, join datasets, convert currencies, and aggregate sales data.
- **Load**: Store the final transformed data into a MySQL database for analysis and reporting.

## Tools Used

- **Pentaho Data Integration (Spoon)**
- **MySQL**
- **CSV files**
- **Excel files**
- **REST API**

## Steps

### Step 1: Extract Data from Multiple Sources

- **CSV Input Step**:
  - Load sales data from a CSV file.
  - Map columns such as `ProductID`, `Quantity`, and `Price`.

- **Excel Input Step**:
  - Load product data from an Excel file.
  - Map columns such as `ProductID`, `ProductName`.

- **REST Client Step**:
  - Retrieve the latest currency exchange rates using a REST API.
  - Parse the JSON response to extract relevant fields like `Currency` and `ExchangeRate`.

### Step 2: Join and Enrich the Data

- **Join Rows (Sales and Product Data)**:
  - Merge sales data from the CSV file with product data from the Excel file using `ProductID`.

- **Add Constants (Currency)**:
  - Add a constant value for currency, such as USD, to the dataset.

- **Join Rows (Sales with Exchange Rates)**:
  - Join the enriched sales data with the currency exchange rates using the `Currency` field as the join key.

- **Calculator Step (Convert Prices)**:
  - Calculate converted prices by multiplying `Price` by `ExchangeRate`.

### Step 3: Data Cleansing and Transformation

- **Filter Rows (Invalid Data)**:
  - Filter out invalid or missing data, such as rows where `ProductID` is missing.

- **Group By (Aggregate Sales Data)**:
  - Aggregate sales data by `ProductID`, calculating totals and averages.

- **Sort Rows**:
  - Sort the final dataset by `Date` or `TotalSales`.

### Step 4: Load Data into MySQL

- **Table Output Step**:
  - Load the final transformed data into a MySQL database.
  - Configure the step to insert or update records in the target table.




