### Variables and Ratios from `uscecchini28` accounting fraud dataset

Based on the `yfinance` balance-sheet, income-statement and cash-flow data, here is a description of the variables and ratios that is obtained or calculated, along with their source financial statement.

***

### Raw Accounting Variables

These are the fundamental financial data points that can be extracted directly from a company's financial statements.

* **`fyear`**: The fiscal year of the financial statement.
    * **Source**: All statements (Balance Sheet, Income Statement, Cash Flow).

* **`at` (Total Assets)**: The total value of a company's assets.
    * **Source**: Balance Sheet.

* **`ap` (Accounts Payable)**: The amount of money a company owes to its suppliers and creditors.
    * **Source**: Balance Sheet.

* **`ceq` (Common Stock Equity)**: The total value of the company's equity belonging to common shareholders.
    * **Source**: Balance Sheet.

* **`che` (Cash and Cash Equivalents)**: The amount of cash and highly liquid assets the company has on hand.
    * **Source**: Balance Sheet.

* **`csho` (Common Shares Outstanding)**: The total number of shares of a company's stock that are held by its shareholders.
    * **Source**: Balance Sheet.

* **`dltt` (Long-Term Debt)**: The total amount of a company's long-term debt.
    * **Source**: Balance Sheet.

* **`dp` (Depreciation)**: A non-cash expense that reflects the decrease in value of a company's assets over time.
    * **Source**: Income Statement.

* **`ni` (Net Income)**: The company's total earnings after all expenses have been subtracted from total revenue.
    * **Source**: Income Statement.

* **`ppegt` (Gross Property, Plant, and Equipment)**: The original cost of a company's fixed assets before depreciation.
    * **Source**: Balance Sheet.

* **`pstk` (Preferred Stock)**: The value of a company's preferred stock.
    * **Source**: Balance Sheet.

* **`re` (Retained Earnings)**: The portion of net income that is not paid out as dividends.
    * **Source**: Balance Sheet.

* **`rect` (Accounts Receivable)**: The amount of money owed to the company by its customers for goods or services.
    * **Source**: Balance Sheet.

* **`sale` (Total Revenue)**: The total amount of money generated from the sale of goods or services.
    * **Source**: Income Statement.

* **`lt` (Total Liabilities)**: The total amount of a company's financial obligations.
    * **Source**: Balance Sheet.

* **`xint` (Interest Expense)**: The cost incurred by an entity for borrowed funds.
    * **Source**: Income Statement.

* **`ivao` (Investments and Advances)**: The value of a company's investments in other entities.
    * **Source**: Balance Sheet.

* **`dltis` (Long-Term Debt Issuance)**: Cash received from issuing new long-term debt.
    * **Source**: Cash Flow Statement.

* **`sstk` (Sale of Common and Preferred Stock)**: Cash received from issuing new shares of stock.
    * **Source**: Cash Flow Statement.

***

### Calculated Financial Ratios

These ratios are derived from the raw accounting variables and are key indicators used in fraud detection models.

* **`ch_rsst` (Change in Revenue and Receivable)**
    * **Formula**: `(sale_t - rect_t) / (sale_{t-1} - rect_{t-1})`
    * **Source**: Income Statement, Balance Sheet.

* **`dch_rec` (Change in Receivables)**
    * **Formula**: `(rect_t - rect_{t-1}) / at_{t-1}`
    * **Source**: Balance Sheet.

* **`ch_cs` (Change in Common Stock)**
    * **Formula**: `(csho_t - csho_{t-1}) / csho_{t-1}`
    * **Source**: Balance Sheet.

* **`ch_cm` (Change in Cash and Marketable Securities)**
    * **Formula**: `(che_t - che_{t-1}) / at_t`
    * **Source**: Balance Sheet.

* **`ch_roa` (Change in Return on Assets)**
    * **Formula**: `(ni_t / at_t) - (ni_{t-1} / at_{t-1})`
    * **Source**: Income Statement, Balance Sheet.

* **`dpi` (Change in Gross Property, Plant, and Equipment)**
    * **Formula**: `(ppegt_t - ppegt_{t-1}) / ppegt_{t-1}`
    * **Source**: Balance Sheet.

* **`reoa` (Retained Earnings to Assets)**
    * **Formula**: `re_t / at_t`
    * **Source**: Balance Sheet.

* **`issue` (Change in Shares Issued)**
    * **Formula**: `sstk_t / at_t`
    * **Source**: Cash Flow Statement, Balance Sheet.

* **`ch_fcf` (Change in Free Cash Flow)**
    * **Formula**: `(fcf_t - fcf_{t-1}) / at_t`
    * **Source**: Cash Flow Statement, Balance Sheet.