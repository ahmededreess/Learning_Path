### Sorting 

ORDER BY -- to order the column 
ORDER BY .... DESC 
ORDER BY ...... , ........
GROUP BY .... -- you'll need to aggregate results. For example,
              --  you might want to count the number of male and female employees in your company
              -- Commonly, GROUP BY is used with aggregate functions like COUNT() or MAX(). Note that GROUP BY always goes after the FROM clause

### Filtering 

WHERE with OR , AND 
WHERE with BETWEEN    ,      
WHERE .... IN (  ,   ,   ,   ) 
WHERE .... IS NULL 
WHERE .... IS NOT NULL 
WHERE .... LIKE 'A%' first latter or '_r%' second latter or '%A' last latter or 'M%esia' start with M and end with esia
WHERE .... NOT LIKE 
HAVING count(...) 


### Joining 

INNER JOIN 
Select ......, ......, ......,  -- you will choose the columns you need from two or three tables 
FROM left table                 -- left table 
INNER JOIN right table          -- right table 
  ON left table.common_column = right table.common_column   --- connect to the common column between two twbles 
  ON left table. common_column = third table.common_column  -- if we will use the third table to pick columns from them 

inner join ... يبق انت هتجيب المشترك بس بين الى الجداول 

left join ... هتجيب كل الى موجود فى الجدول الشمال 

right join ... هنجيب كل الى موجود فى الجدول اليمين 

full join ... هنجيب كل المتغيرات فى الجدولين اليمين والشمال 

cross join ... كل قيمة فى اليمين هتتحط مع كل قيمة فى الشمال 

semi join ...  بتستخدم لو انا عايز القيم الى فى الجدول الشمال الى موجوده فى اليمين بس من غير ما احتاج حاجه من الجدول اليمين بس طبعا البيانات المشتركة الى ما بينهم 
             وهنا ممكن يكون عايز البيانات الى موجوده فى الجدول الشمال بس بشرط موجود فى الجدول اليمين ساعتها بستخدم الربط المشترك ومعه الفلتر 


Anti join ... انا محتاج البيانات الى موجوده فى الجدول الشمال ومش موجوده فى الجدول اليمين
Anti join ... فكرة ان انا ممكن استخدم المشترك الشمال عادى وافلتر على القيم الفارغه ساعتها هيختار القيم برده الى موجوده فى الجدول الشمال الى مش موجوده فى اليمين
            

Self Join .... تستخدم لما تكون عايز تقارن قيمتين فى عمود واحد يعنى مثلا عايو  تقارن بين موظفين فى نفس المدينة وتحسبلهم الفرق ما بينهم مثلا 
                 او لو مثلا فى بيانات موجوده فى عمود وموجوده برده فى عمود تانى ... مثلا رقم الموظف وارتباطه برقم المدير والمدير دا هو نفسه موظف 

