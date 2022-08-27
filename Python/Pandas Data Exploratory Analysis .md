### We will explore the data and discovering some information from the data.
     
   ### functions for Exploring the data
   
   ```
   
   data.head()
   data.shape
   data.index
   data.columns
   data.dtypes
   data.info()
   data["driver_age"].describe()
   data.dtypes
   
   data["Weather"].unique()                                            // to get the total number of unique values from the column  
   data.nunique()                                                      // to get total numbers of unique values in each column 
   data.count()                                                        // to count all values in each column 
   data["Weather"].count()                                             // to count the values of the column 
   data["Weather"].value_counts()                                      // to count the total number of each value in the column
   len(data[data["Weather"] == "Clear"])                                
   data.groupby('Weather').get_group('Clear')
   len(data[data['Wind Speed_km/h'] == 4])
   
   data.isnull()
   data.isnull().sum()
   data.notnull().sum()
   data["Cylinders"].fillna(data["Cylinders"].mean(), inplace = True)  ## to fill the null values 
   
   data["Visibility_km"].mean()
   data.groupby("Weather").mean()
   data["Press_kPa"].std()
   data.Press_kPa.var()
   
   ```
   ### creating new columns 
   ```
   data["Children_1"] = [i*2 if i > 10 else i*3 for i in data.children] 
   
   data["Age_type"] = ["young_man" if i < 25 else "Man" if i > 40 else "Old" for i in data.age ]
   
   
   
   def condition(table):
    if table["product_name"] == "sushi":
        value = table["price"] * 20
    else:
        value = table["price"] * 10
    return value

   sales_menu["points"] = sales_menu.apply(condition, axis = 1)
   
   
   
   
   data.loc[data.gender == "Female", "Female_type"] = "yes"
   data.loc[data.gender != "Female", "Female_type"] = "No" 
   
   data["price_Doll"] = cars["price"] * 18
   data.date = pd.to_datetime(data.date)
   data["year"] = data.date.dt.year 
   
   
   
   data[~(data["Weight"] > 4000)]                                   ## is to remove all values are greater than 4000 
   data["MPG_Highway"] = data["MPG_Highway"].apply(lambda x:x+3)    ## to change the values of the columns
   data_1.insert( 2 , "year", data_1.date.dt.month ) // to create new column contains only one year
   
   data["status_gender"] = data["marriedarital_status"] + ' ' + data["gender"] 
   data[["status", "Gender"]] = data["status_gender"].str.split(" ",expand = True) 
   
   ``` 
   ### updating columns 
   
   ```
   data["children"] = data["children"].apply(lambda x:x+2)
   data["gender"] = data["gender"].apply(lambda z : z.upper())
   
   def upper_email(email) :
    return email.lower()
   data["gender"] = data["gender"].apply(upper_email)
   
   data.rename(columns = {"Weather": "Weather Condition"})
   data.drop(columns = "Origin")
   data.drop_duplicates(subset = "name")
   
   data.loc[0 ,["id","marriedarital_status"]] = ["111", "Single"]
   data.loc[0 , "id"] = "111"                                           // to change one value in the column 
   data["occupation"] = data["occupation"].str.lower()
   
   data["gender"].replace({"female ": "F"}, inplace = True)
   
   data.drop(index = 999)
   data.drop(index = data[data["gender"] == "F"].index, inplace = True)
   
   cars["Cylinders"] = cars["Cylinders"].astype("int")  
   
   
   ```
   
   ### functions for sorting and subsitting 
   
   ```
   cars.sort_values("mode")
   cars.sort_values("mode" , ascending = False )
   cars.sort_values(["mode" , "color"])
   
   cars[cars["mode"] == "toyota"]
   cars[(cond_1 = cars["mode"] == "toyota") & (cond_2 = cars["color"] == "green")] 
   data[(data["Weather"] == "Clear") | (data["Visibility_km"] > 40) ] 
   cars["color"].isin(["blue","black"])
   ```
   ### Slicing  
   
   ```
   data.loc[0] 
   
   
   
   ```
   ### Indexing 
   
   ```
   data.style.hide_index()
   data.style.set_caption("title for the tabel")
   data.set_index("name")
   data.reset_index()
   
   ```
   ### aggregating dataframe
   ```
   cars["hight"].mean() 
   cars["hight"].median()
   cars["hight"].mode()
   cars["hight"].std()
   cars["hight"].var()
   cars["hight"].min()
   cars["hight"].max()
   cars["hight"].sum()
   cars["hight"].quatile()
   cars["hight"].cumsum()
   cars["hight"].cummax()
   cars["hight"].cummin()
   cars["hight"].cumprod()
   
  ```
   ###  Grouping
   
   ```
   data.groupby("Region").sum()
   data.groupby("Region").sum().head(20)
   data.groupby("Region")["Confirmed"].sum()
   data.groupby("Region")["Confirmed"].sum().sort_values(ascending = False)
   
   data.groupby("Region").Deaths.sum().sort_values(ascending = True).head(40)
   data.groupby("Region")["Confirmed"].sum().sort_values(ascending = False)
   
   data.groupby("driver_gender").search_conducted.sum()
   data[police["violation"] == "Speeding"].driver_gender.value_counts()
   
   data["Region"].value_counts(normalize = True)
   
   ```
   
  ### Missing Values 
  
  ```
  data.dropna()                                                 // to remove the columns which has all non values 
  data.dropna()                                                // how is any or all ? 
  police.replace("NA", np.nan, inplace= True)                 
  police.drop(axis ="index", subset = ["country_name"])              
  
  
 ```
 ### datetime 
 ```
 covid["Date"] = pd.to_datetime(covid["Date"], format = "%Y")
 covid.loc[0, "Date"].day_name() 
 covid["Date"].dt.day_name() 
 
 covid["Date"].min() , covid["Date"].max ,  covid["Date"].max() - covid["Date"].min()
 covid[covid["Date"] >= "2020" ]                           // all data after 2020
 covid[covid["Date"] >= pd.datetime("1-9-2020")
 covid["Date"].set_index()
 covid["2019"]
 
 covid["2-2019":"3-2020"]["Confirmed"].mean()
 covid["Confirmed"].resample("D").max()             // means to get the maximun number each day for the confirmed number
 covid.resample("W").mean()                        // means to get the mean for all values each weak you have in your data
 covid.resample("W").agg({"confirmed":"max" , "Death":"mean"})
```
### Converting to other data types
```
covid.to_csv("  ")
covid.to_excel("  ")
covid.to_json("  ") 
covid.to_sql("   ")

excel = pd.read_excel("   ") 
json = pd.read_json("   ")

```  
### datetime functions 

