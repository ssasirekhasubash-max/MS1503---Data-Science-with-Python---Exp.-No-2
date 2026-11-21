# Experiment 2 : Customer Data Exploration Using Pandas

## Aim
To create a sample customer dataset and perform data exploration, filtering, sorting, grouping, and basic statistical analytics using Pandas functions in Python.

## Algorithm

1. **Start** the program.
2. **Import Library**: Import the `pandas` library as `pd` for tabular data manipulation and analysis.
3. **Initialize Dataset**: Create a Python dictionary `data` containing customer attributes (`Customer_ID`, `Customer_Name`, `Region`, `Age`, `Annual_Income`, `Spending_Score`, `Loyalty_Years`).
4. **Construct DataFrame**: Convert the dictionary into a structured Pandas DataFrame `df` using `pd.DataFrame(data)` and print the dataset.
5. **Inspect Structure & Summary**:
   * Display dataset dimensions (`df.shape`), column names (`df.columns`), data types and null counts (`df.info()`), and descriptive statistics (`df.describe()`).
   * Display the first 3 records (`df.head(3)`) and last 3 records (`df.tail(3)`).
6. **Sort & Filter Records**:
   * Sort customers in descending order of `Annual_Income` using `df.sort_values()`.
   * Filter high-income customers where `Annual_Income > 70000`.
7. **Perform Group-Wise & Frequency Analysis**:
   * Group customers by `Region` and calculate regional averages for `Annual_Income` and `Spending_Score` using `df.groupby().mean()`.
   * Count customer distribution across each region using `df["Region"].value_counts()`.
8. **Compute Overall Metrics & Top Performer**:
   * Identify the customer record with the highest `Spending_Score` using `df["Spending_Score"].idxmax()` and `df.loc[]`.
   * Calculate overall mean `Annual_Income` and mean `Spending_Score`.
9. **Stop** the program.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Data Creation** | `pd.DataFrame()` | Converts a Python dictionary into a 2D labeled tabular DataFrame |
| **Structural Inspection** | `df.shape`, `df.columns` | Retrieves dimensions `(rows, columns)` and column labels |
| | `df.info()`, `df.describe()` | Summarizes column data types, memory usage, and descriptive statistics |
| | `df.head(n)`, `df.tail(n)` | Views the first `n` and last `n` rows of the dataset |
| **Sorting & Filtering** | `df.sort_values()` | Orders records by `Annual_Income` in descending order |
| | Boolean Indexing (`df[...]`) | Filters customers with `Annual_Income > 70000` |
| **Grouping & Aggregation** | `df.groupby().mean()` | Aggregates mean income and spending score per `Region` |
| | `df["Region"].value_counts()` | Counts occurrences of customers in each region |
| | `idxmax()`, `df.loc[]`, `.mean()` | Locates the top spender row and computes dataset-wide averages |

