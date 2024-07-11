
## Question 1: Recyclable and Low Fat Products

Write a solution to find the ids of products that are both low fat and recyclable.

Return the result table in any order.

<img width="326" alt="image" src="https://github.com/Masoumeh89/My-LeetCode-/assets/74910834/1835aaac-dbdc-4538-93b3-a32364cc9675">


```sql
select product_id 
from Products
where low_fats = 'Y' and recyclable = 'Y'
```



## Question 2: Find Customer Referee

Find the names of the customer that are not referred by the customer with id = 2.

<img width="244" alt="image" src="https://github.com/Masoumeh89/My-LeetCode-/assets/74910834/f7c78458-2b47-45ee-bab8-9476638d5b9f">

```sql
select name
from Customer
where referee_id <> 2 or referee_id is null

```

## Question 3: Big Countries

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

## Question 4: Article Views I

Write a solution to find all the authors that viewed at least one of their own articles.

Return the result table sorted by id in ascending order.

<img width="347" alt="image" src="https://github.com/user-attachments/assets/8e8261dc-b74b-4c44-8886-ec4cf06436e3">

```sql
select distinct author_id as id 
from Views
where author_id = viewer_id
order by id asc;
```


