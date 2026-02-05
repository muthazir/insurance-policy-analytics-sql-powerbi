# PRISM-Insurance-Policy-Analytics-Report

Power BI insurance analytics report built using SQL Server integration, DAX-driven lifecycle logic, demographic segmentation, and automated scheduled refresh for real-time portfolio monitoring.

---

## 📊 Report Preview

### Portfolio & Claims Overview

<img width="644" height="362" alt="Image" src="https://github.com/user-attachments/assets/52945603-5fd9-41c7-8261-4f7830807d89" />

---

## Problem Statement

This report helps Prism Insurance Pvt. Ltd. analyze policy performance, claims distribution, demographic segmentation, and policy lifecycle status using real-time data from SQL Server.

The report architecture is designed to support scalable policy and claim analysis while ensuring reliable and efficient data refresh from SQL Server.

The objective of this analysis is to:

- Monitor total Premium, Coverage, and Claim exposure.
- Classify policies into Active and Inactive categories.
- Analyze claim status distribution (Rejected, Settled, Pending).
- Evaluate premium contribution by Policy Type.
- Assess claim amount trends across Age Groups.
- Provide detailed transaction-level visibility.
- Enable automatic report updates through scheduled refresh.

By identifying policy lifecycle distribution and claim behavior patterns, the organization can improve underwriting decisions, risk monitoring, and renewal strategies.

---

### Steps followed 

- Step 1 : Connected Power BI Desktop directly to SQL Server database to import insurance dataset.

- Step 2 : Opened Power Query Editor and enabled:
  - Column Distribution
  - Column Quality
  - Column Profile

- Step 3 : Selected "Column profiling based on entire dataset" to validate complete data.

- Step 4 : Verified data types for:
  - PolicyNumber
  - CustomerID
  - Age
  - CoverageAmount
  - PremiumAmount
  - ClaimAmount
  - PolicyStartDate
  - PolicyEndDate
  - ClaimDate

- Step 5 : Created calculated column to segment customers into Age Groups.

        Age Group =
        IF(InsuranceData[Age] <= 30, "Young Adults",
        IF(InsuranceData[Age] <= 60, "Adult",
        "Elder"))

This allows demographic-level risk and claim analysis.

- Step 6 : Created calculated column to classify policies based on lifecycle.

        Policy Status =
        IF(InsuranceData[PolicyEndDate] >= TODAY(), "Active", "Inactive")

This dynamically evaluates policy validity.

- Step 7 : Created key measures:

        Total Premium = SUM(InsuranceData[PremiumAmount])
        Total Coverage = SUM(InsuranceData[CoverageAmount])
        Total Claims = SUM(InsuranceData[ClaimAmount])
        Total Policies = COUNT(InsuranceData[PolicyNumber])

- Step 8 : Built Page 1 – Portfolio & Claims Overview:
  - Premium Amount KPI (5.97M)
  - Coverage Amount KPI (600.33M)
  - Claim Amount KPI (16.90M)
  - Premium by Policy Type (Travel, Health, Auto, Life, Home)
  - Active vs Inactive Policy Distribution
  - Claims by Status (Rejected, Settled, Pending)
  - Claim Amount by Age Group
  - Detailed Claim Breakdown Table

- Step 9 : Built Page 2 – Transaction-Level View:
  - Full dataset visibility
  - Policy-level details
  - Claim status tracking
  - Dynamic filtering by PolicyNumber, CustomerID, and ClaimNumber

- Step 10 : Applied professional dark theme formatting for executive presentation.

- Step 11 : Published report to Power BI Service.

- Step 12 : Configured Scheduled Refresh to ensure that new records inserted into SQL Server automatically update the report.

### Scheduled Refresh Configuration (Power BI Service)

<img width="426" height="240" alt="Image" src="https://github.com/user-attachments/assets/02731dad-ac04-4484-931b-8e01f51b79df" />

---

## Snapshot of Report (Power BI Service)

<img width="646" height="364" alt="Image" src="https://github.com/user-attachments/assets/01de5398-661b-4bd0-995c-4759495cb021" />

---

## Insights

A two-page interactive report was created and deployed to Power BI Service with automatic refresh enabled.

Following inferences can be drawn from the report:

### [1] Portfolio Exposure

- Total Premium Amount: 5.97M
- Total Coverage Exposure: 600.33M
- Total Claim Amount: 16.90M

The coverage-to-premium ratio (~100:1) indicates substantial insured exposure relative to premium collected, highlighting the importance of accurate risk assessment and effective claim management.

---

### [2] Policy Lifecycle Status

- Active Policies: 5.81K (58.11%)
- Inactive Policies: 4.19K (41.89%)

A substantial inactive proportion highlights potential renewal opportunities and retention focus areas.

---

### [3] Claim Status Distribution

- Rejected Claims: 4.4K
- Settled Claims: 3.4K
- Pending Claims: 2.3K

The high rejection volume relative to settled claims may indicate strict underwriting policies, documentation gaps, or operational inefficiencies in claim processing, warranting deeper analysis.

---

### [4] Premium Distribution by Policy Type

Travel policies contribute the highest premium share (2.5M), followed by Health and Auto.

This suggests travel insurance as a dominant revenue segment.

---

### [5] Claim Amount by Age Group

- Adults: 8.8M
- Elders: 6.4M
- Young Adults: 1.7M

Claim severity increases with age group, indicating potential risk concentration in older demographics.

---

### [6] Real-Time Reporting Capability

Since the dataset is sourced from SQL Server with scheduled refresh:

- Reports reflect newly inserted policy and claim records.
- Manual refresh dependency is eliminated.
- Business stakeholders access up-to-date portfolio metrics at all times.

---

## Technical Skills Demonstrated

- SQL Server data integration
- Data profiling and validation in Power Query
- DAX calculated columns and measures
- Dynamic policy lifecycle logic using TODAY()
- KPI design and portfolio exposure analysis
- Claims trend analysis
- Power BI Service deployment and scheduled refresh configuration

---

## Conclusion

This project demonstrates:

- Direct SQL Server integration with Power BI
- DAX-based business logic implementation
- Policy lifecycle classification using dynamic date logic
- Demographic risk segmentation
- Claims performance monitoring
- Real-time report automation via scheduled refresh
- Professional Power BI Service deployment

The report simulates a real-world insurance analytics solution focused on portfolio exposure monitoring, claim trend evaluation, and lifecycle management.
