jupyter:
  colab:
  kernelspec:
    display_name: Python 3
    name: python3
  language_info:
    name: python
  nbformat: 4
  nbformat_minor: 0
---

<div class="cell markdown" id="9xZnRXM7x0Cv">

# CUHK-STAT1013: Practical Assignment Part 1: Sharing Your Idea and Data

</div>

<div class="cell markdown" id="9Fy05KAkyJI0">

## Titanic dataset background

**Description**:

Dataset describing the survival status of individual passengers on the
Titanic.

**Github**:
<https://github.com/datasciencedojo/datasets/blob/master/titanic.csv>

**Sample size**: 1,309

**Feature documentation**:

| Feature   | Class      | Shape | Dtype   |
|:----------|:-----------|:------|:--------|
| age       | Tensor     |       | float32 |
| boat      | Tensor     |       | string  |
| body      | Tensor     |       | int32   |
| cabin     | Tensor     |       | string  |
| embarked  | ClassLabel |       | int64   |
| fare      | Tensor     |       | float32 |
| home.dest | Tensor     |       | string  |
| name      | Tensor     |       | string  |
| parch     | Tensor     |       | int32   |
| pclass    | ClassLabel |       | int64   |
| sex       | ClassLabel |       | int64   |
| sibsp     | Tensor     |       | int32   |
| survived  | ClassLabel |       | int64   |
| ticket    | Tensor     |       | string  |

</div>

<div class="cell markdown" id="k85zO7zxys4H">

## Hypothesis

-   Tell us what your idea is and why you have chosen to pursue this
    idea.
    -   We are interested in "*Did women have a better chance of
        survival on the Titanic?*"
-   What two groups you are comparing:
    -   **G1**: survival rate of male on the Titanic; **G2**: survival
        rate of female on the Titanic
-   What you will be measuring (i.e., what your response variable will
    be)
    -   `survived`
-   Is your response variable quantitative rather than categorical?
    -   `survived` is binary data, with the order `1 > 0`, which can be
        regarded as a quantitative variable.
-   Make a prediction about what kind of difference you expect to see
    between your samples and WHY.
    -   We'd expect that **G2** \> **G1** since [Women and children
        first on the
        Titanic](https://www.theguardian.com/science/2010/mar/02/titanic-lusitania-women-children-survival).
-   Talk about how you will gather your data
    -   From Github link:
        <https://github.com/datasciencedojo/datasets/blob/master/titanic.csv>
-   If you had unlimited resources (time, money, staff, etc.) how would
    you collect your data?
    -   \(i\) Attempt to collect more data on Titanic; (ii) investigate
        if the provided dataset is a good random sampling subset of the
        original Titanic population.

</div>

<div class="cell markdown" id="3GOdPWT03PQB">

## Prepare your dataset

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:206}"
id="mUxJb4hxvpHQ" outputId="fcfa9d33-4114-4ca1-d490-25975860a56a">

``` python
## load dataset from github

import pandas as pd

df = pd.read_csv('https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv')
df.head(5)
```

<div class="output execute_result" execution_count="1">

       PassengerId  Survived  Pclass  \
    0            1         0       3   
    1            2         1       1   
    2            3         1       3   
    3            4         1       1   
    4            5         0       3   

                                                    Name     Sex   Age  SibSp  \
    0                            Braund, Mr. Owen Harris    male  22.0      1   
    1  Cumings, Mrs. John Bradley (Florence Briggs Th...  female  38.0      1   
    2                             Heikkinen, Miss. Laina  female  26.0      0   
    3       Futrelle, Mrs. Jacques Heath (Lily May Peel)  female  35.0      1   
    4                           Allen, Mr. William Henry    male  35.0      0   

       Parch            Ticket     Fare Cabin Embarked  
    0      0         A/5 21171   7.2500   NaN        S  
    1      0          PC 17599  71.2833   C85        C  
    2      0  STON/O2. 3101282   7.9250   NaN        S  
    3      0            113803  53.1000  C123        S  
    4      0            373450   8.0500   NaN        S  

</div>

</div>

<div class="cell markdown" id="55xAIxVa3hpQ">

-   Tell us what groups you want to compare in the dataset
    -   **G1** (survived \| sex = male) vs. **G2** (survived \| sex =
        female)

</div>

<div class="cell markdown" id="13PdL3ht3902">

-   Print first 5 records of each group, respectively.

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="UNL0WXav3hLj" outputId="f02d3bf4-52e9-4df8-c91c-b7b8438b4c45">

``` python
## First 5 records of G1 (male)
(df[df['Sex'] == 'male']['Survived']).head(5)
```

<div class="output execute_result" execution_count="2">

    0    0
    4    0
    5    0
    6    0
    7    0
    Name: Survived, dtype: int64

</div>

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="dhe52HVB4T1O" outputId="91d9ccc4-e004-4c31-fd0d-66c9744f9c74">

``` python
## First 5 records of G2 (female)
(df[df['Sex'] == 'female']['Survived']).head(5)
```

<div class="output execute_result" execution_count="3">

    1    1
    2    1
    3    1
    8    1
    9    1
    Name: Survived, dtype: int64

</div>

</div>

<div class="cell code" id="zEgfWXaKGvNC">

``` python
## Any other data description and visualization you want to add.

## Open question, be flexible and no example can be provided.
```

</div>
