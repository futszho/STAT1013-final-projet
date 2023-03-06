---
jupyter:
  colab:
  kernelspec:
    display_name: Python (Pyodide)
    language: python
    name: python
  language_info:
    codemirror_mode:
      name: python
      version: 3
    file_extension: .py
    mimetype: text/x-python
    name: python
    nbconvert_exporter: python
    pygments_lexer: ipython3
    version: 3.8
  nbformat: 4
  nbformat_minor: 0
---

<div class="cell markdown" id="IpmyVKJ5hYy6">

# CUHK-STAT1013: Practical Assignment Part 1: Sharing Your Idea and Data

</div>

<div class="cell markdown" id="xo70h2eQiNyd">

**Covid-19-data dataset background**

**Description:**

Dataset describing the cases and death of covid-19 in each countries.

**Github:**<https://github.com/owid/covid-19-data/blob/master/public/data/latest/owid-covid-latest.csv>

**Sample size:** 236

**Feature documentation:**

</div>

<div class="cell markdown" id="hSxmD56xjQ1M">

## Hypothesis

-   Tell us what your idea is and why you have chosen to pursue this
    idea.
-   We are interested in "Do Asia countries has lower affected rate of
    covid-19 than Europe countries?"
-   What two groups you are comparing:
-   **G1**: affected rate of Asia countries of covid-19; **G2**:
    affected rate of Europe countries of covid-19
-   What you will be measuring (i.e., what your response variable will
    be)
-   

<!-- -->

    total_cases_per_million

-   Is your response variable quantitative rather than categorical?
-   Yes
-   Make a prediction about what kind of difference you expect to see
    between your samples and WHY.
-   We'd expect that **G2** \> **G1** since Asia countries have
    experienced SARS.
-   Talk about how you will gather your data
-   From Github link:
    <https://github.com/owid/covid-19-data/blob/master/public/data/latest/owid-covid-latest.csv>
-   If you had unlimited resources (time, money, staff, etc.) how would
    you collect your data?
-   investigate if the provided dataset is a good random sampling subset
    of the original population.

</div>

<div class="cell markdown" id="t3ouNyrbj9y_">

## Prepare your dataset

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="wQ5cotDsae5G" outputId="8475ad96-2f26-47f7-c7b2-927a764b50bd"
trusted="true">

``` python
## load dataset from github

import pandas as pd

df = pd.read_csv('https://raw.githubusercontent.com/owid/covid-19-data/master/public/data/latest/owid-covid-latest.csv')
df.head(5)
print(df.dtypes)
```

<div class="output stream stdout">

    iso_code                                    object
    continent                                   object
    location                                    object
    last_updated_date                           object
    total_cases                                float64
                                                ...   
    population                                 float64
    excess_mortality_cumulative_absolute       float64
    excess_mortality_cumulative                float64
    excess_mortality                           float64
    excess_mortality_cumulative_per_million    float64
    Length: 67, dtype: object

</div>

</div>

<div class="cell markdown" id="P_A_5h8zkVjJ">

-   Tell us what groups you want to compare in the dataset
-   **G1** (total_cases_per_million \| continent = Asia) vs. **G2**
    (total_cases_per_million \| continent = Europe)

</div>

<div class="cell markdown" id="ulvnh2NDlIzN">

-   Print first 5 records of each group, respectively.

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="r9yljCSylQa7" outputId="d06e3f4c-5d54-4a3b-dcf1-b9a34ef4fb58">

``` python
## First 5 records of G1 (Asia)
(df[df['continent'] == 'Asia']['total_cases_per_million']).head(5)
```

<div class="output execute_result" execution_count="12">

    0       5089.089
    9     160698.975
    14     79987.040
    16    480292.915
    17     11903.828
    Name: total_cases_per_million, dtype: float64

</div>

</div>

<div class="cell code"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="QYB03xcal44h" outputId="1642cb43-8365-40d6-dc5f-9ec1ed4cc80d">

``` python
## First 5 records of G1 (Europe)
(df[df['continent'] == 'Europe']['total_cases_per_million']).head(5)
```

<div class="output execute_result" execution_count="13">

    2     117643.416
    4     599501.522
    13    660588.144
    19    104251.871
    20    404743.151
    Name: total_cases_per_million, dtype: float64

</div>

</div>
