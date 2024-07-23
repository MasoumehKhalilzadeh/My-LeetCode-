## Select


### Question 1: Recyclable and Low Fat Products

Write a solution to find the ids of products that are both low fat and recyclable.

Return the result table in any order.

<img width="326" alt="image" src="https://github.com/Masoumeh89/My-LeetCode-/assets/74910834/1835aaac-dbdc-4538-93b3-a32364cc9675">


```sql
select product_id 
from Products
where low_fats = 'Y' and recyclable = 'Y'
```



### Question 2: Find Customer Referee

Find the names of the customer that are not referred by the customer with id = 2.

<img width="244" alt="image" src="https://github.com/Masoumeh89/My-LeetCode-/assets/74910834/f7c78458-2b47-45ee-bab8-9476638d5b9f">

```sql
select name
from Customer
where referee_id <> 2 or referee_id is null

```

### Question 3: Big Countries

A country is big if:

it has an area of at least three million (i.e., 3000000 km2), or
it has a population of at least twenty-five million (i.e., 25000000).
Write a solution to find the name, population, and area of the big countries.

<img width="427" alt="image" src="https://github.com/Masoumeh89/My-LeetCode-/assets/74910834/9f9814d3-1e88-447f-9488-8e69c4e8465d">

```sql

select name, population, area
from World
where area >= 3000000 or population >= 25000000


```

### Question 4: Article Views I

Write a solution to find all the authors that viewed at least one of their own articles.

Return the result table sorted by id in ascending order.

<img width="347" alt="image" src="https://github.com/user-attachments/assets/8e8261dc-b74b-4c44-8886-ec4cf06436e3">

```sql
select distinct author_id as id 
from Views
where author_id = viewer_id
order by id asc;
```


## Basic Joins


### Question 5: Replace Employee ID With The Unique Identifier

Write a solution to show the unique ID of each user, If a user does not have a unique ID replace just show null.

Return the result table in any order.

<img width="146" alt="image" src="https://github.com/user-attachments/assets/9a96ec19-3ba1-4fcc-a29b-f66ffd21e882">

<img width="190" alt="image" src="https://github.com/user-attachments/assets/fe16d354-f70c-4c17-b12d-861ce12fe0b9">

```sql
select u.unique_id as unique_id, e.name as name      
from Employees e
left join EmployeeUNI u
on e.id = u.id

```


### Question 6: Product Sales Analysis I

Write a solution to report the product_name, year, and price for each sale_id in the Sales table.


<img width="356" alt="image" src="https://github.com/user-attachments/assets/12a89e7b-51a1-4423-90d3-f61a473dd108">


<img width="228" alt="image" src="https://github.com/user-attachments/assets/717754e0-a775-45ed-8fa3-6d03bd033a7f">


```sql

select p.product_name, s.year, s.price
from Sales s
join Product p
on s.product_id = p.product_id 

```

### Question 7: Customer Who Visited but Did Not Make Any Transactions


Write a solution to find the IDs of the users who visited without making any transactions and the number of times they made these types of visits.

<img width="248" alt="image" src="https://github.com/user-attachments/assets/762ee284-a04c-4bad-8a8f-12dce4572130">

<img width="196" alt="image" src="https://github.com/user-attachments/assets/3960c52c-9738-448f-af41-e3b4f5cbeaae">

```sql
select v.customer_id as customer_id, count(v.visit_id) as count_no_trans 
from Visits v
left join Transactions t
on v.visit_id = t.visit_id 
where t.transaction_id is NULL
GROUP BY v.customer_id
ORDER BY v.customer_id;
```


### Question 8: Rising Temperature

Write a solution to find all dates' Id with higher temperatures compared to its previous dates (yesterday).

<img width="233" alt="image" src="https://github.com/user-attachments/assets/92a7ea8e-8fa7-4c2a-ba5a-0fc0aa2dd345">

```sql
select w1.id
from Weather w1
join Weather w2 
on date_add(w2.recordDate, interval 1 day) = w1.recordDate
where w1.temperature > w2.temperature;

```


### Question 9: Average Time of Process per Machine 

There is a factory website that has several machines each running the same number of processes. Write a solution to find the average time each machine takes to complete a process.

The time to complete a process is the 'end' timestamp minus the 'start' timestamp. The average time is calculated by the total time to complete every process on the machine divided by the number of processes that were run.

The resulting table should have the machine_id along with the average time as processing_time, which should be rounded to 3 decimal places.



<img width="341" alt="image" src="https://github.com/user-attachments/assets/1d18f46c-9f7a-4417-be5a-1d8daa440064">

<img width="205" alt="image" src="https://github.com/user-attachments/assets/73307ee6-39ec-486d-a0cc-1218a422e185">


```sql

WITH ProcessTimes AS (
    SELECT
        machine_id,
        process_id,
        MAX(CASE WHEN activity_type = 'end' THEN timestamp ELSE NULL END) - 
        MAX(CASE WHEN activity_type = 'start' THEN timestamp ELSE NULL END) AS process_time
    FROM Activity
    GROUP BY machine_id, process_id
),
MachineTimes AS (
    SELECT
        machine_id,
        AVG(process_time) AS avg_processing_time
    FROM ProcessTimes
    GROUP BY machine_id
)
SELECT
    machine_id,
    ROUND(avg_processing_time, 3) AS processing_time
FROM MachineTimes;


```


