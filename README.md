# Hotel_Booking_Analyst
## 1.. Lets read data !
'''

Categorical data refers to a data type that can be stored 
into groups/categories/labels ..

Examples of categorical variables are :  
age group, educational level,blood type etc.. 


Numerical data refers to the data that is in the form of numbers, 
Examples of numerical data are height, weight, age etc.. 

Numerical data has two categories: discrete data and continuous data


Discrete data : It basically takes countable numbers like 1, 2, 3, 4, 
                5, and so on. 
                In case of infinity, these numbers will keep going on...
                age of a fly : 8 , 9 day etc..
                
Continuous data : which is continuous in nature 
                  amount of sugar , 11.2 kg  , temp of a city  , 
                  your bank balance !
                  
For example, salary levels and performance classifications are 
discrete variables,  whereas height and weight are continuous variables.


'''
'''

Categorical data has : Object & bool data-types 
Numerical data have : Integer & Float data-type

'''
'''

Variations of int are : ('int64','int32','int16') in numpy library..

Int16 is a 16 bit signed integer , it means it can store both positive & negative values
int16 has has a range of  (2^15 − 1) to -2^15 
int16 has a length of 16 bits (2 bytes).. ie Int16 uses 16 bits 


Int32 is a 32 bit signed integer , it means it stores both positive & negative values
int32 has has a range of (2³¹ − 1) to  -2^31
int32 has a length of 32 bits (4 bytes),, ie Int32 uses 32 bits


Int64 is a 64 bit signed integer , it means it can store both positive & negative values
int64 has has a range of  (2^63 − 1) to -2^63 
int64 has a length of 64 bits (8 bytes) , ie Int64 uses 64 bits.
             

The only difference is that int64 has max range of storing numbers , then comes int32 , then 16 , then int8

That means that Int64’s take up twice as much memory-and doing operations on them may be a lot slower in some machine architectures.

However, Int64’s can represent numbers much more accurately than 32 bit floats.They also allow much larger numbers to be stored..

'''
## 2.. Lets do Data cleaning !
    Removing invalid rows
    ## Adults,babies & children cant be zero at a same time bcz booking couldn't be possible if these 3 attributes are 0 ..
'''

12 features belong to object data-type , ie.. in context to Python ,
they belong to string data-type

16 features belong to int64 nature 

4 features belong to float64 nature  ,


The memory usage of a DataFrame (including the index) is shown when calling the info(). 

 
 
The + symbol indicates that the true memory usage could be higher,  
because pandas does not count the memory used by values in columns 
with dtype=object


Passing memory_usage='deep' will enable a more accurate 
memory usage report ..


''''''
print quantile values ..

'''
'''

"adr" feature seems to have Outlier as 99th percentile value 
is 261 but 100th percentile(max value) is 5400 .. 


'''
## 4.. Perform Spatial Analysis
      Where do the guests come from ?
#### Most guests are from Portugal and other countries in Europe
## 5.. Is any difference between assigned and reserved room types or not ?
'''

## lets find meaningful insight from this :

for A category room , 56436 folks have reserved "A" & 45850 folks get assigned_room as "A".. & rest are unable to get !

for B category room , 996 folks have reserved "B" &  872 folks get assigned_room as "B".. & rest are unable to get !


'''
### Lets normalize above stuff to get more meaningful insights !
'''

Q.. Is any difference between assigned and reserved room type ?
Ans : Yes 


'''
##  6.. Bookings by market segment
'''
Most of the bookings have been done in Online mode 

'''
### 6b) Analysing Avg.price per night (ADR) of various room-types for all the market segment ..
## 7.. Total guests arrival on each day : 
         Is there any pattern in guests arrival , ie whether 
         Guests number have increased or not ? 
data['arrival_date'] = data['arrival_date_year'].astype(str) + '-' + data['arrival_date_month_index'].astype(str) + '-' + data['arrival_date_day_of_month'].astype(str)


'''
we need to use .astype(str) to convert int values to string , 
otherwise we are unable to perform this string concatenation operation ..
'''
'''
Q.. Is there any pattern ?
Ans .. No , there is no visible pattern in guests arrival 
in this line-plot as we have some un-even trend ..

'''
## 8.. Analysing distribution of "guests arrival"
     lets plot distribution of "guests arrival"
     '''


we can achieve distribution plot by smoothening our histogram using KDE  ie PDF is a smoothen form of your histogram !
ie histogram -->> apply KDE -->> we will get distribution plot 



This is called density plot bcz here height representshow many pts exists at each of these intervals 
or how dense each of the region is !



density(distribution) plot : at a point , what is a density of a data pt. ?
                or
how many percentage of data pts available at some particular pt .. ?
                or 
What is the % of data points that I will encounter at any point ? 
                or
what is the probability of certain data pt in whole data ?
                or 
prob that my data has value has some specific value 



Note : Above distribution is close to Gaussian/normal distribution , 


'''
![image](https://github.com/dk1002khoa/Hotel_Booking_Analyst/assets/117648339/2ecf6ee8-64f8-4e23-a7c2-36760f02095a)
'''

If mean & median are equal , it means 
distribution is symmetrical & bell-shaped 

If mean > median , it means distribution is not symmetrical 
& it is Right skewed (positively skewed )

If mean < median , it means distribution is not symmetrical 
& it is Right skewed (negatively skewed )


'''
#### Properties of Normal/Gaussian Distribution : 
     Bell shaped curve 
     Symmetrical distribution
     68-95-99 rule
    '''

between 1 std dev ie between u-sigma to u+sigma ie between 100 to 213 , 
we have approx 68% of data pts 
ie , approx 68% of total guests arrival values lies between interval of 100 to 213


between 2 std dev ie between u-2sigma to u+2sigma ie between 46 to 269 , 
we have approx 95% of data pts 
ie , approx 95% of total guests arrival values lies between interval of 46 to 269


between 3 std dev ie between u-3sigma to u+3sigma ie between 0 to 320 , 
we have approx 99.4% of data pts 
ie , approx 99.7% of total guests arrival values lies between interval of 0 to 320


'''
