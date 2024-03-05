
# Customer Churn Dashboard
![Customer churn](https://github.com/josephadebiyi91/PWC_Customer_Churn/assets/97675443/d806a990-cdb9-4434-bcfd-9a254aea35da)

#### Dashboard Link : https://app.powerbi.com/groups/ed07ede0-211d-47d2-b445-b83cdde82139/reports/d7ffca32-544d-440c-a7aa-eff522993571/ReportSection?experience=power-bi


## Problem Statement
This dashboard helps the Retention Manager understand their customers better. It helps the manager knows why customers are leaving. Through different ratings, they get to know their improvement area, & thus they can improve their services by identifying these area. It also lets them know the Pecentage Partner, Dependents, PhoneService, thus since by using this dashboard they have identified this problem, they can further work on factors responsible for these churn.

### Steps followed
- Step 1 : Load data into Power BI Desktop, dataset is a xls file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that in none of the columns errors & empty values were present in "TotalCharges" and replace as "0".
- Step 5 : Six cards were add to the visuals indicating the "# of Churn, # of SenCitizen, # of Admin tickets, # of Tech Ticket, Montly, Yearly".
- Step 6 : Pie chart are also use on the visuals to display "Internet Service, Techsupport, Online Security".
- Step 7 : A bar chart was also added to the report design area representing payment method, Tenure, and online backup. 
- Step 8 : Guage Visual was used to represent different ratings mentioned below,
(a) Partner in %

(b) Dependents in %

(c) Phone services in %

- Step 9 : Donut chart Visual was used to represent different ratings mentioned below,
(a) Contract

(b) Multiple Lines

- Step 10 : In the report view, under the insert tab, using shapes option from elements group a rectangle was inserted & similarly using image option company's logo was added to the report design area.
- Step 11 : Calculated column was created in which, customers were grouped into various Tenure rating.
for creating new column following DAX expression was written;

Tenure Rating =

if(tenure<=12, "< 1yrs",

if(tenure<=24, "< 2yrs",

if(tenure<=36, "< 3yrs",

if(tenure<=48, "< 4yrs",

if(tenure<=60, "< 5yrs",

"< 6yrs")))

Snap of new column created

![tenure rating column](https://github.com/josephadebiyi91/PWC_Customer_Churn/assets/97675443/5880190b-a3ea-45b1-b175-06fd783ad724)


- Step 12 : Calculated column was created in which, customers were grouped into two # Churn.
for creating new column following DAX expression was written;

#churn =

if(churn = "yes", "1",

"0")))

Snap of new column created

![Churn column](https://github.com/josephadebiyi91/PWC_Customer_Churn/assets/97675443/0335c104-d8de-4978-bced-46bbca400805)

- Step 13 : New measure was created to find % churn rate.
Following DAX expression was written for the same,

% Churn Rate = DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[Churn]),'01 Churn-Dataset'[Churn] = "Yes"),COUNT('01 Churn-Dataset'[Churn]),0)






- Step 14 : New measure was created to find Dependents in %,

Following DAX expression was written to find Dependents in %,

Dependents in % = DIVIDE(
    CALCULATE(COUNT('01 Churn-Dataset'[Dependents]),'01 Churn-Dataset'[Dependents] == "Yes", '01 Churn-Dataset'[Churn] == "Yes"),
    CALCULATE(COUNT('01 Churn-Dataset'[Dependents]),'01 Churn-Dataset'[Churn] == "Yes")
        
)

- Step 15 : New measure was created to find Month-to-Month,

Following DAX expression was written to find Month-to-Month,

Month-to-Month = CALCULATE(AVERAGEX('01 Churn-Dataset',CALCULATE(COUNT('01 Churn-Dataset'[Contract]),'01 Churn-Dataset'[Contract] == "month-to-month",'01 Churn-Dataset'[Churn] == "Yes")))

- Step 16 : New measure was created to calculate Monthly,

Following DAX expression was written to calculate Monthly,

Monthly = SUM('01 Churn-Dataset'[MonthlyCharges])


Snap of new kpi created


![monthly](https://github.com/josephadebiyi91/PWC_Customer_Churn/assets/97675443/683935d3-18d3-47e0-a3cf-f2f29720210e)


- Step 17 : New measure was created to calculate MultipleLines in %,

Following DAX expression was written to calculate MultipleLines in %,

MultipleLines in % = DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[MultipleLines]),'01 Churn-Dataset'[MultipleLines] == "Yes"),
CALCULATE(COUNT('01 Churn-Dataset'[MultipleLines]),'01 Churn-Dataset'[Churn] == "Yes"),0
)

- Step 18 : New measure was created to calculate numbAdminTicket,

Following DAX expression was written to calculate numbAdminTicket,

numbAdminTicket = SUM('01 Churn-Dataset'[numAdminTickets])

Snap of new kpi created