### Question 10: Employee Bonus

Write a solution to report the name and bonus amount of each employee with a bonus less than 1000.

<img width="239" alt="image" src="https://github.com/user-attachments/assets/74a895c4-555b-4c77-80dc-d110ed7348d0">


```sql
select e.name as name, b.bonus as bonus 
from Employee e
left join Bonus b
on e.empId = b.empId 
where b.bonus < 1000 or b.bonus is null

```

### Question 11:Students and Examinations

Write a solution to find the number of times each student attended each exam.

Return the result table ordered by student_id and subject_name.

The result format is in the following example.

<img width="194" alt="image" src="https://github.com/user-attachments/assets/e7597fde-ebda-469c-a730-f6f2e8c6774a">

<img width="203" alt="image" src="https://github.com/user-attachments/assets/cf034bf7-38d8-42f6-a690-950dcd43da2c">

<img width="324" alt="image" src="https://github.com/user-attachments/assets/85f14ba6-5ea6-4f45-82dd-30c5314de737">

```sql
SELECT 
    s.student_id,
    s.student_name,
    sub.subject_name,
    COUNT(e.subject_name) AS attended_exams
FROM 
    Students s
CROSS JOIN 
    Subjects sub
LEFT JOIN 
    Examinations e ON s.student_id = e.student_id AND sub.subject_name = e.subject_name
GROUP BY 
    s.student_id, s.student_name, sub.subject_name
ORDER BY 
    s.student_id, sub.subject_name;

```


### Question 12: Managers with at Least 5 Direct Reports

id is the primary key (column with unique values) for this table.
Each row of this table indicates the name of an employee, their department, and the id of their manager.
If managerId is null, then the employee does not have a manager.
No employee will be the manager of themself.
 

Write a solution to find managers with at least five direct reports.

Return the result table in any order.

The result format is in the following example.

<img width="209" alt="image" src="https://github.com/user-attachments/assets/6899c7c0-81a0-4633-a8cc-db90c34fc28e">

```sql

SELECT 
    e1.name 
FROM 
    Employee e1
WHERE 
    e1.id IN (
        SELECT 
            e.managerId
        FROM 
            Employee e
        WHERE 
            e.managerId IS NOT NULL
        GROUP BY 
            e.managerId
        HAVING 
            COUNT(*) >= 5
    );

```

Subquery:

The subquery selects managerId from the Employee table, grouping by managerId and counting the number of employees (COUNT(*)). It includes only those managerId values where the count is 5 or more (HAVING COUNT(*) >= 5).
Main Query:

The main query selects the name from the Employee table where the id is in the list of managerId values returned by the subquery. This ensures we get the names of managers who have at least five direct reports.

### Question 13: Confirmation Rate

The confirmation rate of a user is the number of 'confirmed' messages divided by the total number of requested confirmation messages. The confirmation rate of a user that did not request any confirmation messages is 0. Round the confirmation rate to two decimal places.

Write a solution to find the confirmation rate of each user.

Return the result table in any order.

The result format is in the following example.

<img width="296" alt="image" src="https://github.com/user-attachments/assets/c72dcb5a-400f-483b-a9e8-898062a8d12a">

<img width="205" alt="image" src="https://github.com/user-attachments/assets/65f8128f-9517-4e9d-b6c7-52edb8217fc6">


```sql
WITH confirmation_counts AS (
    SELECT 
        user_id,
        COUNT(*) AS total_confirmations,
        COUNT(CASE WHEN action = 'confirmed' THEN 1 END) AS confirmed_count
    FROM Confirmations
    GROUP BY user_id
)

SELECT 
    s.user_id,
    IFNULL(ROUND(cc.confirmed_count / cc.total_confirmations, 2), 0.00) AS confirmation_rate
FROM 
    Signups s
LEFT JOIN 
    confirmation_counts cc
ON 
    s.user_id = cc.user_id;

```


## Basic Aggregate Functions

### Not Boring Movies

Write a solution to report the movies with an odd-numbered ID and a description that is not "boring".

Return the result table ordered by rating in descending order.

The result format is in the following example.

<img width="301" alt="image" src="https://github.com/user-attachments/assets/24890004-ba3d-44c0-b44b-0ebf955de2f3">

```sql
select id, movie, description, rating
from Cinema
where description != "boring" and id%2 = 1
order by rating desc

```

###  Average Selling Price

Write a solution to find the average selling price for each product. average_price should be rounded to 2 decimal places.

Return the result table in any order.

The result format is in the following example.

<img width="327" alt="image" src="https://github.com/user-attachments/assets/a5409122-0e3d-4a13-91d3-f105ed331d23">

<img width="185" alt="image" src="https://github.com/user-attachments/assets/6188d32b-3731-4c6f-ad43-7361949ae228">


```sql

SELECT p.product_id,
IFNULL(ROUND(SUM(units*price)/SUM(units),2),0) AS average_price
FROM Prices p 
LEFT JOIN UnitsSold u
ON p.product_id = u.product_id 
AND u.purchase_date BETWEEN start_date AND end_date
group by product_id

```