```
d_parser = lambda x: pd.datetime.strptime(x, '%Y-%m-%d %I-%p')
df = pd.read_csv('ETH_1h.csv', parse_dates=['Date'], date_parser=d_parser)

df['Date'].dt.day_name()
df['DayOfWeek'] = df['Date'].dt.day_name()


df.set_index('Date', inplace=True)
df['2019']
df['2020-01':'2020-02']
df['2020-01':'2020-02']['Close'].mean()
df['2020-01-01']['High'].max()
highs = df['High'].resample('D').max()

df['Close'].resample('M').mean().head()
df['Close'].resample('M').mean().plot(kind='bar')

df.resample('W').mean()
df.resample('W').agg({'Close': 'mean', 'High': 'max', 'Low': 'min', 'Volume': 'sum'})

rng = pd.date_range(start="6/1/2016",end="6/30/2016",freq='B')
rng = pd.date_range('1/1/2011', periods=72, freq='H')

daily_index.difference(df.index)   // to compare between two dataframes.dates 
df.asfreq('D',method='pad')

from datetime import timedelta
sales_menu_members["after_week"] = sales_menu_members["join_date"] + timedelta(days = 7)

df.shift(1) 

```
### Replacing function with many values 

https://pythonguides.com/pandas-replace-multiple-values/

