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
 
 
 ###  Seaborn 
 ```
 df = pd.read_csv(csv_filepath)
 sns.countplot(x="Spiders", data=df)
 plt.show()
 
 tips = sns.load_dateset("tips")
sns.scatterplot(x = "total_bills",y = "tip", data = tips, hue = "somker" ) // classify who is smoker or not 
sns.scatterplot(x = "total_bills",y = "tip", data = tips, hue = "somker", hue_order =["yes",'no'] ) 

hue_color = {'yes':'blue' , 'NO':'red'} 
sns.scatterplot(x = "total_bills",y = "tip", data = tips, hue = "somker", palette = hue_colors )

sns.relplot(x = 'total_bills', y='tips', data= tips,kind= 'scatter' , col = 'somker') // two columns in your graph 
sns.relplot(x = 'total_bills', y='tips', data= tips,kind= 'scatter' , row = 'somker') // two rows in your graph
sns.relplot(x="G1", y="G3", 
            data=student_data,
            kind="scatter",
            col = 'schoolsup', col_order=['yes','no'])
 ```
 
 ### Customizing scatter plots
```

sns.relplot(x = 'total_bills', y='tips', data= tips,kind= 'scatter' , size = 'somker', hue ='smoker') 
// to classify with the size and each size with the color 
sns.relplot(x = 'total_bills', y='tips', data= tips,kind= 'scatter' , size = 'somker', style ='size') 
// to classify with the size but to change the style of each size 
sns.relplot(x = 'total_bills', y='tips', data= tips,kind= 'scatter' , alpha ='size') 
sns.relplot(x= 'acceleration', y = 'mpg', data = mpg , kind = 'scatter',hue = 'origin', style= 'origin' )

sns.catplot( x= 'Gender',y = 'Interested in Math', kind= 'bar', data= survey_data) // for bar chart 

category_order = ["<2 hours", "2 to 5 hours", "5 to 10 hours", ">10 hours"]
```
### Turn off the confidence intervals

```
sns.catplot(x="study_time", y="G3",data=student_data, kind="bar", order=category_order, ci = None)

sns.catplot(x="study_time", y="G3", data=student_data, kind="box", order=study_time_order)

sns.catplot(x= 'internet',y = 'G3', kind = 'box', data = student_data, hue = 'location', sym = '') // sym means don't display the outlier 
sns.catplot(x="romantic", y="G3", data=student_data, kind="box", whis=[5, 95]) // means to draw the box plot included the outlier 

```

point plot 
sns.catplot(x="famrel", y="absences", data=student_data, kind="point", capsize=0.2, join = False, estimator = mediam ))
// capsize is the shape of I in the graph , join means to  not join each point with the other 


### Changing plot style and color

we have five different styles of the plot (white , dark , whitegrid , darkgrid, ticks ) // default white 

sns.set_style('dark' )
sns.set_palette("RdBu') // means the divergance of the color and sequential patette and you can create your own patette 
sns.set_context('paper', 'notebook','talk', 'poster') // change the scale of the plot and elements and labels 

there are two types of the plots in the seaborn 
object type ( facetGrid or AxesSubplot ) 
FacetGrid (relplot, catplot )  // you can create more than plots 
AxesSubplot(scatterplot, countplot),etc ) // you can create only one plot

g= sns.catplot( x= '', y ='' , kind = '' , data = '') 
g.fig.suptitle("new titlle", y = 1.3 ) // y means to be the title more higher than 1 
----------------------------------------
if you have two graphs and need two titles 
g.figsuptitle('main title')
g.set_title('this is {col_name}' 
g.set(xlabel =' ' , ylabel ='')
plt.xticks(rotation = 90)

 
