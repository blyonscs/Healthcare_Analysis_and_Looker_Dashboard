# Healthcare Analysis and Dashboard, Looker
## Dataset from Prasad Patil, Kaggle
### Dashboard Built by Brandon Lyons

#### Background

* You are working for a healthcare company, and you are tasked with cleaning and creating a dashboard for patient data that has been collected, for easy analysis. Keeping there names confidential is important as well because many people are going to view it that aren't necessarily medical professionals.

* You job is to analyze the data and uncover insights such as what conditions and medications where prescribed for certain dates and categories and how does that translate to the billing amounts that were given.

* You need to create a real-time interactive and dynamic dashboard that management can easily use and look at/compare the data to make informed decisions.

*Personal*
Hello everyone! My name is Brandon and I'm a computer science graduate from Florida Atlantic University. I go to a wholesale retailer almost every week and enjoy analyzing and visualizing financial metrics so I really wanted to test my skills and learn new things about PowerBI from this project, follow me on Linkedin - [My Linkedin](https://www.linkedin.com/in/brandon-lyons-8b6b04158)

*Dataset Credit*
The dataset is from Prasad Patil's Healthcare Dataset from Kaggle
[Healthcare Dataset](https://www.kaggle.com/datasets/prasad22/healthcare-dataset)

## Process

1. The first step was to download the dataset from Kaggle and put it into a predetermined folder to access it easily and then load it into excel.

2. Next, I wanted to understand the data for better analysis and to make sure the data types and column names were uniform and correct compared to the data

#### Metadata

* healthcare_dataset.csv
    * Dates 2: Date Of Admission, Discharge Date 
    * Ints 2: Age, Room Number
    * Floats 1: Billing Amount
    * Strings 10: Name, Gender, Blood Type, Medical Condition, Doctor, Hospital, Insurance Provider, Admission Type, Medication, Test Results

    15 Columns
    55500 Rows

3. Next I checked the column names to see if they were relevant and uniform. The names themselves were relevant to the data they were showing, and I liked how the column names were in standard title format so I kept them the same.

4. Lastly, I wanted to check that the data compared to the data types were correct, the only thing I found was the billing amount should only be to two decimal places because it is representing dollars and not the 4 or 5 like some of them, so I put it to two by using Command-Shift-Down Arrow on mac to select the numbers and used the number button on the home tab

![Changing Decimal Places](/Images/Number_Change.png)

## Prepare, Cleaning the Data

1. First, I checked for duplicate data by selecting all the data in the table and using the remove duplicates button in the data tab, make sure to check the "my data has headers" button too if you selected the header. 

![Remove Duplicate Button](/Images/Remove_Dup.png)

![All Columns the Same for Duplicates](/Images/All_Columns_Dup.png)

534 duplicates were found and removed 

![Number of Rows Deleted](/Images/Deleted_Rows.png)

2. Next I checked for NULL values where there shouldn't be any, I used the filters on excel to look through each column one by one to see if there were any NULL's that could be removed, I didn't find any but there would show up at the bottom of the filter results if there were any.

![Checking for NULLs](/Images/Check_Null.png)

3. Next, I check for misspellings or capitalization errors in the data, the only column I found that had errors was the names column, I used the =PROPER function to change the capitalization, on a new column, filled it all the way down, and pasted just the values in a different one and moved it to the right place while deleting the other ones.

![Proper Capitalization](/Images/Proper_Change.png)

When sorting I found that some of the name in the names column had prefixes to the beginning of some of the names like Mr., Ms., Mrs., and Dr. with the end of some of the doctor ones having extra credentials like Phd and Dds. I removed the prefixes with the excel fuction

=IF(OR(LEFT(A2, 3) = "Mr.", LEFT(A2, 3) = "Ms.", LEFT(A2, 3) = "Dr.", LEFT(A2, 4) = "Mrs."), SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(A2, "Mr. ", ""), "Ms. ", ""), "Mrs. ", ""), "Dr. ", ""), A2)

and the postfixes with

=IF(OR(RIGHT(P2, 2) = "Md", RIGHT(P2, 3) = "Dds", RIGHT(P2, 3) = "Dvm", RIGHT(P2, 3) = "Phd"), SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(P2, " Md", ""), " Dds", ""), " Dvm", ""), " Phd", ""), P2)

All other postfixes like Jr. Sr. and IV will be kept as those are usually a formal part of people's names.

I then deleted the original names and put the new one in its place with the values only and checked if there were more duplicate which their wern't.

Even though the Name field isn't going to be on the dashboard it is still important to keep clean data so it can be analyzed and queried by the right people.

4. Lastly, I checked for incorrect entries on the columns that are only supposed to have certain entries like the Age, Gender, Blood Type and Admission Type. I didn't find any using the filter and sort functions so I kept them the same.

## Analyze

1. Excel: I wanted to start my analysis by creating some pivot tables that could show what trends are happening in the data and give key information that can be used by the stakeholders to develop insights. By making some of them you can see that much of this data in the table is evenly distributed across many things like gender, insurance provider, medication, and condition with both number of records and billing amount. This can be because it is sample data, but they can give valuable information in more real-world scenarios and Looker with be able to filter for very specific later on where there with be very unique results.

    * Pivot Tables

![Provider by Condition Pivot](/Images/Provider_by_Condition_Pivot.png)

![Age Pivot](/Images/Age_Pivot.png)

![Condition Pivots](/Images/Condition_Pivot.png)

![Healthcare Pivots](/Images/Healthcare_Pivot.png)

2. Looker, I wanted to brainstorm filters, scorecards and charts that I can use in looker to make it give information in a useful way and make in easy to analyze. 

    * Filters
    Admission Date
    Insurance Provider
    Doctor
    Hospital
    Gender
    Age
    Medical Condition
    Medication
    * Scorecards
    Amount of Patients
    Total Billing Amounts
    Average Billing Amount
    Highest Billing Amount
    * Charts
    Total Billing Amounts by Admission Type
    Total Billing Amounts by Insurance Provider
    Total Billing Amounts by Date
    Number of Admissions by Date
    Amount of Each Test Result
    * Types of Charts
    Pie Charts
    Bar Charts
    Line Charts

I also want to add comparison fields for the same period before it to compare to current dates for the scorecards.


## Visualization in Looker

This is my completed visualization! In the screenshot it is filtering a specific 3-month timeline and for patients with arthritis who were prescribed Aspirin. It works well and is easy to use and understand.

![Dashboard Image](/Images/Healthcare_Dashboard.png)

Link to view and use it.

[Looker Dashboard](https://lookerstudio.google.com/s/kv2jA9D7-MY)