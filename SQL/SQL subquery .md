### Subquery 

  ####  subquery with select 
  
    1. you can use it if you will perform complex calculation. 
    2- if you need a value to compare it with other values like average or the maximun value.
زى فكرة ان انا اجيب المتوسط فى عمود مع القيمة عشان اشوف الفرق
او زى ان يكون فى عملية حسابية معقده زى مثلا عملية طرح بين القيمة ومتوسط القيم ساعتها ممكن اسنخدمها


   #### subquery with from
   
     1. to restructure and transform your data ( when you find the query complex, try to restructure the table first then use from (select...) to get your request.
     2- using to prefiltering ( if you need to filter the table first get the value you need. 
     
المقصد هنا اننا مش محتاجين قيمة او عمود زى الاستخدام بتاع الكويرى مع الوير ..انما هنا انا بحتاج معلومات من اكثر من عمود
او ان افلتر على حاجة الاول وبعد كده اغيرها فى الطلب الاساسي 

وكمان ممكن تستخدم داخل التداخل المشترك 
       INNER Join ( Select ......)
       
       
#### subquery with where 
   
     1. to use it when you need a value like max or min or averge to filter by using it 
     2- now you need not only the value but you may need a column or filtered table to compare a column with it 
    
                                                                                                                                    يبق ملخص استخدمها كامثلة :
                                                                                                     1- لوانا عايز القيم الاكبر من المتوسط مثلا وساعتها هستخدم     
            where country_income > ( select avg(....)........)
                                                         2- لو انا عايز ادور عمود بس بشرط موجود فى جدول تانى والعمود دا مشترك بين الجدولين وساعتها هتسخدم 
         where country_id in ( Select .......)

 
