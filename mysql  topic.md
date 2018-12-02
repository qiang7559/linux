#### 导入hellodb.sql生成数据库  
(1) 在students表中，查询年龄大于25岁，且为男性的同学的名字和年龄  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select b.name,b.age  from students b  where age > 25 and gender='M'; ```  

(2) 以ClassID为分组依据，显示每组的平均年龄  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select classid,avg(age) from students group by classid;```

(3) 显示第2题中平均年龄大于30的分组及平均年龄   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select classid,avg(age) from students group by classid having avg(age) > 30;```

(4) 显示以L开头的名字的同学的信息  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select * from students where name rlike '^L' ;```

(5) 显示TeacherID非空的同学的相关信息  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select * from students where teacherid is not null ;```

(6) 以年龄排序后，显示年龄最大的前10位同学的信息   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select * from students order by age desc limit 10;```

(7) 查询年龄大于等于20岁，小于等于25岁的同学的信息  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select *  from students where age  between 20 and 25;  ```  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select *  from students where  age >=20 and age <=25 ;  ```


(8) 以ClassID分组，显示每班的同学的人数  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select classid,count(*) from students group by classid;```

 
(9) 以Gender分组，显示其年龄之和   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select classid,sum(age) from students group by classid;```


(10) 以ClassID分组，显示其平均年龄大于25的班级   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select classid,avg(age) as a from students group by classid having  a > 25 ;```


(11) 以Gender分组，显示各组中年龄大于25的学员的年龄之和   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select classid,sum(age) from students where age > 25  group by classid;```


(12) 显示前5位同学的姓名、课程及成绩  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select stu.name,cou.course,sco.score  from students as stu left outer join courses as cou on stu.classid=cou.courseid left outer join scores as sco on stu.stuid=sco.stuid where stu.stuid <= 5  ;```


(13) 显示其成绩高于80的同学的名称及课程    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select stu.name,cou.course  from students as stu left outer join courses as cou on stu.classid=cou.courseid left outer join scores as sco on stu.stuid=sco.stuid   where sco.score >= 80  ;```


(14) 取每位同学各门课的平均成绩，显示成绩前三名的同学的姓名和平均成绩    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;```  select  ll.name,avg(ll.score) as scoo  from (select stu.name,cou.course,sco.score  from students as stu left outer join courses as cou on stu.classid=cou.courseid left outer join scores as sco    on stu.stuid=sco.stuid) as ll  where ll.score is not null group by ll.name order  by scoo  desc limit 3 ;```


(15) 显示每门课程课程名称及学习了这门课的同学的个数   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;``` select s.course,count(s.course)  from (select stu.name,cou.course  from students as stu left outer join courses as cou on stu.classid=cou.courseid) as s  group by s.course ; ```


(16) 显示其年龄大于平均年龄的同学的名字   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;``` select stu.name  from students as stu where  (select avg(age)  from students) < stu.age ；```


(17) 显示其学习的课程为第1、2，4或第7门课的同学的名字  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;``` select stu.name  from students as stu left outer join courses as cou on stu.classid=cou.courseid where cou.courseid in (1,2,4,7) ;```


(18) 显示其成员数最少为3个的班级的同学中年龄大于同班同学平均年龄的同学   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;``` select Name,Age from (select Class,c.ClassID from students as s,classes  as c where s.ClassID=c.ClassID group by Class having  count(Name) >= 3) as c,students as s where c.ClassID=s.ClassID and Age > (select avg(Age) from students);```


(19) 统计各班级中年龄大于全校同学平均年龄的同学   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&nsc;&nsc;``` select Name,Age from students as s,classes as c where s.ClassID=c.ClassID and Age > (select avg(Age) from students);      ```

