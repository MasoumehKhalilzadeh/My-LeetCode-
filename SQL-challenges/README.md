
## Question 1 

Write a solution to find the ids of products that are both low fat and recyclable.

Return the result table in any order.

<img width="326" alt="image" src="https://github.com/Masoumeh89/My-LeetCode-/assets/74910834/1835aaac-dbdc-4538-93b3-a32364cc9675">


```sql
select product_id 
from Products
where low_fats = 'Y' and recyclable = 'Y'
```












