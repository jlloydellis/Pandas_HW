

```python
import pandas as pd
import numpy as np

```


```python
# Getting the data

schools_df = pd.read_csv('../Pandas_HW/schools_complete.csv')
students_df = pd.read_csv('../Pandas_HW/students_complete.csv')

schools_df = schools_df.rename(columns={'name': 'school'})

schools_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
  </tbody>
</table>
</div>




```python
#  Merge the data

district_df = pd.merge(schools_df, students_df, on='school', how='outer')

district_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>school</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Create new table with only relevant data

school_group = district_df[["school", "type", "budget", "name", "grade", "math_score", "reading_score"]]
school_group.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>school</th>
      <th>type</th>
      <th>budget</th>
      <th>name</th>
      <th>grade</th>
      <th>math_score</th>
      <th>reading_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>1910635</td>
      <td>Paul Bradley</td>
      <td>9th</td>
      <td>79</td>
      <td>66</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>1910635</td>
      <td>Victor Smith</td>
      <td>12th</td>
      <td>61</td>
      <td>94</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>1910635</td>
      <td>Kevin Rodriguez</td>
      <td>12th</td>
      <td>60</td>
      <td>90</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>1910635</td>
      <td>Dr. Richard Scott</td>
      <td>12th</td>
      <td>58</td>
      <td>67</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>1910635</td>
      <td>Bonnie Ray</td>
      <td>9th</td>
      <td>84</td>
      <td>97</td>
    </tr>
  </tbody>
</table>
</div>




```python
# District Summary

TotalSchools = schools_df["type"].count()
TotalStudents = school_group["school"].count()
TotalBudget = sum(schools_df["budget"])
AvMath = school_group["math_score"].mean()
AvRead = school_group["reading_score"].mean()
PassMath = (school_group['math_score'] >= 65).sum()
PassRead = (school_group['reading_score'] >= 65).sum()
PerMath = PassMath / TotalStudents * 100
PerRead = PassRead / TotalStudents * 100
PassRate = (PerMath + PerRead) / 2


DistrictSum_df = pd.DataFrame({'Total Schools': [TotalSchools], 'Total Students': [TotalStudents], "Total Budget" : [TotalBudget], 
                               "Average Math Score": [AvMath], "Average Reading Score": [AvRead], "% Passing Math": [PerMath], 
                               "% Passing Reading": [PerRead], "Overall Pass Rate": [PassRate]})
DistrictSum_df = DistrictSum_df[['Total Schools', 'Total Students', "Total Budget", 
                               "Average Math Score", "Average Reading Score", "% Passing Math", 
                               "% Passing Reading", "Overall Pass Rate"]]

DistrictSum_df


```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Schools</th>
      <th>Total Students</th>
      <th>Total Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Pass Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>15</td>
      <td>39170</td>
      <td>24649428</td>
      <td>78.985371</td>
      <td>81.87784</td>
      <td>84.728108</td>
      <td>96.198621</td>
      <td>90.463365</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Getting passing rates by school

PassingScores= pd.DataFrame(school_group, columns = ['school', 'math_score', 'reading_score'])

PassingScores['Passing Math'] = np.where(PassingScores['math_score']>=65, 'yes', 'no')
PassingScores['Passing Reading'] = np.where(PassingScores['reading_score']>=65, 'yes', 'no')

MathPass = PassingScores.groupby(['school', "Passing Math"])["Passing Math"].count()
ReadPass = PassingScores.groupby(['school', "Passing Reading"])["Passing Reading"].count()
MathPass, ReadPass

MathPass, ReadPass

    
```




    (school                 Passing Math
     Bailey High School     no              1099
                            yes             3877
     Cabrera High School    yes             1858
     Figueroa High School   no               673
                            yes             2276
     Ford High School       no               597
                            yes             2142
     Griffin High School    yes             1468
     Hernandez High School  no              1032
                            yes             3603
     Holden High School     yes              427
     Huang High School      no               650
                            yes             2267
     Johnson High School    no              1049
                            yes             3712
     Pena High School       yes              962
     Rodriguez High School  no               882
                            yes             3117
     Shelton High School    yes             1761
     Thomas High School     yes             1635
     Wilson High School     yes             2283
     Wright High School     yes             1800
     Name: Passing Math, dtype: int64, school                 Passing Reading
     Bailey High School     no                  271
                            yes                4705
     Cabrera High School    yes                1858
     Figueroa High School   no                  161
                            yes                2788
     Ford High School       no                  168
                            yes                2571
     Griffin High School    yes                1468
     Hernandez High School  no                  250
                            yes                4385
     Holden High School     yes                 427
     Huang High School      no                  161
                            yes                2756
     Johnson High School    no                  263
                            yes                4498
     Pena High School       yes                 962
     Rodriguez High School  no                  215
                            yes                3784
     Shelton High School    yes                1761
     Thomas High School     yes                1635
     Wilson High School     yes                2283
     Wright High School     yes                1800
     Name: Passing Reading, dtype: int64)




```python
# School Summary

