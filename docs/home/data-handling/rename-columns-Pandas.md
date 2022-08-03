
# Rename columns in Pandas

You can use one of the following three methods to rename columns in a pandas DataFrame:

- Method 1: Rename Specific Columns
    ``` python
    df.rename(columns = {'old_col1':'new_col1', 'old_col2':'new_col2'}, inplace = True)
    ```
    Code example:
    ``` python
    import pandas as pd

    #define DataFrame
    df = pd.DataFrame({'team':['A', 'A', 'A', 'A', 'B', 'B', 'B', 'B'],
                    'points': [25, 12, 15, 14, 19, 23, 25, 29],
                    'assists': [5, 7, 7, 9, 12, 9, 9, 4],
                    'rebounds': [11, 8, 10, 6, 6, 5, 9, 12]})

    #list column names
    list(df)

    ['team', 'points', 'assists', 'rebounds']

    #rename specific column names
    df.rename(columns = {'team':'team_name', 'points':'points_scored'}, inplace = True)

    #view updated list of column names
    list(df)

    ['team_name', 'points_scored', 'assists', 'rebounds']
    ```
- Method 2: Rename All Columns
    ``` python
    df.columns = ['new_col1', 'new_col2', 'new_col3', 'new_col4']
    ``` 
    Code example:
    ``` python
    import pandas as pd
    #define DataFrame
    df = pd.DataFrame({'team':['A', 'A', 'A', 'A', 'B', 'B', 'B', 'B'],
                    'points': [25, 12, 15, 14, 19, 23, 25, 29],
                    'assists': [5, 7, 7, 9, 12, 9, 9, 4],
                    'rebounds': [11, 8, 10, 6, 6, 5, 9, 12]})

    #list column names
    list(df)

    ['team', 'points', 'assists', 'rebounds']

    #rename all column names
    df.columns = ['_team', '_points', '_assists', '_rebounds']

    #view updated list of column names
    list(df)

    ['_team', '_points', '_assists', '_rebounds']
    ```

- Method 3: Replace Specific Characters in Columns
    ``` python
    df.columns = df.columns.str.replace('old_char', 'new_char')
    ``` 
    Code example:
    ``` python
    import pandas as pd

    #define DataFrame
    df = pd.DataFrame({'$team':['A', 'A', 'A', 'A', 'B', 'B', 'B', 'B'],
                    '$points': [25, 12, 15, 14, 19, 23, 25, 29],
                    '$assists': [5, 7, 7, 9, 12, 9, 9, 4],
                    '$rebounds': [11, 8, 10, 6, 6, 5, 9, 12]})

    #list column names
    list(df)

    ['team', 'points', 'assists', 'rebounds']

    #rename $ with blank in every column name
    df.columns = df.columns.str.replace('$', '')

    #view updated list of column names
    list(df)

    ['team', 'points', 'assists', 'rebounds']
    ```
!!! info "Reference and related articles"
    * :ledger: [How to Rename Columns in Pandas ](https://www.statology.org/pandas-rename-columns/)