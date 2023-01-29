# **Problem Statement**
Atliq is a computer hardware company which is facing challenges because of dynamically changing market. So, their Sales Director has issued tracking sales and only get verbal insights from his regional managers with lots of excel files which is of no needful to him to figure out small things. So, Sales director decides to invest in data analysis project and he would like to build power BI dashboard that can give him real time sales insights.

# **Project Execution**
There is a team of software engineers (falcons) which owns sales management system. The records of this system are stored in MySQL database.The team of Data Analysts reach out to the falcons to get an access to data base with which they can use to create the dashboard in PowerBI.
In this same manner our project is going to be executed. We are going to extract the data from the database from company’s website and then we are going to transform and load the data through Power Query in the PowerBI to build the dashboard.


# **Tools**
![image](https://user-images.githubusercontent.com/102472369/215255468-c59e6530-4d46-4653-b4df-f337a03e841c.png)
![image](https://user-images.githubusercontent.com/102472369/215255665-aab8c71e-c89f-4ba7-954c-31024c113a50.png)


# **Overview**
After a quick data exploration in MySQL, here are some initial findings:

👉The database contains 5 tables: 
- customers
- date
- markets
- products
- transactions

👉There are 17 markets, 279 products, and 38 customers;

👉The observation period is from january 2018 to june 2020;

👉The total revenue in 2020 was $ 142,23M ;

👉Most of the transactions data are in INR currency, but we have 4 records in U$ currency. And also there are Paris and New York on the “sales markets” table. We’re going to deal with it in the ETL process.


# **ETL (Extract, Transform, Load)**
Once we know the basic features of the data we have to work with, we imported the MySQL database into Power BI to do the necessary transformations and end up with a simple, reliable, and useful dashboard.

👉*Data Modeling*

We got five tables and we need to ensure that the tables are correctly connected.

Here's the star schema:

![image](https://user-images.githubusercontent.com/102472369/215340182-05b221db-29e1-4eee-b455-65494793d06e.png)
 
                        
                        
👉*Measures Created using DAX*

“Revenue” and “Sales Qty” measures to get the sum of each column instantly in the dashboard.

👉*Filtering*

As the company is operated only in India, we filtered out “Paris” and “New York” in the sales markets table by unchecking the “(blank)” field in the “zone” column.

👉*Cleaning and adding new column*

- The “sales_amount” column has -1 and 0 values. We removed them in this case so we can see only the actual sales numbers on the dashboard (sometimes “0” means promotional sales and giveaways, but to know that, we should have further information, which is not the case of this project).

- The “currency” column (sales transactions table) have 4 USD currency values, 2 of them with hidden characters, so included an argument into the conditional formula, in order to create a new column called “norm_sales_amount”, where it converts the USD currency value into INR currency value.

After all the analysis and transformation, data is reliable enough to build the dashboard.


# **The insights**
1) ***Revenue Trend*** -->The comparison between the revenue of a particular date with respect to the same date a year back to know how is the trend changing from previous year to this year .

2) ***Tabular form of profit contribution %, total profit margin % and revenue*** -->The company should try to give special benefits to *Electricalsara Stores* and *Excel stores* as they are their most profitable customers.

3) ***Revenue contribution % by market and Profit contribution % by Markets*** -->To understand about markets, how is each contributing in the over all revenue and over all profit, this comparative study will pave the way to understand the data in much more better way. Consider making a sales strategy for *Lucknow* since it is showing lowest revenue and negative profit margin and if possible so as for *Surat* and *Bhubhaneshwar* also.

4) ***Revenue by product*** -->The company should start their target campagin for *Prod047* and *Prod061* since they two are the most profitable and most selling products.

5) ***Profit contribution % by customer type*** -->To know which type of customers are contributing more so that in future the company can provide some customized offers to particular customer types on particular products to improve the sales further.

I hopefully leave you here with some ideas to evaluate your own approach.