SchoolSummary = pd.DataFrame(SchoolSum.mean())

#Getting Total Students

StudentsTotal = (SchoolSum["name"].count())
SchoolSummary ["Total Students"] = StudentsTotal

#Calculating per student budget
SchoolSummary ["Budget per Student"] = (SchoolSummary[("budget")] / StudentsTotal)

#Getting school type
SchoolSummary ["School Type"] = SchoolSum["type"].unique()

#Getting No. passing Math
school_group.groupby('school')["math_score"].count()
MathPass = (school_group['math_score'] >= 65).sum()
PercentMath = MathPass / StudentsTotal * 100
SchoolSummary ["Passing Math"] = PercentMath


#Getting No. passing Reading
ReadPass = (school_group['reading_score'] >= 65).sum()
PercentRead = ReadPass / StudentsTotal * 100
SchoolSummary ["Passing Reading"] = PercentRead

#Overall Passing rate
SchoolSummary ["Overall Passing Rate"] = (PercentMath + PercentRead) / 2

#Formatting table

SchoolSummary = SchoolSummary.rename(columns={'math_score': 'Average Math Score', 'reading_score': 'Average Reading Score'})

SchoolSummary = SchoolSummary[["School Type", "Total Students", "budget", "Budget per Student", "Average Math Score", "Average Reading Score", "Passing Math", "Passing Reading", "Overall Passing Rate"]]


SchoolSummary
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>budget</th>
      <th>Budget per Student</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Passing Math</th>
      <th>Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>[District]</td>
      <td>4976</td>
      <td>3124928.0</td>
      <td>628.0</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>666.961415</td>
      <td>757.254823</td>
      <td>712.108119</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>[Charter]</td>
      <td>1858</td>
      <td>1081356.0</td>
      <td>582.0</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>1786.221744</td>
      <td>2028.040904</td>
      <td>1907.131324</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>[District]</td>
      <td>2949</td>
      <td>1884411.0</td>
      <td>639.0</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>1125.398440</td>
      <td>1277.755171</td>
      <td>1201.576806</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>[District]</td>
      <td>2739</td>
      <td>1763916.0</td>
      <td>644.0</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>1211.683096</td>
      <td>1375.721066</td>
      <td>1293.702081</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>[Charter]</td>
      <td>1468</td>
      <td>917500.0</td>
      <td>625.0</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>2260.762943</td>
      <td>2566.825613</td>
      <td>2413.794278</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>[District]</td>
      <td>4635</td>
      <td>3022020.0</td>
      <td>652.0</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>716.030205</td>
      <td>812.966559</td>
      <td>764.498382</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>[Charter]</td>
      <td>427</td>
      <td>248087.0</td>
      <td>581.0</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>7772.365340</td>
      <td>8824.590164</td>
      <td>8298.477752</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>[District]</td>
      <td>2917</td>
      <td>1910635.0</td>
      <td>655.0</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>1137.744258</td>
      <td>1291.772369</td>
      <td>1214.758313</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>[District]</td>
      <td>4761</td>
      <td>3094650.0</td>
      <td>650.0</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>697.080445</td>
      <td>791.451376</td>
      <td>744.265911</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>[Charter]</td>
      <td>962</td>
      <td>585858.0</td>
      <td>609.0</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>3449.896050</td>
      <td>3916.943867</td>
      <td>3683.419958</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>[District]</td>
      <td>3999</td>
      <td>2547363.0</td>
      <td>637.0</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>829.907477</td>
      <td>942.260565</td>
      <td>886.084021</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>[Charter]</td>
      <td>1761</td>
      <td>1056600.0</td>
      <td>600.0</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>1884.611016</td>
      <td>2139.750142</td>
      <td>2012.180579</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>[Charter]</td>
      <td>1635</td>
      <td>1043130.0</td>
      <td>638.0</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>2029.847095</td>
      <td>2304.648318</td>
      <td>2167.247706</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>[Charter]</td>
      <td>2283</td>
      <td>1319574.0</td>
      <td>578.0</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>1453.701270</td>
      <td>1650.503723</td>
      <td>1552.102497</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>[Charter]</td>
      <td>1800</td>
      <td>1049400.0</td>
      <td>583.0</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>1843.777778</td>
      <td>2093.388889</td>
      <td>1968.583333</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Top Performing Schools (By Passing Rate)


