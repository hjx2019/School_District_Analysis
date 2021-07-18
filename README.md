# School_District_Analysis

> Data Analysis Boot Camp in UofT, Challenge4, by Jiaxin Hao (Joshua)

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

Pic paste

### School summary key steps and functions used

1. use _value_counts()_ on joined dataframe get student count for each school
2. budget of each student = budget of a school / student count of the school
3. use _.groupby('school name').mean()_ get the average math/reading score
4. filter the passing student list -> groupby() to get passing student count
5. get passing student rate = passing student count / student count of the school
6. join all data using _pd.DataFrame_ , and formatting with _.map()_

7. use _.loc_ get same data of **Thomas High School Grade 10~12**
8. replace the data of THS, using _.loc_

9. use _sort_values()_ for top/bottom performing schools
10. use _groupby()_ get the average data for each Grade. (Pivot_table could be easier)

11. use _bins, pd.cut(), groupby_ get the score sorted by budget per student, and by School size
12. use _groupby_ get score by school type


### THS 9th graders' data impact

When the 9th graders' scores are removed, average scores of Thomas High school dropped from a reasonable value. So we use step 7\8 in school summary to fix it.

> after 9th graders' scores removed:


> fixed with 10th ~ 12th graders' average score:



### Other influences

* Math and reading scores by grade: 
  - 9th grade has isolated data as Nan, no impact on other groups.

* Scores by school spending / school size / school type
  - these 3 table are calculated from the modified School summary data, so there's no effect on the result.
  - if we don't modify the school summary data, the passing rates in THS will always be lower than the actual.
  - additionally, as a suggestion, _weighted-average (on school size)_ should be used instead of _average_ in these 3 values' calculation.


### Summary

There's no effect on the the result.
