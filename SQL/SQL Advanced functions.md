### CTE Common Table Experessions

1- it is executed once 
2- it is stored in memeory 
3- improve the organization of the data
4- you can use it more than one time and it is most important feature 

اهم ميزة انك تقدر تستخدمها اكثر من مره فى الكويري  


### WINDOW FUNCTIONS

     1- you can use it without using group by 
     2- you can use it with aggregates instead of the using (subqueries with select) like 
         (AVG(m.home_goal + m.away_goal) OVER() AS overall_avg
         
     3- using for the ranking the rows ( Rank - and Dense Rank ) 
         RANK() OVER(ORDER BY AVG(m.home_goal + m.away_goal)) AS league_rank
هنا الفكرة انك ممكن ترتب القيم الى انت محتاجها اكير لاصغر 

     4- using partition by ( to calculate the aggregate function ) 
هنااحنا ممكن نستخدم التجميع عشان نحصل على المتوسط لكل مجموعه مش للعمود كله 

     5- using window function to calculate the running totals or sums or avgs or choose some rows you need 
     
     6- using the window function to calculate comulating functions 
        Ex : AVG(home_goal) OVER(ORDER BY date ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS running_avg

     7- ROW_NUMBER() OVER() 
          ROW_NUMBER() OVER() AS Row_N دا عشان نعمل صف يحدد فيه الترتيب 
          ROW_NUMBER() OVER (ORDER BY year DESC) AS Row_N   ودا عشان لو محتاجين نرتب الصفوف معها 

     8- LAG(column, number_of_lags )
        Fetch the previous year champion
            LAG(Champion,1) OVER ()
            
     9- LEAD(column, number_of_leads)
     10- FIRST_VALUE(column)
     11- LAST_VALUE(column) 
الفكرة هنا ان انا هستخدم عدد من الصفوف فى فوق باستخدم التأخير او ممكن استخدم عدد من الصفوف الى تحت باستخدام التقديم 

     12- row BETWEEN UNBOUNDED PRECEDING AND  UNBOUNDED FOLLOWING 
     - row between is normal when we use it , but the range between consider the duplicate rows as a single row.

     13- you can use partion by with LAG() , LEAD(), ROW_NUMBER(), RANK()

#### Paging 
- use to split the table to many pages because some applications need that like API when return a big data from the web , it divides them to pages 
        NTILE(111) OVER (ORDER BY Event ASC) AS Page // divide it to 111 pages 
- بيستخدم لو انا عايز اعرف متوسط كل مجموعه المجموعه الاولى والخيره مثلا عشان اعرف هل دا هيفرق ولا لا 

      - Group By Geneder , Rollup (medal ) بستخدمها لما ابق عايز مجموع المديلايات  الى موجوده مع كل جنس 
      - Group BY Gender , Rollup (Gender , medals ) ودا نفس القيمة الى فوق لام انت هتجيب مجموع للجنس وانت كده كده جبته 
      - Group by cube( Gender, Medels) وهى بتستخدم فى العواميد الفرعية زى هنا هيحصل على مجموع كل نوع ميدليه ولوحها زى الدهب او الفضة 



### CASE_Function

CASE with select -- use to create column with condition 
- use case with select when you need to compare between two columns and create a new column 
- نقدر نستخدم بعد كده دوال الجمع او المتوسط معها فى نفس السطر زى الاتى 
Count( CASE WHEN ....) لما تبق عايز تعد عمود بس بشرط تحقق فى عمود تانى 
- انت ممكن تستخدمها فى فكرة تانيه هى ان عايز اجمع او اجيب المتوسط لعمود بشرط محقق فى عمود تانى 
مثلا يعنى عايز اجيب عدد مرات فوز فريق معين وانا معنديش عمود اقدر اجمع صفوفه او اعده عشان اعرف هو الفريق دا فاز كام مرة فانا ممكن مع تحقيق شرط معين اكتب وقم واحد 
ولو متحققش اكتب صفر وبعد كده اجمع الواحد والى بيمثل عدد مرات الفوز او حتى الحصول على المتوسط  

- بستخدمها برده لما اكون عايز اغير قيم عمود معين فأكون عمود تانى بالشرط الجديد 


### Working_with_Pivot_table 

SELECT * FROM (
    SELECT Gender , Home_owner , purchased_Bike
FROM  `future-producer-337010.Sales_DashBoard.Bike Sales `)
pivot(
    count(purchased_Bike) 
    for Home_owner in (True as rich , False as poor )
)



### working_with_ String

  #### Discovering 
  ```
    - LEN FUNCTION 
    - CHARINDEX('t', 'Customer')  -- Search for "t" in string "Customer", and return position
    - CHARINDEX(substring, string, start) , SELECT CHARINDEX('mer', 'Customer', 3) -- Search for "mer" in string "Customer", and return position (start in position 3)
    -  POISTION('a' in email ) 
    -  STRPOS(email ,'a')
    - to_tsvector(title) @@ to_tsquary('elf'); is to search for elf in full sentence 
```


  #### EXTRACT WORDS
```
    - LEFT FUNCTION LEFT(column , 23)
    - RIGHT FUNCTION RIGHT(column, 23)
    - SUBSTRING(string, start, length)      Example SUBSTRING('SQL Tutorial', 1, 3)  result = SQL
    - SUBSTRING(column from 0 for 10 )
```

 
  #### Modifying and changing words 
  ```
   - UPPER(     ) 
   - LOWER(      ) 
   - INITCAP(     )
   - TRIM('     SQL Tutorial!     ') RESULT = SQL Tutorial! 
   - TRIM('#! ' FROM '    #SQL Tutorial!  )  RESULT =  SQL Tutorial'
   - LTRIM('  PADD  ') OR RTRIM('  PAAA  ') 
   - LPAD('PADD', 10) RESULT = (     PADD) 

   - concat('apples', 'and' , 'oranges')        results 'applesandoranges'
   - concat_ws(' ' , 'apples', 'and', 'oranges')   results 'apples and oranges' 
   - concat_ws('***' , 'apples', 'and', 'oranges')   results 'apples***and**oranges' 
   - CONCAT('W3Schools', '.com') ,  CONCAT('SQL', ' is', ' fun!') , 'W3Schools' + '.com' ,, first_name || '' || second_name to concatnate two string
   - CONCAT_WS(separator, string1, string2, ...., string_n) , CONCAT_WS('.', 'www', 'W3Schools', 'com')
   - string_AGG(Country, ' ,')  RESULT =  (EGY, RSU, USA) بيحوله الى EGY , RSU , USA
   - REPLACE(column, 'what you want to change' , 'the change you need') as
   - REVERSE() need to reverse the function 
   - LPAD('PADD',10,##) means to complete the word padd until make the total no.character equal 10 (result ######PADD)
 ```
   
### WORKING_WITH_NUMBER
```
   - ABS(NUMBER) 
   - SIGN (   ) 
   - SQRT( 9 ) RESULT 3 
   - SQUARE(9) RESULT 81 , LOG( NUMBER , BASE_NUMBER) 
   - ROUND(12.33 , 0) RESULT 12.00 
   - ROUND(12.32 , 1) RESULT 12.30 
   - ROUND(12.34, -1) RESULT 10.00 
   - Round(124.23, -2) RESULT 100.00 
   - ROUND(12.23, 0 ,1) RESULT 12 دا معناها اقتطاع مش تقريب عشان كده انا باخد الرقم 12 واحطه من غير تقريب 
   - ROUND(12.77, 0 ,1) RESULT 12 نفس فكرة الاقتطاع 
   - ceiling(column) 
   - floor (column) 
   - Power(column, 2) 
   - count(distinct   ) 
   - sum(distinct     ) sum only the unique values 
   - min(distinct    )  
```

The functions of the statistics 
AVG() - STDEV() - STDEVP() - VAR() - VARP()
