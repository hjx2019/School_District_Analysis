# School District Analysis

## Overview of the school district analysis

> We need to see the average math&reading scores and passing rate of each school, and by grade/ budget/ school size/ school type.

> Environment: Python 3.7, Windows10

### District summary

* Clean data - name modify   **(In-1)**
* Clean data - THS 9th reading/math remove(change to Nan)  **(In-3 4 / Out-5 6)**
* Join table - merge school/student data   **(In-7)**
* Describe _total data_     **(Out-14)**

### school summary

* Describe data _by school_    **(Out-17)**
* Get THS 10th ~ 12th grade data, replace the old THS data in total table    **(Out-28)**
* Low/High performance school     **(out-29 30)**
* Average math/reading score by school and grade    **(Out-35 36)**

* Score by spending   **(Out-40)**
* Score by school size   **(Out-44)**
* Score by school type   **(Out-47)**

## Results

### District Summary key steps and functions used

1. Read data from file and get DataFrame
2. use _df_str.replace()_ to clean the _student_name_
3. Use _Numpy_ to change Thomas High School 9th grade reading/math to Nan
4. Join school/student table use _pd.merge_ on "school name"
5. Passing rate - use _logical comparison_ and _.count()_
6. Use  _.sum()/ .mean()/ .count()_, get _student count/ average score/ budget ..._
7. Using _'school name'_ as index, _pd.DataFrame_ joins all arrays into a dataframe
8. Formating with _.map()_ and _"{:,}".format_


> Output 14
![image](https://user-images.githubusercontent.com/48306359/126084678-274d0063-1aa4-41d3-b4d9-5f437b0f0175.png)


### School summary key steps and functions used

1. use _value_counts()_ on joined dataframe get student count for each school
2. budget of each student = budget of a school / student count of the school
3. use _.groupby('school name').mean()_ get the average math/reading score
4. filter the passing student list -> groupby() to get passing student count
5. get passing student rate = passing student count / student count of the school
6. join all data using _pd.DataFrame_ , and formatting with _.map()_

![image](https://user-images.githubusercontent.com/48306359/126084722-b3b777e5-e694-4664-91a2-82679ed2e78b.png)

7. use _.loc_ get same data of **Thomas High School Grade 10~12**
8. replace the data of THS, using _.loc_

![image](https://user-images.githubusercontent.com/48306359/126084755-86a7fd35-02b1-4f72-a67d-539ce08964cc.png)


9. use _sort_values()_ for top/bottom performing schools

![image](https://user-images.githubusercontent.com/48306359/126084787-003e2d85-4c83-46b8-a1b4-3cd53d882ca9.png)
![image](https://user-images.githubusercontent.com/48306359/126084795-6e1e2269-fc6e-4c83-8c11-220e6bdd371a.png)


10. use _groupby()_ get the average data for each Grade. (Pivot_table could be easier)

![image](https://user-images.githubusercontent.com/48306359/126084825-d67cf94b-e644-45f3-b8f7-5cad6a699910.png)
![image](https://user-images.githubusercontent.com/48306359/126084841-e7c908fa-a0b4-4104-9e67-75f60f508d81.png)

11. use _bins, pd.cut(), groupby_ get the score sorted by budget per student, and by School size

![image](https://user-images.githubusercontent.com/48306359/126084851-070e7510-0283-43c6-b065-570abd531a64.png)
![image](https://user-images.githubusercontent.com/48306359/126084856-71c59c67-bbeb-4088-ba86-061a5f012af8.png)

12. use _groupby_ get score by school type

![image](https://user-images.githubusercontent.com/48306359/126084862-164bdf78-c079-440d-8239-3c2478a48f8c.png)


### THS 9th graders' data impact on THS data

When the 9th graders' scores are removed, average scores of Thomas High school dropped from a reasonable value. So we use step 7\8 in school summary to fix it.

> after 9th graders' scores removed:

![image](https://user-images.githubusercontent.com/48306359/126084722-b3b777e5-e694-4664-91a2-82679ed2e78b.png)

> fixed with 10th ~ 12th graders' average score:

![image](https://user-images.githubusercontent.com/48306359/126084755-86a7fd35-02b1-4f72-a67d-539ce08964cc.png)

### Other influences

* Math and reading scores by grade: 
  - 9th grade has isolated data as Nan, no impact on other groups.

* Scores by school spending / school size / school type
  - these 3 tables are calculated from the modified _School summary data_, so there's no effect on the result.
  - if we don't modify the _school summary data_, the _passing percentages_ in _Thomas High School_ will always be lower than the actual.
  - additionally, as a suggestion, _weighted-average (on school size)_ should be used instead of _average_ in these 3 values' calculation.


### Summary

There's no effect on the result.
