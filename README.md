                                                                               # pl-Assignment1
### Case Study: 

###### I create database system management system of school recording in four entity { lecture ,course, depatrment and student} and due to that database we have used to insert update delete and other all commands like inner join cross join so it due to this relational diagram.

![Relational_1](https://github.com/user-attachments/assets/3e10ba20-c166-4030-ad9a-0edad17d681c)

 
### Here are all four creating tables


##### SCREENSHOT
![creating tables](https://github.com/user-attachments/assets/af09cd2d-8c4f-4547-b909-832eba947220)
##### creating table departmenr1
```sql
SQL> create table department1(DeptId number(4) primary key,lecturesId number(4),StId number(4)  );
SQL> desc depatrment1;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 DEPTID                                             NUMBER(4)
 LECTURESID                                         NUMBER(4)
 STID                                               NUMBER(4)


Table created.
```
##### Adding foreign key constarint
```sql
SQL> alter table department1 add constraint fkl foreign key (lecturesId) references lectures1 (lecturesId);

Table altered.
```

##### inserting values
```sql
SQL> insert into department1(Deptid,lecturesId,stid) values ( 03 ,'', 2002);

1 row created.

SQL> insert into department1(Deptid,lecturesId,stid) values ( 04 ,'', 2003);

1 row created.

SQL> insert into department1(Deptid,lecturesId,stid) values ( 05 ,'', 2004);

1 row created.

SQL> select * from department1;

    DEPTID LECTURESID       STID
---------- ---------- ----------
         1                  2000
         2                  2001
         3                  2002
         4                  2003
         5                  2004
```
##### Updating
```sql
SQL> update department1 set lecturesid = '100'  where deptid=1;

1 row updated.

SQL> update department1 set lecturesid = '101'  where deptid=222;

0 rows updated.

SQL> update department1 set lecturesid = '101'  where deptid=2;

1 row updated.

SQL> update department1 set lecturesid = '201'  where deptid=3;

1 row updated.

SQL> update department1 set lecturesid = '301'  where deptid=4;

1 row updated.

SQL> update department1 set lecturesid = '300'  where deptid=5;

1 row updated.

SQL> select * from department1;

    DEPTID LECTURESID       STID
---------- ---------- ----------
         1        100       2000
         2        101       2001
         3        201       2002
         4        301       2003
         5        300       2004

```
##### creating table student
```sql
SQL> create table Student1( StId number(4) primary key, Name varchar(20) , DeptId number(4), foreign key(DeptId) references department1(DeptId));

Table created.
SQL> desc student1;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 STID                                      NOT NULL NUMBER(4)
 NAME                                               VARCHAR2(20)
 DEPTID                                             NUMBER(4)
 COURSENAME                                         VARCHAR2(10)
```

##### inserting in student
```sql
SQL> insert into student1(stid,name,deptid,coursename) values ( 2001 ,'kev', '','');

1 row created.

SQL> insert into student1(stid,name,deptid,coursename) values ( 2002 ,'Ezra', '','');

1 row created.

SQL> select* from student1;

      STID NAME                     DEPTID COURSENAME
---------- -------------------- ---------- ----------
      2000 Alain
      2001 kev
      2002 Ezra
      2003 cedro
      2004 cedro
```
##### Updating
```sql

      SQL> update student1 set Deptid=01  where stid=2000;



SQL> update student1 set Deptid=02  where stid=2001;

1 row updated.

SQL> update student1 set Deptid=03  where stid=2003;

1 row updated.

SQL> update student1 set Deptid=03  where stid=2004;

1 row updated.

SQL> update student1 set Deptid=03  where stid=2002;

1 row updated.
// here we updated the deptid
SQL> select * from student1;

      STID NAME                     DEPTID COURSENAME
---------- -------------------- ---------- ----------
      2000 Alain                         1
      2001 kev                           2
      2002 Ezra                          3
      2003 cedro                         3
      2004 cedro                         3

    
#Differences

SQL> select* from student1;

      STID NAME                     DEPTID COURSENAME
---------- -------------------- ---------- ----------
      2000 Alain
      2001 kev
      2002 Ezra
      2003 cedro
      2004 cedro

      SQL> update student1 set Deptid=01  where stid=2000;
```
      
##### Screenshot
--![updating in student111](https://github.com/user-attachments/assets/70c6f3ee-72c4-4860-9a02-c5a14cd6fb74)
##### Creating , inserting updating Deleting into table Lecture1
```sql
SQL> create table lectures1(lecturesId number(4) primary key , lectures_name varchar(20), StId number(4), course_name varchar(20) ,foreign key (StId) references student1(StId));
inserting values
SQL> insert into lectures1(lecturesid,lectures_name,stid,course_name) values ( 100 ,'Eric', 2000,'pl');

1 row created.


--updating
--// here we just inserting values in the tables we had foreign key which are empty so we are just updating by initialising data
 
SQL> insert into lectures1(lecturesid,lectures_name,stid,course_name) values ( 200 ,'Patric', 2000,'pl1');

1 row created.

SQL> insert into lectures1(lecturesid,lectures_name,stid,course_name) values ( 201 ,'Patric', 2001,'pl1');

1 row created.

SQL> insert into lectures1(lecturesid,lectures_name,stid,course_name) values ( 101 ,'Patric', 2002,'pl');

1 row created.

SQL> insert into lectures1(lecturesid,lectures_name,stid,course_name) values ( 102 ,'Eric', 2003,'pl');

1 row created.

SQL> insert into lectures1(lecturesid,lectures_name,stid,course_name) values ( 103 ,'Eric', 2004,'pl');

1 row created.
SQL> select * from lectures1;

LECTURESID LECTURES_NAME              STID COURSE_NAME
---------- -------------------- ---------- --------------------
       100 Eric                       2000 pl
       200 Patric                     2000 pl1
       201 Patric                     2001 pl1
       101 Patric                     2002 pl
       102 Eric                       2003 pl
       103 Eric                       2004 pl
       300 Joshua                     2004 Net
       301 Joshua                     2000 Net
       302 Joshua                     2001 Net
       304 Joshua                     2002 Net

--#screenshot
--![lectures](https://github.com/user-attachments/assets/8e2f6749-5790-4a92-b754-06a47871179c)
##### Creating,updating and inserting table course1
```sql 
Table created.
SQL> create table course1(courseName varchar(10) primary key , periods varchar(20), StId number(4), lectureseId number(4) ,foreign key (StId) references student1(StId));

Table created.
SQL> alter table course1 add constraint fk foreign key (lectureseId) references lectures1 (lecturesId);

Table altered.
inserting valuues

SQL> insert into course1(coursename,periods,stid,lectureseid) values (' Net1' ,'4-periods', 2004,300);

1 row created.

SQL> insert into course1(coursename,periods,stid,lectureseid) values (' Net2' ,'4-periods', 2002,304);

1 row created.

SQL> insert into course1(coursename,periods,stid,lectureseid) values (' pl' ,'4-periods', 2000,100);
SQL> select * from course1;

using delete

COURSENAME PERIODS                    STID LECTURESEID
---------- -------------------- ---------- -----------
 Net       4-periods                  2000         301
 Net1      4-periods                  2004         300
 Net2      4-periods                  2002         304
 pl        4-periods                  2000         100
 pl1       4-periods                  2001         101
 pl2       4-periods                  2002         101

6 rows selected.
SQL> DELETE FROM course1 WHERE stid = 2004;

1 row deleted.

SQL>
SQL> select * from course1;

COURSENAME PERIODS                    STID LECTURESEID
---------- -------------------- ---------- -----------
 Net       4-periods                  2000         301
 Net2      4-periods                  2002         304
 pl        4-periods                  2000         100
 pl1       4-periods                  2001         101
 pl2       4-periods                  2002         101
```

##### Joining 
```sql


SELECT Student1.StId, Student1.Name, department1.DeptId, department1.lecturesId
FROM Student1
INNER JOIN department1
ON Student1.DeptId = department1.DeptId;
SQL> SELECT 
  2    s.StId,
  3    s.Name,
  4    l.lectures_name,
  5    l.course_name,
  6    c.courseName,
  7    c.periods
  8  FROM 
  9    student1 s
 10  INNER JOIN 
 11    lectures1 l ON s.StId = l.StId
 12  INNER JOIN 
 13    course1 c ON s.StId = c.StId;

    StId Name                lectures_name     course_name       courseName   periods   
  ------ ------------------- ----------------- ----------------- ----------- ----------- 
   1001 John                Math 101         Algebra           Algebra      10 weeks    
   1002 Alice               Physics 101      Mechanics         Mechanics    12 weeks    
   1003 Robert              Chemistry 101    Organic Chemistry  Organic      8 weeks


##Cross joining: i joined lectures and course 1 by cross joining


SQL> SELECT *FROM lectures1 CROSS JOIN course1;

LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       100 Eric                       2000 pl                    Net
4-periods                  2000         301

       200 Patric                     2000 pl1                   Net
4-periods                  2000         301

       201 Patric                     2001 pl1                   Net
4-periods                  2000         301


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       101 Patric                     2002 pl                    Net
4-periods                  2000         301

       102 Eric                       2003 pl                    Net
4-periods                  2000         301

       103 Eric                       2004 pl                    Net
4-periods                  2000         301


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       300 Joshua                     2004 Net                   Net
4-periods                  2000         301

       301 Joshua                     2000 Net                   Net
4-periods                  2000         301

       302 Joshua                     2001 Net                   Net
4-periods                  2000         301


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       304 Joshua                     2002 Net                   Net
4-periods                  2000         301

       100 Eric                       2000 pl                    Net2
4-periods                  2002         304

       200 Patric                     2000 pl1                   Net2
4-periods                  2002         304


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       201 Patric                     2001 pl1                   Net2
4-periods                  2002         304

       101 Patric                     2002 pl                    Net2
4-periods                  2002         304

       102 Eric                       2003 pl                    Net2
4-periods                  2002         304


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       103 Eric                       2004 pl                    Net2
4-periods                  2002         304

       300 Joshua                     2004 Net                   Net2
4-periods                  2002         304

       301 Joshua                     2000 Net                   Net2
4-periods                  2002         304


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       302 Joshua                     2001 Net                   Net2
4-periods                  2002         304

       304 Joshua                     2002 Net                   Net2
4-periods                  2002         304

       100 Eric                       2000 pl                    pl
4-periods                  2000         100


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       200 Patric                     2000 pl1                   pl
4-periods                  2000         100

       201 Patric                     2001 pl1                   pl
4-periods                  2000         100

       101 Patric                     2002 pl                    pl
4-periods                  2000         100


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       102 Eric                       2003 pl                    pl
4-periods                  2000         100

       103 Eric                       2004 pl                    pl
4-periods                  2000         100

       300 Joshua                     2004 Net                   pl
4-periods                  2000         100


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       301 Joshua                     2000 Net                   pl
4-periods                  2000         100

       302 Joshua                     2001 Net                   pl
4-periods                  2000         100

       304 Joshua                     2002 Net                   pl
4-periods                  2000         100


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       100 Eric                       2000 pl                    pl1
4-periods                  2001         101

       200 Patric                     2000 pl1                   pl1
4-periods                  2001         101

       201 Patric                     2001 pl1                   pl1
4-periods                  2001         101


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       101 Patric                     2002 pl                    pl1
4-periods                  2001         101

       102 Eric                       2003 pl                    pl1
4-periods                  2001         101

       103 Eric                       2004 pl                    pl1
4-periods                  2001         101


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       300 Joshua                     2004 Net                   pl1
4-periods                  2001         101

       301 Joshua                     2000 Net                   pl1
4-periods                  2001         101

       302 Joshua                     2001 Net                   pl1
4-periods                  2001         101


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       304 Joshua                     2002 Net                   pl1
4-periods                  2001         101

       100 Eric                       2000 pl                    pl2
4-periods                  2002         101

       200 Patric                     2000 pl1                   pl2
4-periods                  2002         101


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       201 Patric                     2001 pl1                   pl2
4-periods                  2002         101

       101 Patric                     2002 pl                    pl2
4-periods                  2002         101

       102 Eric                       2003 pl                    pl2
4-periods                  2002         101


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       103 Eric                       2004 pl                    pl2
4-periods                  2002         101

       300 Joshua                     2004 Net                   pl2
4-periods                  2002         101

       301 Joshua                     2000 Net                   pl2
4-periods                  2002         101


LECTURESID LECTURES_NAME              STID COURSE_NAME          COURSENAME
---------- -------------------- ---------- -------------------- ----------
PERIODS                    STID LECTURESEID
-------------------- ---------- -----------
       302 Joshua                     2001 Net                   pl2
4-periods                  2002         101

       304 Joshua                     2002 Net                   pl2
4-periods                  2002         101


50 rows selected.

# by left join i joined student1 left join to lectures1
SQL> SELECT 
  2    s.StId,
  3    s.Name,
  4    l.lectures_name,
  5    l.course_name,
  6    c.courseName,
  7    c.periods
  8  FROM 
  9    student1 s
 10  LEFT JOIN 
 11    lectures1 l ON s.StId = l.StId
 12  LEFT JOIN 
 13    course1 c ON s.StId = c.StId;

    StId Name                lectures_name     course_name       courseName   periods   
  ------ ------------------- ----------------- ----------------- ----------- ----------- 
   1001 cedro                ERIC                  PL             PL1         4-periods
   1002 pedro                Joshua              NET              NET         3-periods   
   1003 kev                  Turiho              DBMS             DB           4-periods     
   1004 cedro                MANARIHO           NULL              NULL        NULL 

```



-
