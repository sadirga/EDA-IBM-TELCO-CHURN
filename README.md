# EDA-IBM-TELCO-CHURN
Exploratory Data Analysis of IBM Sample Data Set Telco Customer Churn  
[![t1.png](https://i.postimg.cc/W37zmsHb/t1.png)](https://postimg.cc/34d3YQhP)  

#
<br>

## INTRODUCTION
Customer churn is a term used when a customer unsubscribes or stop using services from company A.

## PROBLEMS
Find new customers will be more difficult and costly than to retain or mantainaing the existing customers.

## GOALS
Get an analysis of the customer churn characteristic and finding the correct strategies to handle it.

### Read Data
[![T3.png](https://i.postimg.cc/Pfw2HxR8/T3.png)](https://postimg.cc/8sThB1D1)  

[![T4.png](https://i.postimg.cc/PqMNYmJ8/T4.png)](https://postimg.cc/3ydKH0gK)  

The Data have 7043 rows and 20 columns, and from the columns we can grouped them into 3 groups.
1. customer demographic 
2. IBM Telco Services
3. Contract, Billing and Payment Method

### EDA  
#### CUSTOMER CHURN DISTRIBUTION
[![t8.png](https://i.postimg.cc/9M6Mj1NK/t8.png)](https://postimg.cc/DJcFrQhP)  

From graph above we can see the density of customer who churn/unsubscribe the services are below 20 months of tenure and between 65 to 95 Monthly Charges.  
Now let's take a further look into the data  

[![T9.png](https://i.postimg.cc/FzhnBXVK/T9.png)](https://postimg.cc/VrHRJTTy)  

Now we know 26.5% from Total Customer is Churning or unsubsribing, we also can see from the statistical table data, the average of tenure of customer who churn is around 18 months. And the average of their Monthly Charge is $74, from q1,q2,q3 we can also see the precise number of the density customer churning.

From the Demographic feature, gender doesn't show significance but from Partner and Dependents, we can see customer who doesn't have a partner or dependents are more likely to churn, while both partner and dependents are highly linked to each other. As we see from the Senior Citizen feature, looks like the non senior citizen has more customer to churn, but if we look closely, the churn rate of Senior Citizen is 42%! almost half of total Senior Citizen Customer.  

[![t10.png](https://i.postimg.cc/rwgnKHc6/t10.png)](https://postimg.cc/75GMRmfX)  
Next we have a bar graph showing Customer Churn distribution based on the company services. It shows customers with Fiber Optic Internet Services are more likely to churn. As for the Contract type, a month to month contract are shows significance difference between the other two. And from the billing and payment method we also could see a linked, customers with paperpless billing and electronic check payment are more likely to churn  
```python
pd.crosstab(index=[df['InternetService'], df['PhoneService']], columns=df['Churn'])
(pd.crosstab(index=[df['PaperlessBilling'],df['PaymentMethod']], columns=df['Churn'],normalize='columns', margins=True)*100).round(2)
```  
[![T14.png](https://i.postimg.cc/1Xkx7jX7/T14.png)](https://postimg.cc/q6xZzQ82)  

From the main Services, we can see Customer who has Internet Services of Fiber Optic and Phone Services are more likely to Churn.  

[![T16.png](https://i.postimg.cc/D0ZjQdcj/T16.png)](https://postimg.cc/Hcq9dMRX)  

Then we can see, Customer with paperless billing and electronic check payment scoop up to 49% from total customer who churn.  

[![T11.png](https://i.postimg.cc/wxZcbpxT/T11.png)](https://postimg.cc/XXKCptyT)  

and from the last categorical feature we could see from additional feature except the streaming services, it shows that customers with no additional features are likely to churn.  


### CONCLUSION
```python
df[(df['Churn']== 'Yes') & (df['MonthlyCharges'] > 55)].mean()
```  
[![T17.png](https://i.postimg.cc/FHLcX1Zn/T17.png)](https://postimg.cc/sM31pjbp)  
```python
df[(df['Churn']== 'No') & (df['MonthlyCharges'] > 55)].mean()
```  
[![t18.png](https://i.postimg.cc/hjPfvGLn/t18.png)](https://postimg.cc/p9421Rcc)  
[![T19.png](https://i.postimg.cc/pLvHB6pc/T19.png)](https://postimg.cc/pps4WkQK)  

- If we take another look, the average monthly charges of customer who churn with monthly charge greater than $55 are pretty much the same,i t means price is not the main problem.  
- Senior Citizen although only 16% from total Customer, it has 42% chun rate. It is better to approach them more by giving some discount or promotion gift or any other type of conventional promotion.  
- For customers with No Partner or Dependents are likely to churn, It is better to
- Customer Non Senior Citizen whom bills are paperless and the payment method are electrocnic check, also likely to churn with share of 32% from total customer who churn. 
If we add contract type into it, Customer Non Senior Citizen whom bills are paperless and the payment method are electrocnic check, with month to month contract are 28% from total customer churn. ***Giving discounted price or limited offer yearly contract discounted price to convert their contract to yearly.***


