---
title: SQL AND operator
---
## SQL AND operator

AND is used in a WHERE clause or a GROUP BY HAVING clause to limit the rows returned from the executed statement.  Use AND when it's required to have more than one condition met.

We'll use the simple student table to present examples.

Here's the student table without and WHERE clause:
```sql
select * from student;
```
![image-1](https://github.com/SteveChevalier/guide-images/blob/master/and_operator01.JPG?raw=true)

Now to see just the programming students:
```sql
select * from student 
where programOfStudy = 'Programming';
```
![image-1](https://github.com/SteveChevalier/guide-images/blob/master/and_operator02.JPG?raw=true)

Now for programming students that have a SAT score greater than 800:
```sql
select * from student 
where programOfStudy = 'Programming' 
and sat_score > 800;
```
![image-1](https://github.com/SteveChevalier/guide-images/blob/master/and_operator03.JPG?raw=true)


One last but somewhat more complex example from the campaign contributions table. This example has a GROUP BY clause with HAVING clause using and AND to restrict the returned records to candates from 2016 with contributions between $3 Million and $18 Million in total.
```sql
select Candidate, Office_Sought, Election_Year, FORMAT(sum(Total_$),2) from combined_party_data
where Office_Sought = 'PRESIDENT / VICE PRESIDENT'
group by Candidate, Office_Sought, Election_Year
 having Election_Year = 2016 and sum(Total_$) between 3000000 and 18000000
order by sum(Total_$) desc;
```
![image-1](https://github.com/SteveChevalier/guide-images/blob/master/and_operator06.JPG?raw=true)

