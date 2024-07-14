---
categories: 
 - Pandas
layout: single
title: "(Pandas) 1. Series"
---

## 1. PANDAS SERIES

- Pandas는 Numpy를 기반으로 하는 데이터 조작 및 분석 도구
- Pandas는 DataFrame이라는 데이터 구조를 사용
- DataFrame은 프로그래머가 데이터를 행과 열로 구성된 표 형태로 저장하고 조작할 수 있게 함
- Series와 DataFrame의 차이점 - Series는 DataFrame의 단일 열로 간주


```python
import pandas as pd
```


```python
# 다음은 5개의 주식을 포함하는 파이썬 리스트를 정의: Nvidia, Microsoft, FaceBook, Amazon, and Boeing
my_list = ['NVDA', 'MSFT', 'FB', 'AMZN', 'BA']
```


```python
# 데이터 타입
type(my_list)
```

    list

```python
# Let's create a one dimensional Pandas "series" 
# Let's use Pandas Constructor Method to create a series from a Python list
# Note that series is formed of data and associated index (numeric index has been automatically generated) 
# Check Pandas Documentation for More information: https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.html#pandas.Series
# Object datatype is used for text data (String)
series_1 = pd.Series(data = my_list)
series_1
```

    0    NVDA
    1    MSFT
    2      FB
    3    AMZN
    4      BA
    dtype: object

```python
# Let's confirm the Pandas Series Datatype
type(series_1)
```




    pandas.core.series.Series




```python
# Let's define another Pandas Series that contains numeric values (stock prices) instead of text data
# Note that we have int64 datatype which means it's integer stored in 64 bits in memory
series_2 = pd.Series(data = [100, 200, 500, 1000, 5000])
series_2
```




    0     100
    1     200
    2     500
    3    1000
    4    5000
    dtype: int64



**MINI CHALLENGE #1:**
- **Define a Pandas Series named "my_series" that contains your top 3 favourite movies. Confirm the datatype of "my_series"**


```python
my_series = pd.Series(data = ['Terminator', 'Coco', 'Dragon'])
my_series
```




    0    Terminator
    1          Coco
    2        Dragon
    dtype: object




```python
type(my_series)
```




    pandas.core.series.Series



# 2. DEFINE A PANDAS SERIES WITH CUSTOM INDEX


```python
# Let's define a Python list that contains 5 stocks: Nvidia, Microsoft, FaceBook, Amazon, and Boeing
my_list = ['NVDA', 'MSFT', 'FB', 'AMZN', 'BA']
my_list
```




    ['NVDA', 'MSFT', 'FB', 'AMZN', 'BA']




```python
# Let's define a python list as shown below. This python list will be used for the Series index:
my_labels = ['stock#1', 'stock#2', 'stock#3', 'stock#4', 'stock#5']
my_labels
```




    ['stock#1', 'stock#2', 'stock#3', 'stock#4', 'stock#5']




```python
# Let's create a one dimensional Pandas "series" 
# Let's use Pandas Constructor Method to create a series from a Python list
# Note that this series is formed of data and associated labels 
series_3 = pd.Series(data = my_list, index = my_labels)
```


```python
# Let's view the series
series_3
```




    stock#1    NVDA
    stock#2    MSFT
    stock#3      FB
    stock#4    AMZN
    stock#5      BA
    dtype: object




```python
# Let's obtain the datatype
type(series_3)
```




    pandas.core.series.Series



