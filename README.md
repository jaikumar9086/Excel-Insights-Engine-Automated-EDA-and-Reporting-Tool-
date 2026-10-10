# Excel to Insights Engine

A powerful Python tool for extracting meaningful insights from Excel files without requiring advanced data science knowledge.

## Overview

Excel to Insights Engine is a Python-based tool designed to help users quickly analyze Excel data and extract valuable insights. The tool performs various analyses including statistical summaries, correlation detection, outlier identification, categorical data analysis, and date-based analysis. It also generates visualizations and comprehensive reports to help users understand their data better.

## Features

- **Excel Data Loading**: Load data from single or multi-sheet Excel files
- **Basic Information**: Get row/column counts, data types, and missing value summaries
- **Summary Statistics**: Calculate mean, median, standard deviation, and other statistics for numerical columns
- **Correlation Analysis**: Identify relationships between numerical columns
- **Outlier Detection**: Find and report unusual values in your data
- **Categorical Data Analysis**: Analyze distributions and frequencies of categorical variables
- **Date Analysis**: Extract patterns and trends from date columns
- **Data Visualization**: Generate charts and graphs to visualize your data
- **Insights Report**: Create comprehensive markdown reports summarizing all findings

## Installation

### Prerequisites

- Python 3.6 or higher
- pip (Python package installer)

### Setup

1. Clone or download this repository:

```bash
git clone https://github.com/yourusername/excel-insights-engine.git
cd excel-insights-engine
```

2. Install the required dependencies:

```bash
pip install pandas numpy matplotlib openpyxl
```

## Usage

### Basic Usage

```python
from excel_insights import ExcelInsights

# Create an instance and load an Excel file
insights = ExcelInsights('path/to/your/file.xlsx')
insights.load_excel()

# Get basic information about the data
info = insights.get_basic_info()
print(f"Rows: {info['rows']}, Columns: {info['columns']}")

# Generate summary statistics
insights.generate_summary_statistics()

# Find correlations
correlations = insights.find_correlations(threshold=0.7)

# Identify outliers
outliers = insights.identify_outliers()

# Analyze categorical data
insights.analyze_categorical_data()

# Analyze date columns
insights.analyze_date_columns()

# Generate visualizations
insights.visualize_data(output_dir='visualizations')

# Generate insights report
insights.generate_insights_report(output_file='insights_report.md')
```

### Command Line Usage

You can also run the tool from the command line:

```bash
python excel_insights.py path/to/your/file.xlsx
```

This will perform a complete analysis and save the results to the current directory.

## Example Output

### Insights Report

The tool generates a comprehensive markdown report that includes:

- File information (name, path, sheets, rows, columns)
- Summary statistics for numerical columns
- Correlation analysis
- Outlier detection results
- Categorical data analysis
- Date column analysis

### Visualizations

The tool creates various visualizations including:

- Histograms for numerical columns
- Bar charts for categorical columns
- Correlation heatmaps
- Box plots for outlier detection
- Pie charts for categorical distributions

## Sample Data

The repository includes sample Excel files in the `data` directory that you can use to test the tool:

- `sales_data.xlsx`: Sample sales data with products, regions, and metrics
- `employee_data.xlsx`: Sample HR data with employee information
- `customer_data.xlsx`: Sample customer data with demographics and purchase history
- `sample_data.xlsx`: Multi-sheet Excel file combining all three datasets

You can generate these sample files using the included script:

```bash
python create_sample_data.py
```

## Detailed Feature Documentation

### ExcelInsights Class

The main class that provides all functionality for the Excel to Insights Engine.

#### Methods

- `__init__(file_path=None)`: Initialize the class with an optional file path
- `load_excel(file_path=None)`: Load an Excel file into pandas DataFrames
- `get_basic_info()`: Get basic information about the loaded data
- `generate_summary_statistics(sheet_name=None)`: Generate summary statistics for numerical columns
- `find_correlations(sheet_name=None, threshold=0.5)`: Find correlations between numerical columns
- `identify_outliers(sheet_name=None, method="iqr", threshold=1.5)`: Identify outliers in numerical columns
- `analyze_categorical_data(sheet_name=None, top_n=5)`: Analyze categorical columns in the data
- `analyze_date_columns(sheet_name=None)`: Analyze date columns in the data
- `generate_insights_report(output_file=None)`: Generate a comprehensive insights report
- `visualize_data(output_dir=None, sheet_name=None)`: Generate visualizations for the data

### Analysis Methods

#### Summary Statistics

The tool calculates the following statistics for numerical columns:
- Count
- Mean
- Standard Deviation
- Minimum
- 25th Percentile
- Median (50th Percentile)
- 75th Percentile
- Maximum

#### Correlation Analysis

The tool identifies pairs of numerical columns with correlation coefficients above a specified threshold. This helps in understanding relationships between different variables in your data.

#### Outlier Detection

Two methods are available for outlier detection:
- **IQR Method**: Uses the Interquartile Range to identify values that fall outside 1.5 × IQR from the first and third quartiles
- **Z-Score Method**: Identifies values that are a specified number of standard deviations away from the mean

#### Categorical Analysis

For categorical columns, the tool provides:
- Count of unique values
- Missing value count and percentage
- Top categories with counts and percentages

#### Date Analysis

For date columns, the tool analyzes:
- Date range (minimum and maximum dates)
- Range in days
- Missing value count and percentage
- Day of week distribution
- Month distribution
- Year distribution

## Customization

### Modifying Thresholds

You can customize various thresholds used in the analysis:

```python
# Change correlation threshold
correlations = insights.find_correlations(threshold=0.8)  # Default is 0.5

# Change outlier detection method and threshold
outliers = insights.identify_outliers(method="zscore", threshold=3)  # Default is method="iqr", threshold=1.5

# Change number of top categories in categorical analysis
insights.analyze_categorical_data(top_n=10)  # Default is 5
```

### Working with Multi-Sheet Excel Files

For multi-sheet Excel files, you can specify which sheet to analyze:

```python
# Generate summary statistics for a specific sheet
insights.generate_summary_statistics(sheet_name="Sales")

# Find correlations in a specific sheet
insights.find_correlations(sheet_name="Employees")

# Visualize data from a specific sheet
insights.visualize_data(output_dir="visualizations", sheet_name="Customers")
```

## Limitations

- The tool is designed for structured tabular data in Excel format
- Performance may degrade with very large Excel files (millions of rows)
- Visualization capabilities are focused on common chart types
- No advanced machine learning or predictive analytics features
