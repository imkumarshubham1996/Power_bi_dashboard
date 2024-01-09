# Power_bi_dashboard
# Adventure Works Analysis
Adventure Works Cycles, is a large, multinational manufacturing company.The company manufactures and sells metal and
composite bicycles to North American, European and Asian commercial markets. While its base operation is in Bothell,
Washington with 290 employees, several regional sales teams are located throughout their market base.

In 2000s, Adventure Works Cycles bought a small manufacturing plant in Mexico, Which manufactures several critical 
subcomponents for the Adventure Works Cycles product line. These subcomponents are shipped to the Bothell location 
for final product assembly. In 2001, this manufacturing plant became the sole manufacturer and distributor of the 
touring bicycle product group.Coming off a successful fiscal year, Adventure Works Cycles is looking to broaden its
market share by targeting their sales to their best customers, extending their product availability through an external
Web site.
## Contents
 + Project Objectives
 + Data Sources
 + Tools Used
 + Data Preparation
    + Data Cleaning
    + Data Modelling
    + Data Transformation
    
+ Exploratory Data Analysis
+ Dashboard
+ Insights and Recommendations
+ Power BI Files

### Project Objectives
1. Conduct a thorough market analysis to identify and target the most valuable customers.
2. Identify the most profitable market and enhance product accessibility through the establishment
   of an external e-commerce platform
   
