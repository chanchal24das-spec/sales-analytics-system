# Sales Analytics System

A comprehensive data cleaning, processing, and analytics system for sales data with API integration and automated reporting.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Setup](#setup)
- [Usage](#usage)
- [System Components](#system-components)
- [Output Files](#output-files)
- [Data Flow](#data-flow)

---

## 🎯 Overview

The Sales Analytics System is a complete Python-based solution that:
1. Cleans and validates raw sales data
2. Performs comprehensive analytics and reporting
3. Integrates with external APIs to enrich product data
4. Generates detailed, formatted reports for business insights

---

## ✨ Features

### Part 1: Data Cleaning & Validation
- ✅ Removes invalid records based on business rules
- ✅ Cleans data formatting issues (commas in numbers, product names)
- ✅ Validates transaction integrity
- ✅ Filters data by region and transaction amount
- ✅ Handles encoding issues automatically

### Part 2: Data Processing & Analytics
- 📊 **Revenue Analysis**: Total revenue calculation
- 🌍 **Regional Performance**: Sales breakdown by region with percentages
- 📦 **Product Analytics**: Top-selling products by quantity and revenue
- 👥 **Customer Insights**: Customer purchase patterns and behavior
- 📅 **Temporal Analysis**: Daily sales trends and peak performance days
- ⚠️ **Performance Monitoring**: Low-performing product identification

### Part 3: API Integration
- 🔌 **External Data Fetching**: Integration with DummyJSON product API
- 🔗 **Data Enrichment**: Enhances sales data with product categories, brands, and ratings
- 📈 **Match Tracking**: Reports enrichment success rates
- 🛡️ **Error Handling**: Graceful handling of API failures

### Part 4: Comprehensive Reporting
- 📄 **Professional Reports**: Formatted text reports with all analytics
- 📊 **Multi-section Analysis**: 7 detailed sections covering all aspects
- 💾 **Easy Export**: Plain text format for easy sharing and review

---

## 📁 Project Structure

```
sales-analytics-system/
├── README.md                   # This file
├── requirements.txt            # Python dependencies
├── main.py                     # Main execution script (runs everything)
├── test_task31.py             # API integration tests (optional)
│
├── data/
│   ├── sales_data.txt         # Input: Raw sales data
│   └── enriched_sales_data.txt # Output: API-enriched data
│
├── output/
│   ├── sales_data_cleaned.txt      # Cleaned valid records
│   ├── invalid_records.txt         # Removed invalid records
│   ├── enriched_sales_data.txt     # Copy of enriched data
│   └── sales_report.txt            # ⭐ Comprehensive final report
│
└── utils/
    ├── __init__.py             # Package initializer
    ├── file_handler.py         # File I/O and validation functions
    ├── data_processor.py       # Analytics and processing functions
    └── api_handler.py          # API integration functions
```

---

## 🚀 Setup

### Prerequisites
- Python 3.7 or higher
- Internet connection (for API integration)

### Installation

1. **Clone or download the project**
   ```bash
   cd sales-analytics-system
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

   Or if using virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. **Verify installation**
   ```bash
   python -c "import pandas, requests; print('All dependencies installed!')"
   ```

---

## 💻 Usage

### Quick Start - Run Everything
```bash
python main.py
```

This single command will:
1. ✅ Clean and validate your sales data
2. ✅ Perform all analytics calculations
3. ✅ Fetch and integrate API product data
4. ✅ Generate comprehensive report

### Optional - Test API Integration Only
```bash
python test_task31.py
```

---

## 🔧 System Components

### 1. Data Cleaning (`file_handler.py`)

**Invalid Records Removal Criteria:**
- Missing CustomerID or Region
- Quantity ≤ 0
- UnitPrice ≤ 0
- TransactionID not starting with 'T'

**Data Cleaning Operations:**
- Remove commas from ProductName (e.g., "Mouse,Wireless" → "Mouse Wireless")
- Remove commas from numeric values (e.g., "1,500" → "1500")
- Skip empty lines
- Handle various text encodings (UTF-8, Latin-1, etc.)

### 2. Analytics Functions (`data_processor.py`)

#### Task 2.1: Sales Summary
- **`calculate_total_revenue()`**: Sum of all transaction amounts
- **`region_wise_sales()`**: Regional breakdown with percentages
- **`top_selling_products()`**: Best performers by quantity
- **`customer_analysis()`**: Customer spending patterns

#### Task 2.2: Date-based Analysis
- **`daily_sales_trend()`**: Daily revenue, transactions, unique customers
- **`find_peak_sales_day()`**: Highest revenue day identification

#### Task 2.3: Product Performance
- **`low_performing_products()`**: Items below quantity threshold

#### Task 4.1: Report Generation
- **`generate_sales_report()`**: Creates comprehensive formatted report

### 3. API Integration (`api_handler.py`)

#### Task 3.1: Product Data Fetching
- **`fetch_all_products()`**: Retrieves product catalog from API
- **`create_product_mapping()`**: Maps product IDs to details
- **`get_product_by_id()`**: Fetches single product
- **`search_products()`**: Search by query string

#### Task 3.2: Data Enrichment
- **`enrich_sales_data()`**: Adds API data to transactions
- **`save_enriched_data()`**: Exports enriched dataset
- **`print_enrichment_summary()`**: Reports enrichment statistics

---

## 📤 Output Files

### Primary Outputs

#### 1. `output/sales_report.txt` ⭐
**The main comprehensive report containing:**
- Executive summary (revenue, transactions, averages)
- Region-wise performance table
- Top 5 products ranking
- Top 5 customers ranking
- Daily sales trend analysis
- Product performance insights
- API enrichment summary

#### 2. `output/sales_data_cleaned.txt`
- All valid records after cleaning
- Original format with cleaned values
- Ready for further analysis

#### 3. `data/enriched_sales_data.txt`
- Cleaned data + API information
- Additional columns: API_Category, API_Brand, API_Rating, API_Match
- Combines internal and external data

### Supporting Outputs

#### 4. `output/invalid_records.txt`
- Records removed during cleaning
- Useful for audit and quality control

#### 5. `output/enriched_sales_data.txt`
- Copy of enriched data in output folder
- Convenient for review

---

## 🔄 Data Flow

```
┌─────────────────────────────────────────────────────────────────┐
│                    INPUT: sales_data.txt                         │
│                   (Raw, uncleaned data)                          │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                  PART 1: DATA CLEANING                           │
│  • Remove invalid records (quantity ≤ 0, missing fields, etc.)   │
│  • Clean formatting (commas in numbers, product names)           │
│  • Validate data integrity                                       │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│              OUTPUT: sales_data_cleaned.txt                      │
│                    (70 valid records)                            │
└────────────────────────────┬────────────────────────────────────┘
                             │
                    ┌────────┴────────┐
                    │                 │
                    ▼                 ▼
    ┌───────────────────────┐  ┌──────────────────────┐
    │  PART 2: ANALYTICS    │  │  PART 3: API         │
    │  • Revenue analysis   │  │  • Fetch products    │
    │  • Regional breakdown │  │  • Enrich data       │
    │  • Top products       │  │  • Match records     │
    │  • Customer insights  │  │                      │
    │  • Daily trends       │  │                      │
    └───────────┬───────────┘  └──────────┬───────────┘
                │                         │
                │                         ▼
                │          ┌──────────────────────────┐
                │          │ enriched_sales_data.txt  │
                │          │ (with API categories,    │
                │          │  brands, ratings)        │
                │          └──────────┬───────────────┘
                │                     │
                └──────────┬──────────┘
                           │
                           ▼
            ┌──────────────────────────────────┐
            │   PART 4: REPORT GENERATION      │
            │   • Combines all analytics       │
            │   • Formats professional report  │
            │   • Adds executive summary       │
            └──────────────┬───────────────────┘
                           │
                           ▼
            ┌──────────────────────────────────┐
            │    OUTPUT: sales_report.txt      │
            │   (Comprehensive final report)   │
            └──────────────────────────────────┘
```

---

## 📊 Sample Report Sections

### 1. Overall Summary
```
Total Revenue: $1,545,678.90
Total Transactions: 70
Average Order Value: $22,081.13
Date Range: 2024-12-01 to 2024-12-29
```

### 2. Region-wise Performance
```
Region         Sales Amount        Percentage     Trans Count    
----------------------------------------------------------------------
North          $   450,123.50          29.12%             18
South          $   380,456.20          24.61%             20
East           $   415,789.10          26.90%             17
West           $   299,310.10          19.37%             15
```

### 3. Top Products
```
Rank    Product Name                  Qty Sold       Revenue          
----------------------------------------------------------------------
1       Laptop                        45             $2,250,000.00
2       iPhone                        38             $20,862.00
```

---

## 🛠️ Troubleshooting

### Common Issues

**Issue**: `ModuleNotFoundError: No module named 'requests'`
- **Solution**: Run `pip install -r requirements.txt`

**Issue**: `FileNotFoundError: [Errno 2] No such file or directory: 'data/sales_data.txt'`
- **Solution**: Ensure `sales_data.txt` is in the `data/` folder

**Issue**: API enrichment shows 0% success rate
- **Solution**: Check internet connection, or ProductIDs might be outside API range (1-100)

**Issue**: UnicodeDecodeError when reading files
- **Solution**: System handles this automatically, but ensure file is not corrupted

---

## 📈 Performance Notes

- **Processing Time**: ~2-5 seconds for typical datasets (100-1000 records)
- **API Calls**: ~2-3 seconds for fetching 100 products
- **Memory Usage**: Minimal, suitable for datasets up to 100,000 records

---

## 🎓 Learning Outcomes

This project demonstrates:
- ✅ File I/O operations with encoding handling
- ✅ Data cleaning and validation techniques
- ✅ Dictionary and list comprehensions
- ✅ API integration and error handling
- ✅ Data aggregation and analysis
- ✅ Report generation and formatting
- ✅ Modular code organization
- ✅ Professional documentation

---



