
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











