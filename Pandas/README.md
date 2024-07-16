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
