## Import & Create

import pandas as pd

From dictionary
data = {"name": ["A","B","C"], "age": [23,25,29]}
df = pd.DataFrame(data)

From CSV / Excel
df = pd.read_csv("file.csv")
df = pd.read_excel("file.xlsx", sheet_name="Sheet1")

Save
df.to_csv("out.csv", index=False)
df.to_excel("out.xlsx", index=False)


## Inspect Data
df.head()        # first 5 rows
df.tail()        # last 5 rows
df.shape         # (rows, cols)
df.info()        # column info
df.describe()    # summary stats
df.dtypes        # data types
df.columns       # column names
df.index         # row index


## Select Data
Single column
df['name']
df.name

Multiple columns
df[['name', 'age']]

By position
df.iloc[0]          # first row
df.iloc[0:3, 0:2]   # rows 0-2, cols 0-1

By label
df.loc[0, 'name']        # row 0, col 'name'
df.loc[0:2, ['name']]    # rows 0-2, col 'name'


## Filter / Query
df[df['age'] > 25]

df[(df['age'] > 20) & (df['name'] == "A")]

df.query("age > 20 and name == 'A'")


## Add / Modify Columns
df['salary'] = [100, 200, 300]
df['double_age'] = df['age'] * 2
df.rename(columns={'age':'years'}, inplace=True)


## Drop
df.drop('salary', axis=1, inplace=True)   # drop column
df.drop(0, axis=0, inplace=True)          # drop row


## Missing Data
df.isnull().sum()
df.fillna(0, inplace=True)
df.dropna(inplace=True)


## Sorting
df.sort_values('age', ascending=False)
df.sort_index()


## GroupBy & Aggregation
df.groupby('name')['age'].mean()
df.groupby('name').agg({'age':'mean', 'salary':'sum'})

Pivot Table
df.pivot_table(index='name', columns='dept', values='salary', aggfunc='mean')


## Merge & Join
pd.merge(df1, df2, on='id')                 # inner join
pd.merge(df1, df2, on='id', how='left')     # left join
pd.concat([df1, df2], axis=0)               # stack rows
pd.concat([df1, df2], axis=1)               # stack cols


## Apply & Map
df['age'].apply(lambda x: x*2)
df['name'].map(str.upper)
df.applymap(lambda x: str(x).upper())   # entire DF


## Value Counts & Unique
df['name'].value_counts()
df['name'].nunique()
df['name'].unique()


## String Ops
df['name'].str.upper()
df['name'].str.contains("A")
df['name'].str.replace("A","Z")


## Datetime
df['date'] = pd.to_datetime(df['date'])
df['year'] = df['date'].dt.year
df['month'] = df['date'].dt.month
df['weekday'] = df['date'].dt.day_name()


## Export
df.to_csv("clean.csv", index=False)
df.to_excel("clean.xlsx", index=False)
df.to_json("clean.json")


## Pro Tip: Always prefer vectorized operations (df['col']*2) over loops — they’re faster and cleaner.
