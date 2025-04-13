# Bank-Loan-Report

Just wrapped up this Bank Loan Report Dashboard in Power BI and thought I’d share a few insights 📊

I started by building a Star Schema data model to keep everything clean and scalable—fact and dimension tables made the analysis smoother and more insightful.

Analyzed over 38K loan applications, with $435M funded and $473M received.

🔹 86% Good Loans (fully funded & repaid)
🔸 14% Bad Loans — worth deeper risk analysis
💰 Avg Interest Rate: 12% | Avg DTI: 13%

📈 Month-over-month growth:

+6.9% applications

+13% funding

+16% received amount

📍 Top applying states: CA, NY, FL, TX
🔁 Top loan purpose: Debt Consolidation (~50%)
👨‍💼 Most applicants had either <1 year or 10+ years of work experience

Really enjoyed working on this—it brought together finance, analytics, and storytelling in one place.

Open to feedback or ideas—always learning!
// =====================
// # KPI Measures
// =====================

AVG DTI = 
AVERAGE('Fact _Loan'[dti])

AVG Interest Rate = 
AVERAGE('Fact _Loan'[int_rate])

Total Loan Applications = 
COUNT('Fact _Loan'[id])

Total Funded Amount = 
SUM('Fact _Loan'[loan_amount])

Total Amount Received = 
SUM('Fact _Loan'[total_payment])

// =====================
// # Good vs Bad Loan Metrics
// =====================

Bad Loan Applications = 
CALCULATE([Total Loan Applications], 'Fact _Loan'[Good vs Bad Loans] = "Bad Loan")

Bad Loan Funded Amount = 
CALCULATE([Total Funded Amount], 'Fact _Loan'[Good vs Bad Loans] = "Bad Loan")

Bad Loan Received Amount = 
CALCULATE([Total Amount Received], 'Fact _Loan'[Good vs Bad Loans] = "Bad Loan")

Bad Loan % = 
DIVIDE([Bad Loan Applications], [Total Loan Applications])

Good Loan Applications = 
CALCULATE([Total Loan Applications], 'Fact _Loan'[Good vs Bad Loans] = "Good Loan")

Good Loan Funded Amount = 
CALCULATE([Total Funded Amount], 'Fact _Loan'[Good vs Bad Loans] = "Good Loan")

Good Loan Received Amount = 
CALCULATE([Total Amount Received], 'Fact _Loan'[Good vs Bad Loans] = "Good Loan")

Good Loan % = 
DIVIDE([Good Loan Applications], [Total Loan Applications])

// =====================
// # Month-over-Month Metrics
// =====================

MoM AVG DTI = 
DIVIDE([MTD Avg DTI] - [PMTD AVG DTI], [PMTD AVG DTI])

MoM Avg Interest Rate = 
DIVIDE([MTD Avg Int Rate] - [PMTD Avg Int Rate], [PMTD Avg Int Rate])

MoM Loan Applications = 
DIVIDE([MTD Loan Application] - [PMTD Loan Application], [PMTD Loan Application])

MoM Total Amount Received = 
DIVIDE([MTD Received Amount] - [PMTD Total Amount Received], [PMTD Total Amount Received])

MoM Total Funded Amount = 
DIVIDE([MTD Funded Amount] - [PMTD Total Funded Amount], [PMTD Total Funded Amount])

// =====================
// # MTD Metrics
// =====================

MTD Avg DTI = 
CALCULATE([AVG DTI], TOTALMTD('Date Table'[Date]))

MTD Avg Int Rate = 
CALCULATE([AVG Interest Rate], TOTALMTD('Date Table'[Date]))

MTD Funded Amount = 
CALCULATE([Total Funded Amount], TOTALMTD('Date Table'[Date]))

MTD Loan Application = 
CALCULATE([Total Loan Applications], TOTALMTD('Date Table'[Date]))

MTD Received Amount = 
CALCULATE([Total Amount Received], TOTALMTD('Date Table'[Date]))

// =====================
// # PMTD Metrics
// =====================

PMTD AVG DTI = 
CALCULATE([AVG DTI], DATESMTD(DATEADD('Date Table'[Date], -1, MONTH)))

PMTD Avg Int Rate = 
CALCULATE([AVG Interest Rate], DATESMTD(DATEADD('Date Table'[Date], -1, MONTH)))

PMTD Loan Application = 
CALCULATE([Total Loan Applications], DATESMTD(DATEADD('Date Table'[Date], -1, MONTH)))

PMTD Total Amount Received = 
CALCULATE([Total Amount Received], DATESMTD(DATEADD('Date Table'[Date], -1, MONTH)))

PMTD Total Funded Amount = 
CALCULATE([Total Funded Amount], DATESMTD(DATEADD('Date Table'[Date], -1, MONTH)))


#PowerBI #DataAnalytics #Finance #LoanAnalysis #DashboardDesign #DataStorytelling #StarSchema #DataModeling #MohamedElsaadi

![Image](https://github.com/user-attachments/assets/5c4eb96e-3fba-4398-b6ba-3354da4e8df8)

![Image](https://github.com/user-attachments/assets/dda7b331-dfeb-4627-a484-b613e9c69bed)

![Image](https://github.com/user-attachments/assets/f90cb9b5-8b68-413c-9ad8-036ef421f17f)

![Image](https://github.com/user-attachments/assets/4d979bc9-592c-4eeb-95fc-429d93bfbfe6)