**MINI CHALLENGE #2:**
- **Define a Pandas Series named "my_series" that contains your top 3 favourite movies. Instead of using default numeric indexes (similar to mini challenge #1), use the following indexes "movie #1", "Movie #2", and "movie #3"**


```python
movie_list = ['Terminator', 'Coco', 'Dragon']
movie_label = ['Movie #1', 'Movie #2', 'Movie #3']
my_series = pd.Series(data = movie_list, index = movie_label)
```


```python
my_series
```




    Movie #1    Terminator
    Movie #2          Coco
    Movie #3        Dragon
    dtype: object



# 3. DEFINE A PANDAS SERIES FROM A DICTIONARY


```python
# A Dictionary consists of a collection of key-value pairs. Each key-value pair maps the key to its corresponding value.
# Keys are unique within a dictionary while values may not be. 
# List elements are accessed by their position in the list, via indexing while Dictionary elements are accessed via keys
# Define a dictionary named "my_dict" using key-value pairs
my_dict = {'Bank Client Name': 'Steve',
 'Bank client ID': 111,
 'Net worth [$]': 3500,
 'Years with bank': 9}
```


```python
# Show the dictionary
my_dict
```




    {'Bank Client Name': 'Steve',
     'Bank client ID': 111,
     'Net worth [$]': 3500,
     'Years with bank': 9}




```python
# Confirm the dictionary datatype 
type(my_dict)
```




    dict




```python
# Let's define a Pandas Series Using the dictionary
series_4 = pd.Series(my_dict)
series_4
```




    Bank Client Name    Steve
    Bank client ID        111
    Net worth [$]        3500
    Years with bank         9
    dtype: object



**MINI CHALLENGE #3:**
- **Create a Pandas Series from a dictionary with 3 of your favourite stocks and their corresponding prices** 


```python
stock_dict = {"ABC" : 1000,
              "DDD" : 2000,
              "ERT" : 1300}
stock_series = pd.Series(stock_dict)
```


```python
stock_series
```




    ABC    1000
    DDD    2000
    ERT    1300
    dtype: int64



# 4. PANDAS ATTRIBUTES


```python
# Attributes/Properties: do not use parantheses "()" and are used to get Pandas Series Properties. Ex: my_series.values, my_series.shape
# Methods: use parantheses "()" and might include arguments and they actually alter/change the Pandas Series. Ex: my_series.tail(), my_series.head(), my_series.drop_duplicates()
# Indexers: use square brackets "[]" and are used to access specific elements in a Pandas Series or DataFrame. Ex: my_series.loc[], my_series.iloc[]

# Let's redefine a Pandas Series containing our favourite 5 stocks 
# Nvidia, Microsoft, FaceBook, Amazon, and Boeing
my_list = ['Nvidia', 'Microsoft', 'FaceBook', 'Amazon', 'Boeing']
my_series = pd.Series(data = my_list)
my_series
```




    0       Nvidia
    1    Microsoft
    2     FaceBook
    3       Amazon
    4       Boeing
    dtype: object




```python
# ".Values" attribute is used to return Series as ndarray depending on its dtype
# Check this for more information: https://pandas.pydata.org/docs/reference/api/pandas.Series.values.html#pandas.Series.values
my_series.values
```




    array(['Nvidia', 'Microsoft', 'FaceBook', 'Amazon', 'Boeing'],
          dtype=object)




```python
# index is used to return the index (axis labels) of the Series
my_series.index
```




    RangeIndex(start=0, stop=5, step=1)




```python
stock_series.index
```




    Index(['ABC', 'DDD', 'ERT'], dtype='object')




```python
# dtype is used to return the datatype of the Series ('O' stands for 'object' datatype)
my_series.dtype
```




    dtype('O')




```python
# Check if all elements are unique or not
my_series.is_unique
```




    True




```python
# Check the shape of the Series
# note that a Series is one dimensional
my_series.shape
```




    (5,)



**MINI CHALLENGE #4:** 
- **What is the size of the Pandas Series? (External Research for the proper attribute is Required)**


```python
my_series.size
```




    5



# 5. PANDAS METHODS


```python
# Methods have parentheses and they actually alter/change the Pandas Series
# Methods: use parantheses "()" and might include arguments. Ex: my_series.tail(), my_series.head(), my_series.drop_duplicates()

# Let's define another Pandas Series that contains numeric values (stock prices) instead of text data
# Note that we have int64 datatype which means it contains integer values stored in 64 bits in memory

my_series = pd.Series(data = [100, 200, 500, 1000, 5000])
my_series
```




    0     100
    1     200
    2     500
    3    1000
    4    5000
    dtype: int64




```python
# Let's obtain the sum of all elements in the Pandas Series
my_series.sum()
```




    6800




```python
# Let's obtain the multiplication of all elements in the Pandas Series
my_series.product()
```




    50000000000000




```python
# Let's obtain the average
my_series.mean()
```




    1360.0




```python
# Let's show the first couple of elements in the Pandas Series
my_series.head(2)
```




    0    100
    1    200
    dtype: int64




```python
# Note that head creates a new dataframe 
new_series = my_series.head(3)
new_series
```




    0    100
    1    200
    2    500
    dtype: int64



**MINI CHALLENGE #5:** 
- **Show the last 2 rows in the Pandas Series (External Research is Required)** 
- **How many bytes does this Pandas Series consume in memory? (External Research is Required)**


```python
new_series2 = my_series.tail(2)
print(new_series2)
```

    3    1000
    4    5000
    dtype: int64
    


```python
new_series2.memory_usage()
```




    148



# 6. IMPORT CSV DATA (1-D) USING PANDAS


```python
# Pandas read_csv is used to read a csv file and store data in a DataFrame by default (DataFrames will be covered shortly!)
# Use Squeeze to convert it into a Pandas Series (One-dimensional), Padas 2.0 버전부터는 squeeze 옵션이 없고 squeeze() method 사용
# Notice that no foramtting exists when a Series is plotted

sp500 = pd.read_csv('./sample_data/S_P500_Prices.csv')
sp500_s = sp500.squeeze()
```


```python
type(sp500)
```




    pandas.core.frame.DataFrame




```python
type(sp500_s)
```




    pandas.core.series.Series



**MINI CHALLENGE #6:**
- **Set Squeeze = False and rerun the cell, what do you notice? Use Type to compare both outputs**


```python
sp500_2 = pd.read_csv('./sample_data/S_P500_Prices.csv')
```


```python
print(sp500_2)
```

                sp500
    0     1295.500000
    1     1289.089966
    2     1293.670044
    3     1308.040039
    4     1314.500000
    ...           ...
    2154  3327.770020
    2155  3349.159912
    2156  3351.280029
    2157  3360.469971
    2158  3333.689941
    
    [2159 rows x 1 columns]
    


```python
type(sp500_2)
```




    pandas.core.frame.DataFrame



# 7. PANDAS BUILT-IN FUNCTIONS


```python
# Pandas works great with pre-existing python functions 
# You don't have to play with pandas methods and directly leverage Python functions
# Check Python built-in functions here: https://docs.python.org/3/library/functions.html

sp500 = pd.read_csv('./sample_data/S_P500_Prices.csv')
sp500 = sp500.squeeze()
sp500
```




    0       1295.500000
    1       1289.089966
    2       1293.670044
    3       1308.040039
    4       1314.500000
               ...     
    2154    3327.770020
    2155    3349.159912
    2156    3351.280029
    2157    3360.469971
    2158    3333.689941
    Name: sp500, Length: 2159, dtype: float64




```python
# Obtain the Data Type of the Pandas Series
sp500
```




    0       1295.500000
    1       1289.089966
    2       1293.670044
    3       1308.040039
    4       1314.500000
               ...     
    2154    3327.770020
    2155    3349.159912
    2156    3351.280029
    2157    3360.469971
    2158    3333.689941
    Name: sp500, Length: 2159, dtype: float64




```python
# Obtain the length of the Pandas Series
len(sp500)
```




    2159




```python
# Obtain the maximum value of the Pandas Series
max(sp500)
```




    3386.149902




```python
# Obtain the minimum value of the Pandas Series
min(sp500)
```




    1278.040039



**MINI CHALLENGE #7:**
- **Given the following Pandas Series, convert all positive values to negative using python built-in functions**
- **Obtain only unique values (ie: Remove duplicates) using python built-in functions**
- **my_series = pd.Series(data = [-10, 100, -30, 50, 100])**



```python
my_series = pd.Series(data = [-10, 100, -30, 50, 100])
my_series
```




    0    -10
    1    100
    2    -30
    3     50
    4    100
    dtype: int64




```python
my_series2 = my_series.abs() * -1
my_series2
```




    0    -10
    1   -100
    2    -30
    3    -50
    4   -100
    dtype: int64




```python
set(my_series)
```




    {-30, -10, 50, 100}



# 8. SORTING PANDAS SERIES


```python
# Let's import CSV data as follows:
sp500 = pd.read_csv('./sample_data/S_P500_Prices.csv')
sp500 = sp500.squeeze()
sp500
```




    0       1295.500000
    1       1289.089966
    2       1293.670044
    3       1308.040039
    4       1314.500000
               ...     
    2154    3327.770020
    2155    3349.159912
    2156    3351.280029
    2157    3360.469971
    2158    3333.689941
    Name: sp500, Length: 2159, dtype: float64




```python
# You can sort the values in the dataframe as follows
sp500.sort_values()
```




    97      1278.040039
    98      1278.180054
    99      1285.500000
    1       1289.089966
    2       1293.670044
               ...     
    2038    3373.229980
    2034    3373.939941
    2033    3379.449951
    2035    3380.159912
    2037    3386.149902
    Name: sp500, Length: 2159, dtype: float64




```python
# Let's view Pandas Series again after sorting, Note that nothing changed in memory! you have to make sure that inplace is set to True
sp500
```




    0       1295.500000
    1       1289.089966
    2       1293.670044
    3       1308.040039
    4       1314.500000
               ...     
    2154    3327.770020
    2155    3349.159912
    2156    3351.280029
    2157    3360.469971
    2158    3333.689941
    Name: sp500, Length: 2159, dtype: float64




```python
type(sp500)
```




    pandas.core.series.Series




```python
# Set inplace = True to ensure that change has taken place in memory
# sp500.sort_values(inplace = True) -> 작동하지 않음(Error 발생)
sp500_2 = sp500.copy() 
sp500_2.sort_values(inplace=True)  # 복사본을 만들어서 사용하는 경우 inplace parameter 작동, 그러면 그냥 sp500_2 = sp500.sort_values() 하고 똑같지 않나...
```


```python
# Note that now the change (ordering) took place 
sp500_2
```




    97      1278.040039
    98      1278.180054
    99      1285.500000
    1       1289.089966
    2       1293.670044
               ...     
    2038    3373.229980
    2034    3373.939941
    2033    3379.449951
    2035    3380.159912
    2037    3386.149902
    Name: sp500, Length: 2159, dtype: float64




```python
# Notice that the indexes are now changed 
# You can also sort by index (revert back to the original Pandas Series) as follows: 
# 요건 또 inplace parameter가 작동하네...
sp500_2.sort_index(inplace = True)
```


```python
sp500_2
```




    0       1295.500000
    1       1289.089966
    2       1293.670044
    3       1308.040039
    4       1314.500000
               ...     
    2154    3327.770020
    2155    3349.159912
    2156    3351.280029
    2157    3360.469971
    2158    3333.689941
    Name: sp500, Length: 2159, dtype: float64



**MINI CHALLENGE #8:**
- **Sort the S&P500 values in a decending order instead. Make sure to update values in-memory.**


```python
sp500_3 = sp500.sort_values(ascending=False)
sp500_3
```




    2037    3386.149902
    2035    3380.159912
    2033    3379.449951
    2034    3373.939941
    2038    3373.229980
               ...     
    2       1293.670044
    1       1289.089966
    99      1285.500000
    98      1278.180054
    97      1278.040039
    Name: sp500, Length: 2159, dtype: float64



# 9. PERFORM MATH OPERATIONS ON PANDAS SERIES


```python
# Let's import CSV data as follows:
sp500 = pd.read_csv('./sample_data/S_P500_Prices.csv')
sp500 = sp500.squeeze()
sp500
```




    0       1295.500000
    1       1289.089966
    2       1293.670044
    3       1308.040039
    4       1314.500000
               ...     
    2154    3327.770020
    2155    3349.159912
    2156    3351.280029
    2157    3360.469971
    2158    3333.689941
    Name: sp500, Length: 2159, dtype: float64




```python
# Apply Sum Method on Pandas Series
sp500.sum()
```




    4790280.287214




```python
# Apply count Method on Pandas Series
sp500.count()
```




    2159




```python
# Obtain the maximum value
sp500.max()
```




    3386.149902




```python
# Obtain the minimum value
sp500.min()
```




    1278.040039




```python
# My favourite: Describe! 
# Describe is used to obtain all statistical information in one place 
sp500.describe()
```




    count    2159.000000
    mean     2218.749554
    std       537.321727
    min      1278.040039
    25%      1847.984985
    50%      2106.629883
    75%      2705.810059
    max      3386.149902
    Name: sp500, dtype: float64



**MINI CHALLENGE #9:**
- **Obtain the average price of the S&P500 using two different methods**


```python
print(sp500.mean())
print(sp500.sum() / sp500.count())
```

    2218.7495540592868
    2218.7495540592868
    

# 10. CHECK IF A GIVEN ELEMENT EXISTS IN A PANDAS SERIES


```python
# Let's import CSV data as follows:
sp500 = pd.read_csv('./sample_data/S_P500_Prices.csv')
sp500 = sp500.squeeze()
sp500
```




    0       1295.500000
    1       1289.089966
    2       1293.670044
    3       1308.040039
    4       1314.500000
               ...     
    2154    3327.770020
    2155    3349.159912
    2156    3351.280029
    2157    3360.469971
    2158    3333.689941
    Name: sp500, Length: 2159, dtype: float64




```python
# Check if a given number exists in a Pandas Series values
# Returns a boolean "True" or "False"
1295.5000 in sp500.values
```




    True




```python
# Check if a given number exists in a Pandas Series index
1295.5000 in sp500.index
```




    False




```python
# Note that by default 'in' will search in Pandas index and not values
1295.5000 in sp500
```




    False



**MINI CHALLENGE #10:**
- **Check if the stock price 3349 exists in the sp500 Pandas Series or not**
- **Round stock prices to the nearest integer and check again**


```python
3349 in sp500.values
```




    False




```python
sp500.values
```




    array([1295.5     , 1289.089966, 1293.670044, ..., 3351.280029,
           3360.469971, 3333.689941])




```python
sp500 = round(sp500)
sp500
```




    0       1296.0
    1       1289.0
    2       1294.0
    3       1308.0
    4       1314.0
             ...  
    2154    3328.0
    2155    3349.0
    2156    3351.0
    2157    3360.0
    2158    3334.0
    Name: sp500, Length: 2159, dtype: float64




```python
import math
3349 in sp500.values
```




    True



# 11. INDEXING: OBTAIN SPECIFIC ELEMENTS FROM PANDAS SERIES


```python
# Let's import CSV data as follows:
sp500 = pd.read_csv('./sample_data/S_P500_Prices.csv')
sp500 = sp500.squeeze()
sp500
```




    0       1295.500000
    1       1289.089966
    2       1293.670044
    3       1308.040039
    4       1314.500000
               ...     
    2154    3327.770020
    2155    3349.159912
    2156    3351.280029
    2157    3360.469971
    2158    3333.689941
    Name: sp500, Length: 2159, dtype: float64




```python
# Obtain the first element in a Pandas Series
# Note that first element has an index 0
sp500[0]
```




    1295.5




```python
# Obtain the last element in the Pandas Series
sp500[2158]
```




    3333.689941



**MINI CHALLENGE #11:**
- **Obtain the fifth element in the Pandas Series**


```python
sp500[4]
```




    1314.5



# 12. SLICING: OBTAIN MULTIPLE ELEMENTS FROM PANDAS SERIES


```python
# Let's import CSV data as follows:
sp500 = pd.read_csv('./sample_data/S_P500_Prices.csv')
sp500 = sp500.squeeze()
sp500
```




    0       1295.500000
    1       1289.089966
    2       1293.670044
    3       1308.040039
    4       1314.500000
               ...     
    2154    3327.770020
    2155    3349.159912
    2156    3351.280029
    2157    3360.469971
    2158    3333.689941
    Name: sp500, Length: 2159, dtype: float64




```python
# Slice elements from a Pandas Series
# Let's obtain elements starting from index 0 up until and not including index 5 (ie: indexes 0-4)
sp500[0:5]
```




    0    1295.500000
    1    1289.089966
    2    1293.670044
    3    1308.040039
    4    1314.500000
    Name: sp500, dtype: float64




```python
# obtain all elements starting from index 0 up until and not including index 10
sp500[:10]
```




    0    1295.500000
    1    1289.089966
    2    1293.670044
    3    1308.040039
    4    1314.500000
    5    1315.380005
    6    1316.000000
    7    1314.650024
    8    1326.060059
    9    1318.430054
    Name: sp500, dtype: float64




```python
# obtain all elements starting from index 5 up until the end of the Pandas Series
sp500[5:]
```




    5       1315.380005
    6       1316.000000
    7       1314.650024
    8       1326.060059
    9       1318.430054
               ...     
    2154    3327.770020
    2155    3349.159912
    2156    3351.280029
    2157    3360.469971
    2158    3333.689941
    Name: sp500, Length: 2154, dtype: float64



**MINI CHALLENGE #12:**
- **Obtain all elements in Pandas Series except for the last 3 elements**

# EXCELLENT JOB!

# MINI CHALLENGE SOLUTIONS

**MINI CHALLENGE #1 SOLUTION:**
- **Define a Pandas Series named "my_series" that contains your top 3 favourite movies. Confirm the datatype of "my_series"**


```python
# Let's define a Python list that contains 3 top movies
my_list = ['The Godfather','Star Wars','The Wolf of Wall Street'] 
my_series = pd.Series(data = my_list) 
my_series
```




    0              The Godfather
    1                  Star Wars
    2    The Wolf of Wall Street
    dtype: object




```python
type(my_series)
```




    pandas.core.series.Series



**MINI CHALLENGE #2 SOLUTION:**
- **Define a Pandas Series named "my_series" that contains your top 3 favourite movies. Instead of using default numeric indexes (similar to mini challenge #1), use the following indexes "movie #1", "Movie #2", and "movie #3"**


```python
# Let's define a Python list that contains 3 movies as follows
my_list = ['The Godfather','Star Wars','The Wolf of Wall Street'] 

# Let's define a python list as shown below. This python list will be used for the Series index:
my_labels = ['movie #1', 'movie #2', 'movie #3']

```


```python
# Let's create a one dimensional Pandas "series" 
# Let's use Pandas Constructor Method to create a series from a Python list
# Note that this series is formed of data and associated labels 
my_series = pd.Series(data = my_list, index = my_labels)
my_series
```




    movie #1              The Godfather
    movie #2                  Star Wars
    movie #3    The Wolf of Wall Street
    dtype: object



**MINI CHALLENGE #3 SOLUTION:**
- **Create a Pandas Series from a dictionary with 3 of your favourite stocks and their corresponding prices** 



```python
stocks = {'SP500': 3000, 
          'AAPL': 400,
          'TSLA': 2200}
print(stocks)
```

    {'SP500': 3000, 'AAPL': 400, 'TSLA': 2200}
    


```python
# Let's define a Pandas Series Using the dictionary
my_series = pd.Series(stocks)
my_series
```




    SP500    3000
    AAPL      400
    TSLA     2200
    dtype: int64



**MINI CHALLENGE #4 SOLUTION:** 
- **What is the size of the Pandas Series? (External Research is Required)**


```python
# size is used to return the size of the series
series_3.size
```




    5



**MINI CHALLENGE #5 SOLUTION:** 
- **Show the last 2 rows in the Pandas Series (External Research is Required)** 
- **How many bytes does this Pandas Series consume in memory? (External Research is Required)**


```python
my_series.tail(2)
```




    AAPL     400
    TSLA    2200
    dtype: int64




```python
my_series.memory_usage()
```




    156



**MINI CHALLENGE #6 SOLUTION:**
- **Set Squeeze = False and rerun the cell, what do you notice? Use Type to compare both outputs**


```python
sp500 = pd.read_csv('./sample_data/S_P500_Prices.csv')
sp500 = sp500.squeeze()
# Note that when you set Squeeze = False, the data is stored in a DataFrame by default. 
# DataFrame is simply used to store multi dimensional data as compares to Pandas Series that only holds 1-D dataset 
# Note that DataFrames has proper formatting when you attempt to view them as shown below 
# Note that Pandas Series has no formatting

```


```python
sp500
```




    0       1295.500000
    1       1289.089966
    2       1293.670044
    3       1308.040039
    4       1314.500000
               ...     
    2154    3327.770020
    2155    3349.159912
    2156    3351.280029
    2157    3360.469971
    2158    3333.689941
    Name: sp500, Length: 2159, dtype: float64




```python
type(sp500)
```




    pandas.core.series.Series




```python
sp500 = pd.read_csv('./sample_data/S_P500_Prices.csv')
type(sp500)
```




    pandas.core.frame.DataFrame



**MINI CHALLENGE #7 SOLUTION:**
- **Given the following Pandas Series, convert all positive values to negative using python built-in functions**
- **Obtain only unique values (ie: Remove duplicates) using python built-in functions**
- **my_series = pd.Series(data = [-10, 100, -30, 50, 100])**



```python
my_series = pd.Series(data = [-10, 100, -30, 50, 100])
my_series
```




    0    -10
    1    100
    2    -30
    3     50
    4    100
    dtype: int64




```python
abs(my_series)
```




    0     10
    1    100
    2     30
    3     50
    4    100
    dtype: int64




```python
set(my_series)
```




    {-30, -10, 50, 100}



**MINI CHALLENGE #8 SOLUTION:**
- **Sort the S&P500 values in a decending order instead. Make sure to update values in-memory.**


```python
sp500 = pd.read_csv('./sample_data/S_P500_Prices.csv')
sp500 = sp500.squeeze()
sp500
```




    0       1295.500000
    1       1289.089966
    2       1293.670044
    3       1308.040039
    4       1314.500000
               ...     
    2154    3327.770020
    2155    3349.159912
    2156    3351.280029
    2157    3360.469971
    2158    3333.689941
    Name: sp500, Length: 2159, dtype: float64




```python
sp500_2 = sp500.copy()
sp500_2.sort_values(ascending = False, inplace = True) 
sp500_2
```




    2037    3386.149902
    2035    3380.159912
    2033    3379.449951
    2034    3373.939941
    2038    3373.229980
               ...     
    2       1293.670044
    1       1289.089966
    99      1285.500000
    98      1278.180054
    97      1278.040039
    Name: sp500, Length: 2159, dtype: float64



**MINI CHALLENGE #9 SOLUTION:**
- **Obtain the average price using two different methods**


```python
# Obtain the average - Solution #1
sp500.sum()/sp500.count()
```




    2218.7495540592868




```python
# Obtain the average - Solution #s
sp500.mean()
```




    2218.7495540592868



**MINI CHALLENGE #10 SOLUTION:**
- **Check if the stock price 3349 exists in the sp500 Pandas Series or not**
- **Round stock prices to the nearest integer and check again**


```python
3349 in sp500.values
```




    False




```python
sp500 = round(sp500)
sp500
```




    0       1296.0
    1       1289.0
    2       1294.0
    3       1308.0
    4       1314.0
             ...  
    2154    3328.0
    2155    3349.0
    2156    3351.0
    2157    3360.0
    2158    3334.0
    Name: sp500, Length: 2159, dtype: float64




```python
3349 in sp500.values
```




    True



**MINI CHALLENGE #11 SOLUTION:**
- **Obtain the fifth element in the Pandas Series**


```python
# Note that the fifth element has an index = 4
sp500[4]
```




    1314.0



**MINI CHALLENGE #12 SOLUTION:**
- **Obtain all elements in Pandas Series except for the last 3 elements**


```python
sp500[:-3]
```




    0       1296.0
    1       1289.0
    2       1294.0
    3       1308.0
    4       1314.0
             ...  
    2151    3271.0
    2152    3295.0
    2153    3307.0
    2154    3328.0
    2155    3349.0
    Name: sp500, Length: 2156, dtype: float64




```python

```
