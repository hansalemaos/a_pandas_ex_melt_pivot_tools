# Some useful melt / pivot stuff for pandas DataFrames

```python
pip install a-pandas-ex-melt-pivot-tools
```

```python
from a_pandas_ex_melt_pivot_tools import pd_add_stack_melt_tools
pd_add_stack_melt_tools()
import pandas as pd
df = pd.DataFrame(
    {
        "A": ["foo", "foo", "foo", "foo", "foo", "bar", "bar", "bar", "bar"],
        "B": ["one", "one", "one", "two", "two", "one", "one", "two", "two"],
        "C": [
            "small",
            "large",
            "large",
            "small",
            "small",
            "large",
            "small",
            "small",
            "large",
        ],
        "D": [1, 2, 2, 3, 3, 4, 5, 6, 7],
        "E": [2, 4, 5, 5, 6, 6, 8, 9, 9],
    }
)
print('___________________________________')
print(f'{df}\n\n')
print('___________________________________')
print(f"{df.ds_pivot_to_list(columns=['A'])}\n\n")
print(f"{df.ds_pivot_to_list(columns=['A','B'])}\n\n")
print(f"{df.ds_pivot_to_list(columns=['A','B', 'C'],stack=True)}\n\n")
print(f"{df.ds_pivot_to_list_no_old_index_column(columns=['A'])}\n\n")
print(f"{df.ds_pivot_to_list_no_old_index_column(columns=['A','B'])}\n\n")
print(f"{df.ds_pivot_to_list_no_old_index_column(columns=['A','B', 'C'],stack=True)}\n\n")
print(f"{df.ds_pivot_to_list_no_old_index_column_transposed(columns=['A'],stack=True)}\n\n")
print(f"{df.ds_pivot_to_list_no_old_index_column_transposed(columns=['A','B'],stack=True)}\n\n")
print(f"{df.ds_pivot_to_list_no_old_index_column_transposed(columns=['A','B', 'C'],stack=True)}\n\n")
___________________________________
     A    B      C  D  E
0  foo  one  small  1  2
1  foo  one  large  2  4
2  foo  one  large  2  5
3  foo  two  small  3  5
4  foo  two  small  3  6
5  bar  one  large  4  6
6  bar  one  small  5  8
7  bar  two  small  6  9
8  bar  two  large  7  9
___________________________________
                                            bar  ...      old_columns
old_columns                                      ...                 
B                    [one, one, two, two, None]  ...  [B, B, B, B, B]
C            [large, small, small, large, None]  ...  [C, C, C, C, C]
D                            [4, 5, 6, 7, None]  ...  [D, D, D, D, D]
E                            [6, 8, 9, 9, None]  ...  [E, E, E, E, E]
[4 rows x 3 columns]
                              bar  ... old_columns
                              one  ...            
old_columns                        ...            
C            [large, small, None]  ...   [C, C, C]
D                    [4, 5, None]  ...   [D, D, D]
E                    [6, 8, None]  ...   [E, E, E]
[3 rows x 5 columns]
                         bar                   foo         old_columns
                         one        two        one     two            
old_columns                                                           
D                        NaN        NaN        NaN     NaN      [D, D]
            large  [4, None]  [7, None]     [2, 2]     NaN         NaN
            small  [5, None]  [6, None]  [1, None]  [3, 3]         NaN
E                        NaN        NaN        NaN     NaN      [E, E]
            large  [6, None]  [9, None]     [4, 5]     NaN         NaN
            small  [8, None]  [9, None]  [2, None]  [5, 6]         NaN
                            bar                                  foo
B          [one, one, two, two]            [one, one, one, two, two]
C  [large, small, small, large]  [small, large, large, small, small]
D                  [4, 5, 6, 7]                      [1, 2, 2, 3, 3]
E                  [6, 8, 9, 9]                      [2, 4, 5, 5, 6]
              bar                                    foo                
              one             two                    one             two
C  [large, small]  [small, large]  [small, large, large]  [small, small]
D          [4, 5]          [6, 7]              [1, 2, 2]          [3, 3]
E          [6, 8]          [9, 9]              [2, 4, 5]          [5, 6]
         bar          foo        
         one  two     one     two
D large  [4]  [7]  [2, 2]     NaN
  small  [5]  [6]     [1]  [3, 3]
E large  [6]  [9]  [4, 5]     NaN
  small  [8]  [9]     [2]  [5, 6]
bar  B      one
     C    large
     D        4
     E        6
     B      one
          ...  
foo  E        5
     B      two
     C    small
     D        3
     E        6
Length: 3524, dtype: object
bar  one  C    large
          D        4
          E        6
          C    large
          D        4
               ...  
foo  two  D        3
          E        5
          C    small
          D        3
          E        6
Length: 153, dtype: object
bar  one  large  D    4
                 E    6
          small  D    5
                 E    8
     two  large  D    7
                 E    9
          small  D    6
                 E    9
foo  one  large  D    2
                 E    4
                 D    2
                 E    5
                 D    2
                 E    4
                 D    2
                 E    5
          small  D    1
                 E    2
     two  small  D    3
                 E    5
                 D    3
                 E    6
                 D    3
                 E    5
                 D    3
                 E    6
dtype: object


```
