#   Vedika Finance Power BI Dashboard – Customer & Loan Analytics

This project is a complete Power BI dashboard that visualizes and analyzes customer and loan data for Vedika Credit Capital Ltd, a microfinance NBFC.

---

##   Dashboard Objectives

- Track loan disbursal, EMI performance, and overdue trends
- Visualize borrower demographics and credit health
- Monitor branch and loan officer performance
- Understand repayment behavior, loyalty, and risk

---

##   Data Model Overview

- **Customer Info:** Customer ID, Name, Gender, State, City, DOB, Contact, KYC
- **Loan Info:** Loan ID, Loan Type, Purpose, Amount, Disbursal/Maturity Date, EMI, Status
- **Credit Scores:** CIBIL, Experian, Equifax, Loan-to-Income & DTI ratios
- **Payment Data:** EMI Due Date, Latest Payment Date, Overdue, Late Fee, Prepayment
- **Ops & Compliance:** Sanction Letter, Insurance, Audit Flag, Fraud Flag, Complaint Status

**
 Smart Visual Setup Tips**
For date visuals, avoid hierarchy: use flat Month-Year formats.
For maps, categorize location columns under Column Tools (State = “State or Province”).
For gauge, use AVERAGE instead of SUM on score fields.
Use slicers for Branch, State, City, Loan Officer, and Loan Type.

**Tools Used**
Microsoft Power BI Desktop
DAX for custom calculations
Microsoft Bing Maps (default map visual)
Manual data cleaning in Power Query

**Use Case**
This dashboard is designed for internal business intelligence teams, regional managers, and finance leadership of Vedika Credit Capital Ltd to:
Improve collection and cross-sell strategy
Monitor credit risk in real time
Optimize loan officer and branch performance
Enhance investor reporting and RBI compliance


---

## 📊 Visual Components

### 🔹 KPI Cards
- Total Loans
- Total Outstanding Amount
- Total Customers
- Average CIBIL Score
- Overdue %

### 🔹 Main Charts
- **Bar Chart:** Loan Type vs Total Loan Amount
- **Stacked Column Chart:** EMI Status by Month/Quarter
- **Pie Chart:** Gender Distribution
- **Map:** Loan Amount by State
- **Line Chart:** Monthly Disbursal Trend
- **Gauge:** Avg. Customer Loyalty Score
- **Matrix Table:** Customer Name | Loan ID | EMI | Overdue | Days Overdue

---

## 🧠 Key DAX Measures

```DAX
Total Loan Amount = SUM('VedikaFinanceData'[Loan Amount])

Total Outstanding = SUM('VedikaFinanceData'[Total Outstanding Amount])

Total Customers = DISTINCTCOUNT('VedikaFinanceData'[Customer ID])

Average CIBIL = AVERAGE('VedikaFinanceData'[CIBIL Score])

Overdue % = 
DIVIDE(
    COUNTROWS(FILTER('VedikaFinanceData', 'VedikaFinanceData'[Days Overdue] > 0)),
    COUNT('VedikaFinanceData'[Loan ID]),
    0
)






