# Pandas 🐼

## Import the Dataset

```python
path = "./data/file.csv"

df = pd.DataFrame(student_dict)     # From Dict
df = pd.read_csv(path)              # From File
df = pd.ExcelFile('file.xls')       # From Excel
df = pd.read_excel(xlsx, 'Sheet1')

# Column to series
ser = df.ix[:,0]
```

---
#### Splitting Features and Dependent Variable
```python
# Separating Variables by position
X = df.iloc[:, :-1].values     # Matrix of Features
y = df.iloc[:, -1].values      # Dependent Variable

# Separating Variables by column-name
features = ["A", "B", "C", "D"]
X = df[features]
y = df["E"]
```

---
## 2) Data Exploration
Profile-Report 🐼
```python
from ydata_profiling import ProfileReport

profile = ProfileReport(df, title="Pandas Profiling Report")
profile.to_file("eda_df.html")
```

```python
df.info()
df.describe().T

df.head()       # df.tail()
df.shape()

df.dtypes.value_counts()
df['Colum_Name'].value_counts()   # Count unique value-occurences

df.nunique()         # Check for unique values
df.isna().sum()      # Check for null values

df.mean().sort_values() # Mean per column
df.max().sort_values()  # Max per column
```

---
## Selecting Data
```python
# Select data
df.columns
df["value"]                   # Select columns
df.loc[10]                    # Show complete Row 10

# Filter for Values
women = df.loc[df.Sex == 'female']["Survived"]  # [Filter row][Select column]
rate = sum(women)/len(women)  # Calculate ratio

# Filter data
df[df["column"] >= 1000]      # Select data by filter
df.query("colum" >= 1000)     
df["value"].max()             # Highest value in column
df["value"].idxmax()          # Id of highest value in column
df.sort_values("column", ascending=False) # Sort values in column

# Datetime Manipulation: Change Time Interval
df.resample('D').size() # Numbers of days the data was collected
df.resample('W').size() # Numbers of weeks the data was collected
```

---
## 3) Cleaning Data

#### Modifying features
```python
# ---------------------------------------------------------*/
# Modifying Features
# ---------------------------------------------------------*/
# Change datatype, coerce = "invalid parsing will be set as NaN"
df['column']= pd.to_numeric(df['column'], errors='coerce')

# Change number to datetime
df['column'] = pd.to_datetime(df.column.astype(str), format ='%Y%m%d%H%M%S%f')

# Set the index of the dataframe
df = df.set_index('column')
```

---
## Plotting (--> see Matplotlib)
```python
# ---------------------------------------------------------*/
# Plotting the data
# ---------------------------------------------------------*/
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(10, 5))     # Define Size
ax.set_xlabel('Days')                       # Define Labels
ax.set_ylabel('Value')

# Plotting
df.plot.hist()
df.plot.scatter(x='w',y='h')
df.plot(title='Plot', ax=ax, label = 'counts', legend = True)

plt.show(plt)
```

---
### Exporting

```python
# CSV
df.to_csv('name.csv', encoding='utf-8')

# Excel
from pandas import ExcelWriter
writer = ExcelWriter('filename.xlsx')
df1.to_excel(writer,'Sheet1')
df2.to_excel(writer,'Sheet2')
writer.save()

# MySQL
import pymysql
from sqlalchemy import create_engine
e = create_engine('mysql+pymysql://' +
	'USER:PASSWORD@HOST/DATABASE')
df.to_sql('TABLE',e, if_exists='replace')

# Python object
d = df.to_dict() # to dictionary
str = df.to_string() # to string
m = df.as_matrix() # to numpy matrix
```

---
