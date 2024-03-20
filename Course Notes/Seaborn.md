# Introduction to Seaborn
## Main setup

```python
import seaborn as sns
import matplotlib.pyplot as plt
# optional
import pandas as pd
```
## Simple Plots
```python
# Scatterplot
hue_dict={'colnames':'colors'}
sns.scatterplot(x='col_name or series', 
				y='col_name or series',
				data=df #in case df, not used if series in x,y
				hue='col_name or series',
				hue_order = [colnames_list],
				palette=hue_dict)
```

```python
# Countplot
sns.countplot(x='colname or series',
			 data=df)
```


## Relational Plots
```python
## load some data to a df
sns.replot(x='x-axis',
		   y='y-axis'
		   kind='scatter',
		   col='', # label column that will generate plots column-wise
		   row='', # label column that will generate plots row-wise
		   col_wrap=, # how many columns of plots
		   row_wrap=, # how many rows of plots
		   col_order=[],
		   size='', # colname 
		   hue='', # colname
		   style='' # colname
		   alpha= # 0 to 1
		   )
sns.scatterplot		
```
In `kind = 'line'`:
- `style='colname' `creates a different line for each label on the colname
- `hue='colname'` assigns different colors to each line for the labels in colname
- `marker=bool` adds markers for each data point
- `dashes=bool` indicates dashed or solid line
- `ci='stats_type'` If different values are present in the dataset for the same x, by default it aggregates them and shows the mean as a solid line and 95% confidence intervals as shaded regions. Can use other stats like `'sd'`.

Here the param col and row indicates which column will be use to generate separated plots in a col-ordered manner. The same applies to rows. Can be use together.

col_wrap is used to indicate how many plots will be showed on each column

## Categorical Plots
### Count Plots
```Python
sns.catplot(x='some categorical variable',
		   data=df
		   kind='count')
```
Can make the plot horizontal by switching the parameter x->y. Parameters like `col=` can be used here too.

### Bar Plots
```Python
sns.catplot(x='some categorical variable',
			y='quantitative_variable_to_sumarise',
		   data=df,
		   kind='bar'
		   order=[]
		   ci='')  # some stat or None
```
### Box Plot (Whiskers)
```Python
sns.catplot(x='some categorical variable',
			y='quantitative_variable_to_sumarise',
		   data=df,
		   kind='box'
		   sym='' # Empty for no outliers
		   whis= #footnote
		   )  # some stat or None
```
In the `whis` parameter, if nothing is specified, then the whiskers extend to 1.5* Interquartile range, eg:
- `whis=2.0` makes it 2.0 * IQR
- `whis=[5,95]`  shows the 5th and 95th percentiles 
- `whis=[0,100]` shows the min and max values

### Point Plots

```python
sns.catplot(x='some categorical variable',
			y='quantitative_variable_to_sumarise',
		    data=df,
		    kind='point',
            join=bool, # if the points are joined by a line
            estimator=func, #or any estimator like np.median
            capsize= # size of the cap from 0 to 1?
		   )  # some stat or None 
```

## Customization

### sns.set_style()

- `whitegrid`adds a horizontal line gray grid
- `ticks`adds ticks to the x-y axes
- `darkgrid`gray background and white grid

### sns.set_palette()

- Diverging palettes for extreme values that represent opposites and a neutral middle point, e.g. `RdBu`,`PRGn`, ...

- Sequential palettes are same colors but varying on intensity, e.g. `Greys`, `Blues`, `PuRd`, `GnBu`.
- Custom palettes `['red', 'green', 'orange', ... ]`and used like `sns.set_palette(custom_palette)`.(can also use hex-color codes like `#FBB4AE`)

### sns.set_context()

Sets the scales: 'paper', 'notebook', 'talk', 'poster'



### Titles 

an object `g = sns.scatterplot(x,y,data)`can be

- AxesSubplot: the regular plot &rarr; `relplot()`and `catplot()` &rarr; Can create subplots
- FacetGrid: a collection of AxesSubplots &rarr;  `scatterplot()`and `countplot()`&rarr; creates single plot

#### On FacetGrid

`g.fig.suptitle('New Title', y=1.3)`sets the whole grit title and `y` upwards offset

`g.set_titles('This is {col_name}')`sets the title of individual subplots 

#### On AxesSubplot

`g.set_title('New Title', y = 1.03)`

### Labels

`g.set(xlabel='New X Label', ylabel='New Y label')`sets the names of the labels in both _FacetGrid_ and _AxesSubplot_.

`plt.xticks(rotation=90)`rotates the ticks labels. Note it is not a function of the **seaborn** object, but of **mathplotlib**.