### Data Sources
The dataset used for this analysis was provided by the [Excelr Solutions](https://www.googleadservices.com/pagead/aclk?sa=L&ai=DChcSEwjJt5qq8LeDAxXVqWYCHTUpBEwYABAAGgJzbQ&ase=2&gclid=CjwKCAiAnL-sBhBnEiwAJRGigsLMv4HtQ2_dWcBMF9W0jCqZOSagdDirBdsI6vgGP_QOE_WPmbou0hoCCPIQAvD_BwE&ei=Im2QZaDmJPy74-EPisWOiA0&ohost=www.google.com&cid=CAESVuD2ch22XuVzZ3_Yf5l4iIIj8zSXtJDF7hHJfKWqoWEO1WUanG-km-Ol2_Hqkjt3A2W7CHG9Mq6ERCi0kgaMuWEpsXWCCO4xWFEfFaMjPt30xSNWWcl2&sig=AOD64_3n32L52kKMw_we5YFjj9pUSGiXRA&q&sqi=2&nis=4&adurl&ved=2ahUKEwig_5Sq8LeDAxX83TgGHYqiA9EQ0Qx6BAgJEAM) as part of an internship project, whose data spans from December 2010 to January 2014 and
which contains the following files like-
+ FactInternetSales
+ DimDate
+ DimProduct
+ DimProductCategory
+ DimProductSubCategory
+ DimSalesterritory
+ Dimcustomer

### Tools Used
+ Power BI

### Data Preparation

#### Data Cleaning
The data cleaning process was executed using Power Query Editor and involved several operations mentioned below to ensure
data accuracy and consistency:

+ Union of tables using append queries.
+ Correction of data types to ensure accurate representation.
+ Elimination of empty and insignificant columns for streamlined analysis.
+ Removal of empty rows for a more concise dataset.
+ Cross-field validation to verify relationships between different fields for data consistency.
+ Derivation of profit through a calculated column
+ Addition of a custom column for customer full names using power query
      Customer_fullname = Text.Combine({[FirstName], [MiddleName], [LastName]}, " ")
      
After the data cleaning process, the refined datasets were loaded into Power BI Desktop for further analysis.   

#### Data Modelling
Organized the data set and create data model in model view

Data model-	
![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Capture6.PNG)
#### Data Transformation
Generate a calculated field in Power BI using DAX by leveraging existing fields, such as the customer's birth
date from the Customer table and the order date from the Sales table. Utilize the DATEDIFF function along with
the RELATED function to calculate the customer's age at the time of placing an order.   
Example-
Age=DATEDIFF(RELATED(Dimcustomer[BirthDate]),FactInternetsales_Union[OrderDate],YEAR)

        
Also used  Supplementary DAX expressions, encompassing functionalities like weekday, weeknum, and
if statements, were used to generate calculated columns. The analysis process involved
the application of various functions such as Sameperiodlastyear, Rankx, Calculate, Count, Sum, and others  
Example-
        
    Weekday_no = WEEKDAY(FactInternetSales_UNION[OrderDate].[Date])
    Weekday/Weekend = IF(FactInternetSales_UNION[Weekday_no]<=5,"Weekday","Weekend")
### Exploratory Data Analysis
Adventure Works offers a diverse product range of 606 items for sale across 6 countries, 
encompassing 4 main categories and 37 subcategories. Over the period from December 2010
to January 2014, customers purchased a total of 60,398 products, contributing to an overall 
sales amount of 29.36 million dollars, with a corresponding profit of 9 million dollars. The
profit margin achieved during this period stands at 30.65%. The customer base comprises a total
of 18,484 individuals. The cumulative production cost for these products is recorded as 17.28 million dollars.
    
    1. Yearly, Quarterly, and Monthly Sales and Profit Trends: 
The depicted chart illustrates Adventure Works' consistent sales growth from 2010 to 2014, 
reaching a peak in Q4 2013. A notable decline occurred in 2012, mainly attributed to reduced 
sales in Q2, possibly influenced by the emergence of a competitive force offering enhanced customer
opportunities.
Each year consistently sees a sales peak in the fourth quarter, likely due to festive season demand.

![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Sales\Capture1.PNG)

    2. Weekday vs. Weekend Sales Distribution:
Analysis reveals that weekend sales constitute 28.2%, whereas weekday sales dominate at 71.8%.
		This suggests a preference for online shopping during work breaks or after work hours on
        weekdays.
        
![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Sales\Capture2.PNG)

    3. Country-wise Sales Breakdown:
The United States leads in sales, contributing 31.98% of the total, followed by Australia at 30.86%.
		Canada lags behind with a modest 6.74% of total sales.  
        
![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Sales\Capture3.PNG)   

    4. Category-specific Revenue Breakdown:
Bikes category emerge as the primary revenue driver, accounting for 96.46% of total revenue, with
		Accessories and Clothing contributing 2.39% and 1.16%, respectively.
        
![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Sales\Capture5.PNG)       

    5. Age Group Impact on Sales:
Customers aged 31 to 40 and 41 to 50 significantly contribute to revenue, generating $11.36 million
	    and $8.17 million, respectively. Conversely, customers above 70 contribute less than $1 million.
        
![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Sales\Capture4.PNG)

    6. Top N Customers and Revenue Generation:
Utilizing a parameterized visual, the company can identify top customers based on sales amount,
	    enabling targeted benefits to enhance their contribution. 
	    Nichole Nara emerges as the top revenue contributor.
     
![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Customer\Capture3.PNG)

    7. Gender-based Sales Equality:
Both male and female customers equally contribute to company revenue, with sales amounts of $14.55 million
		and $14.81 million, respectively.  
        
![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Customer\Capture2.PNG)

    8. Commute Distance Impact on Sales:
Customers with shorter commute distances (0-1 miles) significantly drive sales, while those with distances 
	    between 2-10 miles contribute half of the sales value. Customers with distances exceeding 10 miles contribute
	    less, potentially due to a preference for alternative transportation.
        
 ![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Customer\Capture5.PNG)
 
    9. Sales Disparity Based on Marital Status:
Married individuals show a higher tendency to make purchases (51.73%) compared to single individuals (48.27%),
		This trend may be indicative of a connection between the act of cycling a pursuit known for its health benefits
		and eco-friendly nature and the shared values or recreational choices often associated with married life.
        
 ![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Customer\Capture4.PNG)
 
    10. Age Distribution and Order Frequency:
The histogram illustrates that customers aged 31-40 place the highest number of orders (21,000),
		 followed by the 41-50 age group with 17,000 orders. 
		 Histogram is right skewed ,and the probability of getting outliers above 70 is more but receiving
		 orders from customers over the age 70 is notably low.
         
 ![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Customer\Capture1.PNG)  
 
    11. Category-Subcategory Impact on Sales and Profit:
Bikes, especially Road Bikes, Mountain Bikes, and Touring Bikes, contribute significantly to sales 
		 and profit. In Accessories, Tires and Tubes dominate, while in Clothing, Jerseys lead in revenue. 
		 The sales trend for Bikes shows consistent growth from 2010 to 2014.
         
 ![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Product\Capture4.PNG)    
 
    12. Sales Based on Model and Color Preferences:
The top 3 most popular bicycle models include Mountain-200 in Black and Silver, Road 150 in Red,
		and Road 250 in Black and Red respectively. This highlights a discernible inclination among customers
		for particular models and color combinations.
        
The highest revenue-generating product is the Mountain-200 Black, contributing a substantial 4.03M in sales,
		signifying its strong market appeal and customer preference.        
        
 ![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Product\Capture8.PNG) 
 
    13.Model wise Correlation between Sales and Profit:
A correlation factor of 0.9 between model-wise sales and profit indicates a very strong positive correlation.
	   This means that there is a highly consistent and positive relationship between the sales and profit of the 
	   different models. This suggests that as sales for a particular model increase, the profit generated from that
	   model also tends to increase, and vice versa.
       
       
 ![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\Product\Capture2.PNG) 
 
 ### Dashboard
 Sales Dashboard
 
 ![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\CaptureSales.PNG) 
 
 Customer Dashboard

![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\CaptureCustomer.PNG)

Product Dashboard

![alt text](C:\Users\Subham\Desktop\EXCELR PROJECT\second project power pivot\power bi\Screenshots\CaptureProduct.PNG)

### Insights and Recommendations
+  `Optimize Sales Strategies Based on Time Trends:`

    Leverage the consistent pattern of peak sales in the fourth quarter across the years, 
    especially the significant peak in Q4 2013, to optimize inventory and marketing strategies.
    Plan for increased stock and promotional activities during this period. Additionally, analyse
    the sales dip in 2012, particularly in Q2, to understand the causes and develop strategies to
    mitigate similar declines in the future. This approach should include year-round vigilance and 
    adaptability to maintain sales momentum throughout the year, capitalizing on identified peak times
+ `Diversify Geographical Focus:`

   Explore opportunities to expand market share in regions with lower sales, such as Canada.
   Tailor marketing strategies to address the specific needs and preferences of these regions.
+  `Strategic Promotion of Accessories and Clothing:` 

    Given the dominance of bike sales, strategically promote accessories and clothing to diversify revenue
    streams. Highlight the unique features and benefits of these products to attract customer interest
+ `Customer Loyalty Programs:`

   Implement customer loyalty programs to further engage top customers, like Nichole Nara.
   Recognize and reward their contribution to encourage continued loyalty and increased spending
+ `Enhanced Product Visibility for Road Bikes:`

   Given the significant contribution of Road Bikes to sales and profit, ensure prominent visibility 
   and promotion of this category. Highlight the features that make Road Bikes popular among customers
   to drive continued growth in this segment
+ `Personalized Marketing for Age Groups:`
    
    Customize marketing communications and promotions to align with the preferences of key age demographics,
    notably targeting customers aged 31 to 50. This tailored approach aims to increase engagement and boost 
    sales within these influential age segments.
+ `Focus on High-Performing Models:`
   
   Concentrate resources, marketing efforts, and inventory management on the models that have demonstrated 
   both high sales and high profitability. This targeted approach can maximize returns and ensure efficient
   resource allocation
