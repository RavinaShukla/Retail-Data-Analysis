 # RetailPulse – Retail Data Analytics & ETL Pipeline

RetailPulse is a retail data analytics project developed as part of the Zidio project. It processes large-scale retail transaction data, cleans sales records, creates customer RFM features, and generates summary datasets for business analytics and dashboard development.

## Project Objectives

- Process millions of retail sales records using Python and Pandas.
- Clean sales transaction data.
- Create masked customer ID fields.
- Generate daily sales summaries by store.
- Calculate customer Recency, Frequency, and Monetary (RFM) features.
- Combine inventory snapshots with SKU master data.
- Prepare summary datasets for analytics and visualization.

## Technology Stack

- Python
- Pandas
- CSV data processing
- Git and GitHub

## Project Structure

```text
retailpulse-zidio/
├── data/
│   ├── sales_transactions.csv
│   ├── customer_master.csv
│   ├── sku_master.csv
│   ├── store_master.csv
│   ├── promotions.csv
│   ├── inventory_snapshot.csv
│   ├── cleaned/
│   │   └── cleaned_sales.csv
│   └── demo/
│       ├── daily_sales_summary.csv
│       ├── customer_rfm.csv
│       └── inventory_summary.csv
├── src/
│   └── etl.py
├── .gitignore
├── requirements.txt
└── README.md
```

## ETL Workflow

### 1. Data Loading
Loads six datasets: sales transactions, customers, SKU master, stores, promotions, and inventory snapshots.

### 2. Data Cleaning
- Converts sales dates into datetime format.
- Filters out rows with non-positive quantities.
- Removes rows with negative unit prices.
- Replaces missing promotion IDs with `NO_PROMO`.

### 3. Customer ID Masking
Creates a `customer_id_masked` field using the last four characters of the customer ID. The original customer ID remains in the output, so this is masking rather than complete anonymization.

### 4. Daily Sales Summary
Groups sales by date and store, calculating total revenue, total quantity, and unique receipt counts.

Output: `data/demo/daily_sales_summary.csv`

### 5. Customer RFM Analysis
Calculates:
- **Recency:** Days since the customer's latest purchase relative to the maximum transaction date in the processed data.
- **Frequency:** Number of unique receipts.
- **Monetary:** Sum of transaction values.

Output: `data/demo/customer_rfm.csv`

### 6. Inventory Summary
Merges inventory snapshots with SKU master data using `sku_id`.

Output: `data/demo/inventory_summary.csv`

## Setup and Execution

### Prerequisites
- Python 3.10 or later
- pip

### 1. Clone the Repository

```bash
git clone https://github.com/dipeshgunjal62940-svg/retailpulse-zidio.git
cd retailpulse-zidio
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

Activate it in Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

If needed, install Pandas directly:

```bash
pip install pandas
```

### 4. Add Input Datasets

Place these six CSV files in the `data/` directory:

- `sales_transactions.csv`
- `customer_master.csv`
- `sku_master.csv`
- `store_master.csv`
- `promotions.csv`
- `inventory_snapshot.csv`

Large source datasets are kept locally and are not included in the repository.

### 5. Run the ETL Pipeline

Run this command from the repository root:

```bash
python src/etl.py
```

The script generates the cleaned sales dataset and three demo summary CSV files.

## Generated Outputs

| File | Description |
|---|---|
| `cleaned_sales.csv` | Processed sales transactions |
| `daily_sales_summary.csv` | Daily sales metrics by store |
| `customer_rfm.csv` | Customer-level RFM features |
| `inventory_summary.csv` | Inventory enriched with SKU information |

## My Contribution

**Role: Data & ETL**

- Developed and executed the ETL pipeline.
- Processed approximately 10 million sales records.
- Implemented sales data cleaning and customer ID masking.
- Generated daily sales, RFM, and inventory summary datasets.
- Prepared data outputs for downstream analytics and dashboards.

## Future Improvements

- Add automated data-quality checks.
- Strengthen customer data privacy.
- Improve logging and error handling.
- Integrate outputs with a business intelligence dashboard.

## Project Information

**Project:** Zidio Data Analytics & ETL  
**Repository:** https://github.com/dipeshgunjal62940-svg/retailpulse-zidio