TopSchools = SchoolSummary.sort_values("Overall Passing Rate", ascending=False)


TopSchools

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>budget</th>
      <th>Budget per Student</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Passing Math</th>
      <th>Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Holden High School</th>
      <td>[Charter]</td>
      <td>427</td>
      <td>248087.0</td>
      <td>581.0</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>7772.365340</td>
      <td>8824.590164</td>
      <td>8298.477752</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>[Charter]</td>
      <td>962</td>
      <td>585858.0</td>
      <td>609.0</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>3449.896050</td>
      <td>3916.943867</td>
      <td>3683.419958</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>[Charter]</td>
      <td>1468</td>
      <td>917500.0</td>
      <td>625.0</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>2260.762943</td>
      <td>2566.825613</td>
      <td>2413.794278</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>[Charter]</td>
      <td>1635</td>
      <td>1043130.0</td>
      <td>638.0</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>2029.847095</td>
      <td>2304.648318</td>
      <td>2167.247706</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>[Charter]</td>
      <td>1761</td>
      <td>1056600.0</td>
      <td>600.0</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>1884.611016</td>
      <td>2139.750142</td>
      <td>2012.180579</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>[Charter]</td>
      <td>1800</td>
      <td>1049400.0</td>
      <td>583.0</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>1843.777778</td>
      <td>2093.388889</td>
      <td>1968.583333</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>[Charter]</td>
      <td>1858</td>
      <td>1081356.0</td>
      <td>582.0</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>1786.221744</td>
      <td>2028.040904</td>
      <td>1907.131324</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>[Charter]</td>
      <td>2283</td>
      <td>1319574.0</td>
      <td>578.0</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>1453.701270</td>
      <td>1650.503723</td>
      <td>1552.102497</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>[District]</td>
      <td>2739</td>
      <td>1763916.0</td>
      <td>644.0</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>1211.683096</td>
      <td>1375.721066</td>
      <td>1293.702081</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>[District]</td>
      <td>2917</td>
      <td>1910635.0</td>
      <td>655.0</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>1137.744258</td>
      <td>1291.772369</td>
      <td>1214.758313</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>[District]</td>
      <td>2949</td>
      <td>1884411.0</td>
      <td>639.0</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>1125.398440</td>
      <td>1277.755171</td>
      <td>1201.576806</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>[District]</td>
      <td>3999</td>
      <td>2547363.0</td>
      <td>637.0</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>829.907477</td>
      <td>942.260565</td>
      <td>886.084021</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>[District]</td>
      <td>4635</td>
      <td>3022020.0</td>
      <td>652.0</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>716.030205</td>
      <td>812.966559</td>
      <td>764.498382</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>[District]</td>
      <td>4761</td>
      <td>3094650.0</td>
      <td>650.0</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>697.080445</td>
      <td>791.451376</td>
      <td>744.265911</td>
    </tr>
    <tr>
      <th>Bailey High School</th>
      <td>[District]</td>
      <td>4976</td>
      <td>3124928.0</td>
      <td>628.0</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>666.961415</td>
      <td>757.254823</td>
      <td>712.108119</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Bottom Performing Schools (By Passing Rate)


BottomSchools = SchoolSummary.sort_values("Overall Passing Rate")