## Program
    # Customer Data Exploration using Pandas
    import pandas as pd
    
    # Step 1: Create a sample customer dataset
    data = {
        "Customer_ID": [101, 102, 103, 104, 105, 106, 107, 108],
        "Customer_Name": [
            "Aarav Sharma",
            "Diya Nair",
            "Rohan Verma",
            "Meera Krishnan",
            "Kabir Menon",
            "Ananya Iyer",
            "Vikram Rao",
            "Sneha Das",
        ],
        "Region": [
            "South",
            "South",
            "North",
            "South",
            "West",
            "East",
            "North",
            "West",
        ],
        "Age": [28, 34, 45, 24, 39, 31, 52, 27],
        "Annual_Income": [65000, 82000, 95000, 54000, 76000, 61000, 110000, 72000],
        "Spending_Score": [78, 85, 62, 91, 74, 68, 58, 88],
        "Loyalty_Years": [2, 5, 8, 1, 4, 3, 10, 3],
    }
    
    # Step 2: Convert to a Pandas DataFrame
    df = pd.DataFrame(data)
    print("=== Customer Dataset ===")
    print(df)
    print()
    
    # Step 3: Basic exploration
    print("=== Shape & Columns ===")
    print("Shape (rows, columns):", df.shape)
    print("Columns:", list(df.columns))
    print()
    
    print("=== DataFrame Info ===")
    print(df.info())
    print()
    
    print("=== Descriptive Statistics ===")
    print(df.describe())
    print()
    
    # Step 4: Display first and last few records
    print("=== First 3 Records ===")
    print(df.head(3))
    print()
    
    print("=== Last 3 Records ===")
    print(df.tail(3))
    print()
    
    # Step 5: Sort customers by Annual Income (descending)
    sorted_df = df.sort_values(by="Annual_Income", ascending=False)
    print("=== Customers Sorted by Annual Income (Descending) ===")
    print(sorted_df)
    print()
    
    # Step 6: Filter high-income customers (Income > 70000)
    high_income_df = df[df["Annual_Income"] > 70000]
    print("=== High-Income Customers (Annual_Income > 70000) ===")
    print(high_income_df)
    print()
    
    # Step 7: Group customers by Region and find average Income and Spending Score
    regional_avg = df.groupby("Region")[["Annual_Income", "Spending_Score"]].mean()
    print("=== Regional Averages (Annual_Income & Spending_Score) ===")
    print(regional_avg)
    print()
    
    # Step 8: Count number of customers in each Region
    region_counts = df["Region"].value_counts()
    print("=== Customer Count by Region ===")
    print(region_counts)
    print()
    
    # Step 9: Identify customer with maximum Spending Score
    top_spender_idx = df["Spending_Score"].idxmax()
    top_spender = df.loc[top_spender_idx]
    print("=== Customer with Highest Spending Score ===")
    print(top_spender)
    print()
    
    # Step 10: Compute overall averages
    overall_avg_income = df["Annual_Income"].mean()
    overall_avg_spending = df["Spending_Score"].mean()
    print("=== Overall Averages ===")
    print(f"Overall Mean Annual Income: {overall_avg_income:.2f}")
    print(f"Overall Mean Spending Score: {overall_avg_spending:.2f}")


## Output
<img width="775" height="240" alt="image" src="https://github.com/user-attachments/assets/91960564-1b56-4742-bec5-63678126aa74" />
<img width="1118" height="307" alt="image" src="https://github.com/user-attachments/assets/0dec77b9-215c-4a7b-a08d-100dc922aafe" />
<img width="448" height="385" alt="image" src="https://github.com/user-attachments/assets/821be23a-b8e0-446e-b3a6-ed7b617555b1" />
<img width="807" height="238" alt="image" src="https://github.com/user-attachments/assets/b9b3272d-b335-455d-a45f-9e32d39c0eb3" />
<img width="762" height="242" alt="image" src="https://github.com/user-attachments/assets/63cdde28-f747-4db8-9fb2-c0e64d1fc959" />
<img width="737" height="240" alt="image" src="https://github.com/user-attachments/assets/e7fb26b6-79e0-4d22-9bc2-0cc33da2e4dc" />
<img width="847" height="432" alt="image" src="https://github.com/user-attachments/assets/22b1ea95-930f-4ec1-b2e2-4c70f42c6f00" />
<img width="863" height="325" alt="image" src="https://github.com/user-attachments/assets/9ca6ad62-e1c2-4089-8098-5ef87ab339fa" />
<img width="678" height="356" alt="image" src="https://github.com/user-attachments/assets/e26a78e9-ff05-4582-9537-6b3016b25652" />
<img width="477" height="315" alt="image" src="https://github.com/user-attachments/assets/c8684370-d0b9-45d4-bb22-9e81ae7dd77d" />
## Result
The program successfully creates a customer dataset using Pandas and performs exploratory analysis, sorting, filtering, regional grouping, and summary statistics.