![adminTicket](https://github.com/josephadebiyi91/PWC_Customer_Churn/assets/97675443/47b4a9c6-aa05-4268-9db4-75a504d729ef)


- Step 19 : New measure was created to calculate numTechTicket,

Following DAX expression was written to calculate numTechTicket,

numTechTicket = CALCULATE(SUM('01 Churn-Dataset'[numTechTickets]),'01 Churn-Dataset'[Churn] == "Yes")

Snap of new kpi created

![TechTicket](https://github.com/josephadebiyi91/PWC_Customer_Churn/assets/97675443/9bfc7586-7f3f-4e67-a79d-40a28b200b51)


- Step 20 : New measure was created to calculate PaperlessBilling in %,

Following DAX expression was written to calculate PaperlessBilling in %,

PaperlessBilling in % = DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[PaperlessBilling]),'01 Churn-Dataset'[PaperlessBilling] == "Yes",'01 Churn-Dataset'[Churn] == "Yes"),
CALCULATE(COUNT('01 Churn-Dataset'[Churn]),'01 Churn-Dataset'[Churn] == "Yes"),0)

- Step 21 : New measure was created to calculate Partner in %,

Following DAX expression was written to calculate Partner in %,

Partner in % = DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[Partner]),'01 Churn-Dataset'[Partner] == "Yes",'01 Churn-Dataset'[Churn] == "Yes"),
CALCULATE(COUNT('01 Churn-Dataset'[Partner]),'01 Churn-Dataset'[Churn] == "Yes"),0)


- Step 22 : New measure was created to calculate PhoneService in %,

Following DAX expression was written to calculate PhoneService in %,

PhoneService in % = DIVIDE(CALCULATE(COUNT('01 Churn-Dataset'[PhoneService]),'01 Churn-Dataset'[PhoneService] == "Yes"),
CALCULATE(COUNT('01 Churn-Dataset'[PhoneService]),'01 Churn-Dataset'[Churn] == "Yes"),0
)

- Step 23 : New measure was created to calculate Yearly,

Following DAX expression was written to calculate Yearly,

Yearly = SUM('01 Churn-Dataset'[TotalCharges])

Snap of new kpi created

![yearly](https://github.com/josephadebiyi91/PWC_Customer_Churn/assets/97675443/5a8c9265-5b93-49ba-aca2-eb018e6dbf73)


A Slicer visual was used to represent gender (Male/ Female).  
 
- Step 24 : The report was then published to Power BI Service.
 

# Snapshot of Dashboard (Power BI Service)

![powerBI dashboard](https://github.com/josephadebiyi91/PWC_Customer_Churn/assets/97675443/25d20153-312f-438a-af11-bdd3c3b7d462)


 
 # Report Snapshot (Power BI DESKTOP)

 
![Customer churn](https://github.com/josephadebiyi91/PWC_Customer_Churn/assets/97675443/cc9ea0af-7ab0-4bc2-8b98-61d18577d39a)



# Insights
A single page report was created on Power BI Desktop & it was then published to Power BI Service.
Following inferences can be drawn from the dashboard;

### [1] Total Number of Churn = 1,869
Number of SenCitizen = 476
Number of AdminTickets = 885
Number of Tech Ticket = 2,173
Montly = $ 139,131
Yearly = $ 2,862,927

### [2] Pecentage Ratings
a) Partner = 36%
b) Dependents = 17%
c) PhoneService = 91%

while calculating Percentage rating, PhoneService has high rating.

These ratings will change if different visual filters will be applied.

### [3] Online Security

a) 1,461 (78.17%) of customer has No Online security.
b) 295 (15.78%) of customer has Internet service.
c) 113 (6.05%) of customer has No Internet service.

Online Security will change if different visual filters will be applied.


### [4] Internet Service

a) 1,297 (69.4%) of customer has Fiber Optic.
b) 459 (24.56%) of customer has DSL.
c) 113 (6.05%) of customer has No Internet service.

Online Security will change if different visual filters will be applied.


### [5] Contract

a) 1,655 (89%) of customer is Month-to-month contract.
b) 166 (9%) of customer is One year contract.
c) 48 (3%) of customer is Two year contract.

Online Security will change if different visual filters will be applied.

### [6] Techsupport

a) 1,446 (77%) of customer has no Techsupport.
b) 310 (17%) of customer has TechTicket.
c) 113 (6%) of customer has no internet service.

Online Security will change if different visual filters will be applied.

### [7] MultipleLines

a) 850 (45.48%) of customer has Multiple Lines.
b) 849 (45.43%) of customer has no Multiple Lines.
c) 170 (9.1%) of customer has no phone service.

Online Security will change if different visual filters will be applied.

### [8] Some other insights

### payment Method

1.1) 45 % customers uses Electronic check.

1.2) 19 % customers travelled by Mailed Check.

1.3) 17 % customers travelled by Bank Transfer(Automatic).

1.4) 15 % customers travelled by Credit Card(Automatic).

thus, maximum customers uses Electronic check.

### Online backup

1.1) 40 % customers has no online backup.

1.2) 22 % customers has online backup.

1.3) 7 % customers has no internet service.


thus, maximum customers has no online backup.

### Tenure

2.1) 1,013 customers belong to < 1yrs.

2.2) 294 customers belong to < 2yrs.

2.3) 180 customers belong to < 3yrs.

2.4) 145 customers belong to < 4yrs.

2.5) 120 customers belong to < 5yrs.

2.6) 93 customers belong to < 6yrs.

thus, maximum customers belong to < 1yrs.


 
# Customer Churn-Dashboard.md.txt