BottomSchools
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>budget</th>
      <th>Budget per Student</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Passing Math</th>
      <th>Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>[District]</td>
      <td>4976</td>
      <td>3124928.0</td>
      <td>628.0</td>
      <td>77.048432</td>
      <td>81.033963</td>
      <td>666.961415</td>
      <td>757.254823</td>
      <td>712.108119</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>[District]</td>
      <td>4761</td>
      <td>3094650.0</td>
      <td>650.0</td>
      <td>77.072464</td>
      <td>80.966394</td>
      <td>697.080445</td>
      <td>791.451376</td>
      <td>744.265911</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>[District]</td>
      <td>4635</td>
      <td>3022020.0</td>
      <td>652.0</td>
      <td>77.289752</td>
      <td>80.934412</td>
      <td>716.030205</td>
      <td>812.966559</td>
      <td>764.498382</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>[District]</td>
      <td>3999</td>
      <td>2547363.0</td>
      <td>637.0</td>
      <td>76.842711</td>
      <td>80.744686</td>
      <td>829.907477</td>
      <td>942.260565</td>
      <td>886.084021</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>[District]</td>
      <td>2949</td>
      <td>1884411.0</td>
      <td>639.0</td>
      <td>76.711767</td>
      <td>81.158020</td>
      <td>1125.398440</td>
      <td>1277.755171</td>
      <td>1201.576806</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>[District]</td>
      <td>2917</td>
      <td>1910635.0</td>
      <td>655.0</td>
      <td>76.629414</td>
      <td>81.182722</td>
      <td>1137.744258</td>
      <td>1291.772369</td>
      <td>1214.758313</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>[District]</td>
      <td>2739</td>
      <td>1763916.0</td>
      <td>644.0</td>
      <td>77.102592</td>
      <td>80.746258</td>
      <td>1211.683096</td>
      <td>1375.721066</td>
      <td>1293.702081</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>[Charter]</td>
      <td>2283</td>
      <td>1319574.0</td>
      <td>578.0</td>
      <td>83.274201</td>
      <td>83.989488</td>
      <td>1453.701270</td>
      <td>1650.503723</td>
      <td>1552.102497</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>[Charter]</td>
      <td>1858</td>
      <td>1081356.0</td>
      <td>582.0</td>
      <td>83.061895</td>
      <td>83.975780</td>
      <td>1786.221744</td>
      <td>2028.040904</td>
      <td>1907.131324</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>[Charter]</td>
      <td>1800</td>
      <td>1049400.0</td>
      <td>583.0</td>
      <td>83.682222</td>
      <td>83.955000</td>
      <td>1843.777778</td>
      <td>2093.388889</td>
      <td>1968.583333</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>[Charter]</td>
      <td>1761</td>
      <td>1056600.0</td>
      <td>600.0</td>
      <td>83.359455</td>
      <td>83.725724</td>
      <td>1884.611016</td>
      <td>2139.750142</td>
      <td>2012.180579</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>[Charter]</td>
      <td>1635</td>
      <td>1043130.0</td>
      <td>638.0</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>2029.847095</td>
      <td>2304.648318</td>
      <td>2167.247706</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>[Charter]</td>
      <td>1468</td>
      <td>917500.0</td>
      <td>625.0</td>
      <td>83.351499</td>
      <td>83.816757</td>
      <td>2260.762943</td>
      <td>2566.825613</td>
      <td>2413.794278</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>[Charter]</td>
      <td>962</td>
      <td>585858.0</td>
      <td>609.0</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>3449.896050</td>
      <td>3916.943867</td>
      <td>3683.419958</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>[Charter]</td>
      <td>427</td>
      <td>248087.0</td>
      <td>581.0</td>
      <td>83.803279</td>
      <td>83.814988</td>
      <td>7772.365340</td>
      <td>8824.590164</td>
      <td>8298.477752</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Math and Reading Scores by Grade

Grade_group = district_df[["school", "grade", "math_score", "reading_score"]]
Grade_group.groupby(by=['school', 'grade']).mean()

