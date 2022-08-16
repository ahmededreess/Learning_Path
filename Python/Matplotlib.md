### Bar Chart 

``` 






```


### Pie Chart 

```
slices = [59219, 55466, 47544, 36443]
labels = ['JavaScript', 'HTML/CSS', 'SQL', 'Python']
explode = [0,0 , 0.1,0]
colors = ["red", "white", "blue", "yellow"]

plt.pie(slices)                                         // to draw without labels 
plt.pie(slices , labels = labels                        // to draw the labels 
, wedgeprops = {"edgecolor":"black"}                    // to draw edge with black color 
, explode = explode                                     //  to apear part of the pie chart 
, colors = colors                                       //  to change the color 
, shadow = True                                         //  to draw the shadow 
, autopct = "%1.1f%%"                                   // to appear the percentage of each item on the chart )

```
### filling the area under the line 
 ``` 
 plt.fill_between(ages, py_salaries, dev_salaries,
                 where=(py_salaries > dev_salaries),
                 interpolate=True, alpha=0.25, label='Above Avg')
                 
 ```
 
 ### Histogram
 ``` 
 plt.hist(ages, bins=bins, edgecolor='black', log=True)
 
 ```
 ### Scatter Diagram
 ```
 
 
