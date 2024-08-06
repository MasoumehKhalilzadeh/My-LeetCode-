## Pandas Data Structures

### Question 1: Create a DataFrame from List

Write a solution to create a DataFrame from a 2D list called student_data. This 2D list contains the IDs and ages of some students.

The DataFrame should have two columns, student_id and age, and be in the same order as the original 2D list.

<img width="221" alt="image" src="https://github.com/user-attachments/assets/35bff9d0-f71b-4376-af2f-2e04dbc58fee">

```python

import pandas as pd

def createDataframe(student_data: List[List[int]]) -> pd.DataFrame:
    df = pd.DataFrame(student_data, columns =["student_id","age"])
    return df

```


## Data Inspection

### Get the Size of a DataFrame

Write a solution to calculate and display the number of rows and columns of players.

Return the result as an array:

[number of rows, number of columns]


<img width="428" alt="image" src="https://github.com/user-attachments/assets/4756a8d4-95d8-43c3-9a0c-1f6645c106e8">

```python
import pandas as pd

def getDataframeSize(players: pd.DataFrame) -> List[int]:
    # Get the number of rows and columns
    nrows = players.shape[0]
    ncolumns = players.shape[1]

    # Return as a list
    return[nrows,ncolumns]

```


### Display the First Three Rows


Write a solution to display the first 3 rows of this DataFrame.

<img width="357" alt="image" src="https://github.com/user-attachments/assets/ded7690a-309c-4bb1-b96c-cefe3705479e">


```python
import pandas as pd

def selectFirstRows(employees: pd.DataFrame) -> pd.DataFrame:
    return employees.head(3)
```



## Data Selecting

### Select Data


Write a solution to select the name and age of the student with student_id = 101.

<img width="226" alt="image" src="https://github.com/user-attachments/assets/480b96b7-0b3f-4f97-9982-cf8bbdcd79da">

```python

import pandas as pd

def selectData(students: pd.DataFrame) -> pd.DataFrame:

    # Filter the DataFrame to get the student with student_id = 101
    students = students[students["student_id"] == 101]

    # Select the name and age columns
    result = students[["name","age"]]

    return result


```

### Create a New Column

A company plans to provide its employees with a bonus.

Write a solution to create a new column name bonus that contains the doubled values of the salary column.

The result format is in the following example.

<img width="202" alt="image" src="https://github.com/user-attachments/assets/7f4f901f-735b-4770-96b8-f6a4b2a87370">

```python
import pandas as pd

def createBonusColumn(employees: pd.DataFrame) -> pd.DataFrame:
    employees["bonus"] = employees["salary"]*2
    return employees

```

## Data Cleaning

### Drop Duplicate Rows

There are some duplicate rows in the DataFrame based on the email column.

Write a solution to remove these duplicate rows and keep only the first occurrence.

The result format is in the following example.

<img width="302" alt="image" src="https://github.com/user-attachments/assets/d12d1a0f-8f20-4dc9-beb5-e0a28063b8c7">

```python
import pandas as pd

def dropDuplicateEmails(customers: pd.DataFrame) -> pd.DataFrame:
    customers = customers.drop_duplicates(subset = "email", keep = "first" )
    return customers

```


### Drop Missing Data

There are some rows having missing values in the name column.

Write a solution to remove the rows with missing values.

The result format is in the following example.

<img width="227" alt="image" src="https://github.com/user-attachments/assets/33035959-76a8-494d-88da-452665b59669">

```python

import pandas as pd

def dropMissingData(students: pd.DataFrame) -> pd.DataFrame:
    students = students.dropna(subset = ["name"])
    return students

```

### Modify Columns

A company intends to give its employees a pay rise.

Write a solution to modify the salary column by multiplying each salary by 2.

The result format is in the following example.


<img width="164" alt="image" src="https://github.com/user-attachments/assets/a5e9c896-2ec1-4e24-ab4f-b81413bc57ef">


```python


import pandas as pd

def modifySalaryColumn(employees: pd.DataFrame) -> pd.DataFrame:
    employees["salary"] = employees["salary"]*2
    return employees

```

### Rename Columns

Write a solution to rename the columns as follows:

id to student_id
first to first_name
last to last_name
age to age_in_years
The result format is in the following example.

<img width="361" alt="image" src="https://github.com/user-attachments/assets/e88776f8-bd8e-4071-81e8-3c34e23ebe38">


```python

import pandas as pd

def renameColumns(students: pd.DataFrame) -> pd.DataFrame:
    rename_columns = students.rename(columns={
        'id':'student_id',
        'first':'first_name',
        'last':'last_name',
        'age':'age_in_years'
    })

    return rename_columns
```

## Change Data Type

Write a solution to correct the errors:

The grade column is stored as floats, convert it to integers.

The result format is in the following example.

<img width="342" alt="image" src="https://github.com/user-attachments/assets/56fe7386-7861-421e-8662-9f7573c2f538">

```python
import pandas as pd

def changeDatatype(students: pd.DataFrame) -> pd.DataFrame:
    students['grade'] = students['grade'].astype(int)
    return students

```

## Fill Missing Data

Write a solution to fill in the missing value as 0 in the quantity column.

The result format is in the following example.

<img width="470" alt="image" src="https://github.com/user-attachments/assets/8cfdc2f0-c966-4009-b109-2f670a84736e">

```python
import pandas as pd

def fillMissingValues(products: pd.DataFrame) -> pd.DataFrame:
    products['quantity'] = products['quantity'].fillna(0)
    return products

```


