```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>math_score</th>
      <th>reading_score</th>
    </tr>
    <tr>
      <th>school</th>
      <th>grade</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="4" valign="top">Bailey High School</th>
      <th>10th</th>
      <td>76.996772</td>
      <td>80.907183</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>77.515588</td>
      <td>80.945643</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>76.492218</td>
      <td>80.912451</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>77.083676</td>
      <td>81.303155</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Cabrera High School</th>
      <th>10th</th>
      <td>83.154506</td>
      <td>84.253219</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>82.765560</td>
      <td>83.788382</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.277487</td>
      <td>84.287958</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.094697</td>
      <td>83.676136</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Figueroa High School</th>
      <th>10th</th>
      <td>76.539974</td>
      <td>81.408912</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>76.884344</td>
      <td>80.640339</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>77.151369</td>
      <td>81.384863</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>76.403037</td>
      <td>81.198598</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Ford High School</th>
      <th>10th</th>
      <td>77.672316</td>
      <td>81.262712</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>76.918058</td>
      <td>80.403642</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>76.179963</td>
      <td>80.662338</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>77.361345</td>
      <td>80.632653</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Griffin High School</th>
      <th>10th</th>
      <td>84.229064</td>
      <td>83.706897</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.842105</td>
      <td>84.288089</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.356164</td>
      <td>84.013699</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>82.044010</td>
      <td>83.369193</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Hernandez High School</th>
      <th>10th</th>
      <td>77.337408</td>
      <td>80.660147</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>77.136029</td>
      <td>81.396140</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>77.186567</td>
      <td>80.857143</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>77.438495</td>
      <td>80.866860</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Holden High School</th>
      <th>10th</th>
      <td>83.429825</td>
      <td>83.324561</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>85.000000</td>
      <td>83.815534</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>82.855422</td>
      <td>84.698795</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.787402</td>
      <td>83.677165</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Huang High School</th>
      <th>10th</th>
      <td>75.908735</td>
      <td>81.512386</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>76.446602</td>
      <td>81.417476</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>77.225641</td>
      <td>80.305983</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>77.027251</td>
      <td>81.290284</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Johnson High School</th>
      <th>10th</th>
      <td>76.691117</td>
      <td>80.773431</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>77.491653</td>
      <td>80.616027</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>76.863248</td>
      <td>81.227564</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>77.187857</td>
      <td>81.260714</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Pena High School</th>
      <th>10th</th>
      <td>83.372000</td>
      <td>83.612000</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>84.328125</td>
      <td>84.335938</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>84.121547</td>
      <td>84.591160</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.625455</td>
      <td>83.807273</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Rodriguez High School</th>
      <th>10th</th>
      <td>76.612500</td>
      <td>80.629808</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>76.395626</td>
      <td>80.864811</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>77.690748</td>
      <td>80.376426</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>76.859966</td>
      <td>80.993127</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Shelton High School</th>
      <th>10th</th>
      <td>82.917411</td>
      <td>83.441964</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.383495</td>
      <td>84.373786</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.778976</td>
      <td>82.781671</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.420755</td>
      <td>84.122642</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Thomas High School</th>
      <th>10th</th>
      <td>83.087886</td>
      <td>84.254157</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.498795</td>
      <td>83.585542</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.497041</td>
      <td>83.831361</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.590022</td>
      <td>83.728850</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Wilson High School</th>
      <th>10th</th>
      <td>83.724422</td>
      <td>84.021452</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.195326</td>
      <td>83.764608</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.035794</td>
      <td>84.317673</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.085578</td>
      <td>83.939778</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">Wright High School</th>
      <th>10th</th>
      <td>84.010288</td>
      <td>83.812757</td>
    </tr>
    <tr>
      <th>11th</th>
      <td>83.836782</td>
      <td>84.156322</td>
    </tr>
    <tr>
      <th>12th</th>
      <td>83.644986</td>
      <td>84.073171</td>
    </tr>
    <tr>
      <th>9th</th>
      <td>83.264706</td>
      <td>83.833333</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Scores by School Spending
bins = [575, 600, 625, 650, 675]

bin_names = ["575-600", "600-625", "625-650", "650+"]

pd.cut(SchoolSummary["Budget per Student"], bins, labels=bin_names)

```




    school
    Bailey High School       625-650
    Cabrera High School      575-600
    Figueroa High School     625-650
    Ford High School         625-650
    Griffin High School      600-625
    Hernandez High School       650+
    Holden High School       575-600
    Huang High School           650+
    Johnson High School      625-650
    Pena High School         600-625
    Rodriguez High School    625-650
    Shelton High School      575-600
    Thomas High School       625-650
    Wilson High School       575-600
    Wright High School       575-600
    Name: Budget per Student, dtype: category
    Categories (4, object): [575-600 < 600-625 < 625-650 < 650+]




