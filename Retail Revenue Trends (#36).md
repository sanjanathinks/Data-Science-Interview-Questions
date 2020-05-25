# Retail Revenue Trends
Given the table below, called 'orders', write code to show the average revenue
by month by channel. The format of the result should look like the following:
Month | Channel | Avg. Revenue

| order_id     | channel     | date     | month     | revenue   |
| :------------- | :----------: | :-----------:|:-------------:| ----------: |
|  1 | Online   | 2018-09-01    | 09  | 100  |
| 2  | Online | 2018-09-03 | 09   | 125|
| 3  | In_store | 2018-10-11 | 10   | 200|
| 4  | In_store | 2018-08-21 | 08   | 80|
| 5 | Online | 2018-08-13 | 08   | 200|
| 6  | Online | 2018-10-29 | 10  | 100|

Below is the code to create the above dataframe:

````python
import pandas as pd
raw_data = {'order_id': [1, 2, 3, 4, 5, 6],
'channel': ['Online', 'Online', 'In_Store', 'In_Store', 'Online', 'Online'], 
'date': ['2018-09-01', '2018-09-03', '2018-10-11', '2018-08-21', '2018-08-13', '2018-10-29'], 
'month': ['09', '09', '10', '08', '08', '10'],
'revenue' :[100, 125, 200, 80, 200, 100]}
df = pd.DataFrame(raw_data, columns = ['order_id', 'channel', 'date', 'month', 'revenue'])
````

Solution:

````python
res = []
def flatten(l):
   for x in l:
      if type(x) == list:
         flatten(x)
      else:
         res.append(x)
   return res

def average(l):
    avg = sum(l)/float(len(l))
    return avg

month_val = raw_input("Enter month in 2018:")
channel_val = raw_input("Enter channel value:")
Revenue_list = []
final_revenue_list = []
for index, row in df.iterrows(): 
    if (row['month'] == month_val and row['channel'] == channel_val):
        myList = [row['revenue']]
        Revenue_list.append(myList)
final_revenue_list = flatten(Revenue_list)
print(month_val + " "+ channel_val + " " + str(average(final_revenue_list)))
````
Let's dissect this solution to get a clearer sense of what we are doing.
The flatten method takes a list of lists and makes it into a list.
The average method finds the mean of a list. We take the return value from the flatten method and input it into the 
average method to find the mean.
Given a value for the month and a value for the channel, we iterate through the month and channel rows
in order to find an instance where our month values coincide with our given values.
We then create a list of the revenue row, which contains our revenue for the given month and channel values.
myList creates a **list of lists**, not a list. We can tell this by the syntax of the expression.
We then append myList to a Revenue_list variable and flatten it to get a single list.
Finally, we print the month, channel and average revenue, as per our result's format.
