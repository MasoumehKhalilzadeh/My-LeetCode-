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




