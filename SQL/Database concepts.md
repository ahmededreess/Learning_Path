### Definitions 

1- Datebase is the place to store the date ( huge data) to make the CRUD operation ( create - read - update - delete )
2- databasemanagement is software to help me to manage the data ( store the data - help me in queries ) 

advantages of the database management system 
 1-

 ### How to design database ? 
 
three steps to create database

1- conceptual data model : هو انك تجمع المتطلبات وتبدا تجمعها فى رسمه  
     - convert tاث requirements to ERM (entities relationships model )
     to convert the requirements to ERM model follow the following :
        1- draw the entities and then the attributies then the relationships 
   
            properities of the entitiy :
                1- degree ( unary - binary - trenery - quarterary ) ( no of tables) 
                2- cordinalary ( one to one - one to many - many to many ) between the columns in each table ( وبرمز ليها بالسهم ) 
                3- participation ( total - partial ) وبيرمز بها بخطين ودا معناها هل كل الطلاب ليهم كورسات ولا ممكن طلب ميكنش ليه اى كورس والعكس 
                     week entity which doesn't have the primary key زى البيانات الخاصة بموظف اسماء ولاده وزوجته 

           properities of the attributies :  
               1- simple & composite (like the name contains to attributies first_name & last_name ) ودا بيتعامل كجدول لوحده 
               2- single values & multivalue (like the phone_number I may have two numbers) 
               3- Derived (computed) like the age you can get it from the birthdate (we draw it as a dots ) مش بيتعمله عمود اصلا ولو احتاجته بعمل عملية فى الطلب 


2- logical data model 
     - convert the ERM to schemas وفيها بنقوم بتحويل الرسمه الى جداول وبناخد في الحسبان ال PRIMERY KEY AND FOREIGN KEY.
                                                                                             -- وكمان بنبدأ نستخدم عملية NORMALLIZATION TO START CREATE THE TABLES 
              you will start to convert the ERM to schemas and write their attributities. 

     - when the relationship is one to one you can use the foreign key to put it with the other entity (but try use the total )
         dependence ( ex: chair table and student table the relationship is one to one means each student has chair 
                      and chair has only one student but you may find chairs without student so the best way is to 
                      put the foreign key in the student chair during the creation 
     - when the relationship is one to many we put the foreign key in the many table. 
     - when the relationship is many to many , no problem to put foreign key on any table or to create table to the foreign keys only 
                              then we talk about the normalization 
                                       1- 1NF is to delete the repeated groups ,,,, 
                                       2- 2NF is to delete the partial dependency when there are more than one primary key 
                                       3-  3NF is to delete the transitive dependency 

      - some concepts like 1- disjoin (( one coulmn is impossible to be like other column )) 
                           2- specilization (( like person( has address - city )) and the customer and employee are the person type and the employee may be manager and programmer also ) 
                           3- generalization is the opposite of the specialization 


3- physical data model 
      - we start use the SQL ( the DDL : data defination language like ( create - drop - alter ,,,, DML : data manpulation language like insert - update - delete - select ) 


4- SECURITY AND AUTHORIZATION 
        is to specify how will access to the data ( modify and change ) all these functions 