```python
SchoolSummary["Scores by Spending"] = pd.cut(SchoolSummary["Budget per Student"], bins, labels=bin_names)

Score_Spending = SchoolSummary.groupby("Scores by Spending")

Score_Spending.max()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>budget</th>
      <th>Budget per Student</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Passing Math</th>
      <th>Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
    <tr>
      <th>Scores by Spending</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>575-600</th>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574.0</td>
      <td>600.0</td>
      <td>83.803279</td>
      <td>83.989488</td>
      <td>7772.365340</td>
      <td>8824.590164</td>
      <td>8298.477752</td>
    </tr>
    <tr>
      <th>600-625</th>
      <td>Charter</td>
      <td>1468</td>
      <td>917500.0</td>
      <td>625.0</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>3449.896050</td>
      <td>3916.943867</td>
      <td>3683.419958</td>
    </tr>
    <tr>
      <th>625-650</th>
      <td>District</td>
      <td>4976</td>
      <td>3124928.0</td>
      <td>650.0</td>
      <td>83.418349</td>
      <td>83.848930</td>
      <td>2029.847095</td>
      <td>2304.648318</td>
      <td>2167.247706</td>
    </tr>
    <tr>
      <th>650+</th>
      <td>District</td>
      <td>4635</td>
      <td>3022020.0</td>
      <td>655.0</td>
      <td>77.289752</td>
      <td>81.182722</td>
      <td>1137.744258</td>
      <td>1291.772369</td>
      <td>1214.758313</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Scores by School Size

bins = [0, 1500, 3000, 5000]

bin_names = ["Small", "Medium", "Large"]

pd.cut(SchoolSummary["Total Students"], bins, labels=bin_names)

SchoolSummary["Scores by School Size"] = pd.cut(SchoolSummary["Total Students"], bins, labels=bin_names)

Score_Size = SchoolSummary.groupby("Scores by School Size")

Score_Size.max()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>budget</th>
      <th>Budget per Student</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Passing Math</th>
      <th>Passing Reading</th>
      <th>Overall Passing Rate</th>
      <th>Scores by Spending</th>
    </tr>
    <tr>
      <th>Scores by School Size</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Small</th>
      <td>Charter</td>
      <td>1468</td>
      <td>917500.0</td>
      <td>625.0</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>7772.365340</td>
      <td>8824.590164</td>
      <td>8298.477752</td>
      <td>600-625</td>
    </tr>
    <tr>
      <th>Medium</th>
      <td>District</td>
      <td>2949</td>
      <td>1910635.0</td>
      <td>655.0</td>
      <td>83.682222</td>
      <td>83.989488</td>
      <td>2029.847095</td>
      <td>2304.648318</td>
      <td>2167.247706</td>
      <td>650+</td>
    </tr>
    <tr>
      <th>Large</th>
      <td>District</td>
      <td>4976</td>
      <td>3124928.0</td>
      <td>652.0</td>
      <td>77.289752</td>
      <td>81.033963</td>
      <td>829.907477</td>
      <td>942.260565</td>
      <td>886.084021</td>
      <td>650+</td>
    </tr>
  </tbody>
</table>
</div>




```python
SchoolSummary['School Type'] = np.where(SchoolSummary['School Type'] == 'Charter', 1, 2)

bins = [0, 1, 2]

bin_names = ["Charter", "District"]

pd.cut(SchoolSummary["School Type"], bins, labels=bin_names)

SchoolSummary["Scores by School Type"] = pd.cut(SchoolSummary["School Type"], bins, labels=bin_names)

Score_Type = SchoolSummary.groupby("Scores by School Type")

Score_Type.max()


```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>budget</th>
      <th>Budget per Student</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>Passing Math</th>
      <th>Passing Reading</th>
      <th>Overall Passing Rate</th>
      <th>Scores by Spending</th>
      <th>Scores by School Size</th>
    </tr>
    <tr>
      <th>Scores by School Type</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Charter</th>
      <td>1</td>
      <td>2283</td>
      <td>1319574.0</td>
      <td>638.0</td>
      <td>83.839917</td>
      <td>84.044699</td>
      <td>7772.365340</td>
      <td>8824.590164</td>
      <td>8298.477752</td>
      <td>625-650</td>
      <td>Medium</td>
    </tr>
    <tr>
      <th>District</th>
      <td>2</td>
      <td>4976</td>
      <td>3124928.0</td>
      <td>655.0</td>
      <td>77.289752</td>
      <td>81.182722</td>
      <td>1211.683096</td>
      <td>1375.721066</td>
      <td>1293.702081</td>
      <td>650+</td>
      <td>Large</td>
    </tr>
  </tbody>
</table>
</div>


