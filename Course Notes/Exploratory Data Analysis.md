# Exploratory Data Analysis in Python

## Common Methods

`df.head()`

`df.info()`

`df.value_counts('col_name')`

`df.describe()`

`sns.histplot(data=df, x='col_name', binwidth=.1)`

## dtypes Casting

`df.dtypes`

`df['colname'] = df['colname'].astype('str')`

| Type | Python Name |
| ---- | ----------- |
|String	  |`str`|
|Integer  |`int`		|
|Float	  |`float`|
|Dictionary|`dict`|
|List|`list`|
|Boolean|`bool`|



`df['colname'].isin(['val_a', 'val_b','...'])`returns a bool list with whether is in the given list or not

`df.select_dtypes('number')` use the method to subset the df with columns of the 'number' type

`df['colname'].min()` gives the min value

`df['colname'].max()` gives the max value



`sns.boxplot(data=df,x='year',y='genre')` gives a plot with horizontal boxes for each 'genre'

