Student Droput Prediction
================
Kerven Zephir
March 27, 2024

# Project Title

Predicting Student Dropout

# Motivation

Primary motivations is to identify predictors of student dropout and
factors contributing to academic success. By analyzing variables such as
application mode, marital status, chosen course, and more, we aim to
uncover patterns and correlations that can shed light on why some
students persist while others discontinue their studies.

# Tools Used

- Definitions and principles of exploratory data analysis (EDA)
- Programming language (R) for implementation
- R packages for data manipulation, analysis, and visualization.
- Random Forest machine learning algorithm

# Data Understanding

Here are the column names:

    ##  [1] "Marital.status"                                
    ##  [2] "Application.mode"                              
    ##  [3] "Application.order"                             
    ##  [4] "Course"                                        
    ##  [5] "Daytime.evening.attendance"                    
    ##  [6] "Previous.qualification"                        
    ##  [7] "Nationality"                                   
    ##  [8] "Mother.s.qualification"                        
    ##  [9] "Father.s.qualification"                        
    ## [10] "Mother.s.occupation"                           
    ## [11] "Father.s.occupation"                           
    ## [12] "Displaced"                                     
    ## [13] "Educational.special.needs"                     
    ## [14] "Debtor"                                        
    ## [15] "Tuition.fees.up.to.date"                       
    ## [16] "Gender"                                        
    ## [17] "Scholarship.holder"                            
    ## [18] "Age.at.enrollment"                             
    ## [19] "International"                                 
    ## [20] "Curricular.units.1st.sem..credited."           
    ## [21] "Curricular.units.1st.sem..enrolled."           
    ## [22] "Curricular.units.1st.sem..evaluations."        
    ## [23] "Curricular.units.1st.sem..approved."           
    ## [24] "Curricular.units.1st.sem..grade."              
    ## [25] "Curricular.units.1st.sem..without.evaluations."
    ## [26] "Curricular.units.2nd.sem..credited."           
    ## [27] "Curricular.units.2nd.sem..enrolled."           
    ## [28] "Curricular.units.2nd.sem..evaluations."        
    ## [29] "Curricular.units.2nd.sem..approved."           
    ## [30] "Curricular.units.2nd.sem..grade."              
    ## [31] "Curricular.units.2nd.sem..without.evaluations."
    ## [32] "Unemployment.rate"                             
    ## [33] "Inflation.rate"                                
    ## [34] "GDP"                                           
    ## [35] "Target"

## Data Description

- Marital status: The student’s current marital status. (Categorical)
- Application mode: The method used by the student to apply.
  (Categorical)
- Application order: The sequence of the student’s applications.
  (Numerical)
- Course: The program or course the student is enrolled in.
  (Categorical)
- Daytime/evening attendance: The student’s class attendance time.
  (Categorical)
- Previous qualification: The student’s prior educational qualification.
  (Categorical)
- Nationality: The student’s country of nationality. (Categorical)
- Mother’s qualification: The educational level of the student’s mother.
  (Categorical)
- Father’s qualification: The educational level of the student’s father.
  (Categorical)
- Mother’s occupation: The profession of the student’s mother.
  (Categorical)
- Father’s occupation: The profession of the student’s father.
  (Categorical)
- Displaced: Indicates whether the student is displaced. (Categorical)
- Educational special needs: Indicates if the student has special
  educational needs. (Categorical)
- Debtor: Indicates if the student is in debt. (Categorical)
- Tuition fees up to date: Indicates if the student’s tuition fees are
  paid up to date. (Categorical)
- Gender: The student’s gender. (Categorical)
- Scholarship holder: Indicates if the student holds a scholarship.
  (Categorical)
- Age at enrollment: The age of the student when enrolled. (Numerical)
- International: Indicates if the student is an international student.
  (Categorical)
- Curricular units 1st sem (credited): Number of units credited by the
  student in the first semester. (Numerical)
- Curricular units 1st sem (enrolled): Number of units enrolled by the
  student in the first semester. (Numerical)
- Curricular units 1st sem (evaluations): Number of units evaluated by
  the student in the first semester. (Numerical)
- Curricular units 1st sem (approved): Number of units approved by the
  student in the first semester. (Numerical)

# Solving Process

1.  **Data Preparation and Cleaning**
    - Began with data understanding, focusing on variables like marital
      status, application mode, course, and others.
    - Removed variables like ‘Nationality’ and ‘International’ due to
      their limited variability and predictive power.
2.  **Exploratory Data Analysis (EDA)**
    - Conducted EDA to identify patterns and correlations within the
      data, utilizing R for data manipulation and visualization.
3.  **Statistical Analysis**
    - Performed association analysis using Cramer’s V to determine the
      strength of relationships between categorical variables.
    - Conducted Chi-square tests to evaluate the significance of these
      associations.
4.  **Feature Selection**
    - Selected relevant predictors for the model while excluding
      variables that provided less predictive power, improving model
      efficiency and interpretability.
5.  **Model Building and Evaluation**
    - Implemented machine learning techniques, specifically Random
      Forest, to predict student dropout.
    - Utilized cross-validation and computed AUC to assess the model’s
      predictive performance.
6.  **Results Interpretation**
    - Analyzed the model results to understand the influence of
      different variables on student dropout rates.
    - Identified key factors that have a strong association with student
      academic outcomes.

# Justification for Removing Nationality and International Variables

As shown in the table, the overwhelming number of students are
Portuguese nationals.

    ## 
    ##               Angolan             Brazilian          Cape Verdean 
    ##                     2                    38                    13 
    ##             Colombian                 Cuban                 Dutch 
    ##                     1                     1                     1 
    ##               English                German               Guinean 
    ##                     1                     2                     5 
    ##               Italian            Lithuanian               Mexican 
    ##                     3                     1                     2 
    ## Moldova (Republic of)            Mozambican            Portuguese 
    ##                     3                     2                  4314 
    ##              Romanian               Russian             Santomean 
    ##                     2                     2                    14 
    ##               Spanish               Turkish             Ukrainian 
    ##                    13                     1                     3

The Nationality variable, predominantly composed of Portuguese
individuals, lacks variability and predictive power due to its
homogeneity. Similarly, the International variable, representing a small
subset, does not significantly influence our predictive models.

Removing these variables allows us to focus on predictors with more
meaningful insights, enhancing the efficiency and interpretability of
our predictive models. This decision also mitigates issues like
multicollinearity, ensuring robust and reliable modeling outcomes.

\#Exploratory Data Analysis

## Cramer’s V

Cramer’s V is left only to the categorical variables

Cramer’s V is a measure of association used to assess the strength of
the relationship between categorical variables in a contingency table.
It extends the concept of Pearson’s chi-squared test for independence
and is valuable in determining the degree of association between
variables with more than two levels.

Cramer’s V ranges from 0 to 1. - A value closer to 0 indicates a weak
association between the variables. - A value closer to 1 indicates a
strong association between the variables.

In this project, analyzing Cramer’s V can help reveal which factors,
such as demographic data, social-economic factors, and academic
performance, significantly influence student outcomes like dropout rates
or academic success.

![](STAProject-4--1--2--1--1-upload_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

1.  **Tuition Fees Up to Date (0.153)**: There is a strong association
    between whether tuition fees are up to date and the target variable.
    This suggests that students whose tuition fees are up to date are
    more likely to exhibit certain characteristics related to the target
    variable.

2.  **Course (0.103)**: There is a moderate association between the
    course chosen by students and the target variable. This implies that
    the choice of course may have an impact on the outcome represented
    by the target variable.

3.  **Scholarship Holder (0.108)**: There is a moderate association
    between being a scholarship holder and the target variable. This
    indicates that students with scholarships may have different
    outcomes compared to those without scholarships.

4.  **Application Mode (0.094)**: There is a moderate association
    between the application mode and the target variable. This suggests
    that the method of application could influence the outcome
    represented by the target variable.

5.  **Gender (0.081)**: There is a moderate association between gender
    and the target variable. This implies that gender may play a role in
    determining the outcome represented by the target variable.

6.  **Father’s Occupation (0.07)**: There is a weak association between
    the father’s occupation and the target variable. This suggests that
    the father’s occupation may have a limited influence on the outcome
    represented by the target variable.

7.  **Mother’s Occupation (0.074)**: There is a weak association between
    the mother’s occupation and the target variable. This implies that
    the mother’s occupation may have a limited impact on the outcome
    represented by the target variable.

8.  **Previous Qualification (0.064)**: There is a weak association
    between the previous qualification and the target variable. This
    suggests that the previous qualification may not strongly predict
    the outcome represented by the target variable.

9.  **Displaced (0.04)**: There is a weak association between
    displacement status and the target variable. This implies that being
    displaced may not strongly influence the outcome represented by the
    target variable.

10. **Marital Status (0.035)**: There is a very weak association between
    marital status and the target variable. This suggests that marital
    status may have minimal impact on the outcome represented by the
    target variable.

11. **Daytime/Evening Attendance (0.028)**: There is a very weak
    association between attendance mode and the target variable. This
    implies that the mode of attendance may not strongly predict the
    outcome represented by the target variable.

12. **Educational Special Needs (0.004)**: There is almost no
    association between having educational special needs and the target
    variable. This suggests that having special needs may not influence
    the outcome represented by the target variable.

These interpretations provide a clearer understanding of how each
attribute is associated with the target variable, ranging from strong
associations that indicate predictive value to weak associations that
suggest limited influence.

## Chi square and P value

The chi-square and p value tests are left only to the categorical
variables.

### Chi-square Test Results

| Variable                   | Chi-square | df  | P-value    | Cramer’s V |
|----------------------------|------------|-----|------------|------------|
| Marital.status             | 60.083     | 10  | 1.9839e-06 | 0.035      |
| Application.mode           | 462.05     | 34  | \< 0.001   | 0.094      |
| Course                     | 588.11     | 32  | \< 0.001   | 0.103      |
| Daytime.evening.attendance | 27.583     | 2   | 1.1256e-04 | 0.028      |
| Previous.qualification     | 217.89     | 32  | \< 0.001   | 0.064      |
| Mother.s.qualification     | 219.85     | 56  | 1.7841e-13 | 0.064      |
| Father.s.qualification     | 230.21     | 66  | 6.6843e-12 | 0.065      |
| Mother.s.occupation        | 301.03     | 62  | \< 0.001   | 0.074      |
| Father.s.occupation        | 271.29     | 90  | 3.4153e-11 | 0.07       |
| Displaced                  | 57.744     | 2   | 1.2913e-10 | 0.04       |
| Educational.special.needs  | 0.62706    | 2   | 0.99593    | 0.004      |
| Debtor                     | 256.05     | 2   | \< 0.001   | 0.086      |
| Tuition.fees.up.to.date    | 812.49     | 2   | \< 0.001   | 0.153      |
| Gender                     | 233.72     | 2   | \< 0.001   | 0.081      |
| Scholarship.holder         | 434.93     | 2   | \< 0.001   | 0.108      |

Note: “\< 0.001” indicates a p-value smaller than 0.001, suggesting
strong statistical significance.

### Analysis of Chi-square Test Results

The Chi-square test results for various variables related to students’
academic and demographic backgrounds reveal insights into how these
factors may be associated with certain outcomes.

- **Marital Status**: With a Chi-square value of 60.083 and a p-value of
  1.9839e-06, marital status has a statistically significant association
  with the outcome variable. However, the Cramer’s V value of 0.035
  indicates a weak association.

- **Application Mode**: This variable shows a strong association with
  the outcome, evidenced by a Chi-square value of 462.05 and a p-value
  less than 0.001. The Cramer’s V of 0.094 suggests a moderate
  association.

- **Course**: The course chosen by students is significantly associated
  with the outcome (Chi-square = 588.11, p-value \< 0.001), and a
  Cramer’s V of 0.103 indicates a moderate association strength.

- **Daytime/Evening Attendance**: This variable, with a Chi-square of
  27.583 and a p-value of 1.1256e-04, shows a significant but weak
  association with the outcome, as reflected by a Cramer’s V of 0.028.

- **Previous Qualification**: Shows a moderate association with the
  outcome (Chi-square = 217.89, p-value \< 0.001, Cramer’s V = 0.064).

- **Parents’ Qualifications and Occupations**: Both the qualifications
  and occupations of students’ parents (mother and father) show
  statistically significant associations with the outcome, with moderate
  Cramer’s V values ranging from 0.064 to 0.074.

- **Displaced**: Indicates a significant relationship with the outcome
  (Chi-square = 57.744, p-value = 1.2913e-10), with a Cramer’s V of
  0.04.

- **Educational Special Needs**: The association is not significant
  (p-value = 0.99593), and the Cramer’s V value of 0.004 indicates a
  very weak association.

- **Debtor**: With a Chi-square of 256.05 and a p-value \< 0.001, there
  is a significant association, and the Cramer’s V of 0.086 suggests a
  moderate relationship.

- **Tuition Fees Up to Date**: This shows the strongest association
  among the variables tested (Chi-square = 812.49, p-value \< 0.001),
  with a Cramer’s V of 0.153 indicating a relatively strong association.

- **Gender**: Gender has a moderate association with the outcome
  (Chi-square = 233.72, p-value \< 0.001, Cramer’s V = 0.081).

- **Scholarship Holder**: Indicates a significant and moderate
  association with the outcome (Chi-square = 434.93, p-value \< 0.001,
  Cramer’s V = 0.108).

#### Conclusions

Variables such as `Application Mode`, `Course`, and
`Tuition Fees Up to Date` demonstrate strong and statistically
significant associations with the academic outcomes of students, with
moderate to strong effect sizes. These findings suggest that these
factors are important predictors of academic success. In contrast,
variables like `Educational Special Needs` show little to no
association, indicating they may have minimal impact on the outcomes
measured.

This analysis underscores the complexity of factors influencing academic
success and highlights the importance of considering a wide range of
variables in educational research.
\######################################\|

``` r
library(polycor)
```

    ## Warning: package 'polycor' was built under R version 4.3.3

``` r
library(dplyr)

# Ensure Target is numeric if it's not already
data_test$Target <- as.numeric(data_test$Target)

# Selecting only numeric columns for correlation analysis, excluding 'Target'
quantitative_attributes <- data_test %>%
  select(where(is.numeric)) %>%
  select(-Target)  # Excluding the 'Target' column explicitly

# Calculate polyserial correlations only for numeric attributes
poly_corr_results <- sapply(quantitative_attributes, function(col) {
  polyserial(col, data_test$Target)
})

# Setting names for results
names(poly_corr_results) <- names(quantitative_attributes)
print(poly_corr_results)
```

    ##                              Application.order 
    ##                                    0.030624315 
    ##                              Age.at.enrollment 
    ##                                   -0.225614635 
    ##            Curricular.units.1st.sem..credited. 
    ##                                   -0.002754627 
    ##            Curricular.units.1st.sem..enrolled. 
    ##                                    0.058157246 
    ##         Curricular.units.1st.sem..evaluations. 
    ##                                    0.140057679 
    ##            Curricular.units.1st.sem..approved. 
    ##                                    0.324485246 
    ##               Curricular.units.1st.sem..grade. 
    ##                                    0.390902420 
    ## Curricular.units.1st.sem..without.evaluations. 
    ##                                   -0.024109092 
    ##            Curricular.units.2nd.sem..credited. 
    ##                                   -0.002713628 
    ##            Curricular.units.2nd.sem..enrolled. 
    ##                                    0.067827387 
    ##         Curricular.units.2nd.sem..evaluations. 
    ##                                    0.217347673 
    ##            Curricular.units.2nd.sem..approved. 
    ##                                    0.392561105 
    ##               Curricular.units.2nd.sem..grade. 
    ##                                    0.479851561 
    ## Curricular.units.2nd.sem..without.evaluations. 
    ##                                   -0.045827266 
    ##                              Unemployment.rate 
    ##                                   -0.041677331 
    ##                                 Inflation.rate 
    ##                                   -0.024369176 
    ##                                            GDP 
    ##                                    0.041422931

``` r
# Creating a data frame for plotting
poly_corr_df <- data.frame(Attribute = names(poly_corr_results), Polyserial_Correlation = poly_corr_results)

# Load ggplot2 for plotting
library(ggplot2)
ggplot(poly_corr_df, aes(x = Attribute, y = Polyserial_Correlation)) +
  geom_bar(stat = "identity", fill = "pink", color = "black") +
  labs(title = "Polyserial Correlation of Quantitative Attributes with Target",
       x = "Attribute",
       y = "Polyserial Correlation") +
  theme_minimal() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1))
```

![](STAProject-4--1--2--1--1-upload_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

############################################ 

## Observations

### Academic Status Distribution by Gender

![](STAProject-4--1--2--1--1-upload_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

![](STAProject-4--1--2--1--1-upload_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   17.00   19.00   20.00   23.27   25.00   70.00

### Descriptive Statistics of Age at Enrollment

- **Minimum (Min.)**: The youngest age at enrollment is 17 years.
- **First Quartile (1st Qu.)**: 25% of the students enrolled at the age
  of 19 or younger.
- **Median**: The middle value in the age data is 20 years, meaning half
  of the students enrolled at age 20 or younger.
- **Mean**: The average age of enrollment is approximately 23.27 years.
- **Third Quartile (3rd Qu.)**: 75% of the students enrolled at the age
  of 25 or younger.
- **Maximum (Max.)**: The oldest age at enrollment is 70 years.

## Academic Status Distribution by Special Needs

    ## Warning: No shared levels found between `names(values)` of the manual scale and the
    ## data's fill values.
    ## No shared levels found between `names(values)` of the manual scale and the
    ## data's fill values.

![](STAProject-4--1--2--1--1-upload_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

### Academic Status by Distribution by Special Needs Analysis

- **Students without educational special needs:**
  - There is a substantial group of students without educational special
    needs.
  - Among these students, a majority have graduated, with a considerably
    lower number of enrollments and even fewer dropouts.
  - This distribution indicates that students without special
    educational needs tend to have a high graduation rate.
- **Students with educational special needs:**
  - Compared to their counterparts, there are fewer students with
    educational special needs.
  - In this group, the numbers of graduates and dropouts are roughly
    comparable, with the number of enrolled students being slightly
    lower.
  - The near-equal count of graduates and dropouts suggests that
    students with special needs may face challenges that affect their
    completion rates.
  - These observations may point to a need for enhanced support systems
    to improve graduation rates among students with special needs.

## Academic Status Distribution by Scholarship Holder

    ## Warning: No shared levels found between `names(values)` of the manual scale and the
    ## data's fill values.
    ## No shared levels found between `names(values)` of the manual scale and the
    ## data's fill values.

![](STAProject-4--1--2--1--1-upload_files/figure-gfm/unnamed-chunk-12-1.png)<!-- -->

    ## # A tibble: 2 × 5
    ##   Scholarship.holder   `1`   `2`   `3` Total
    ##   <fct>              <int> <int> <int> <dbl>
    ## 1 no                  1287  1374   664  3325
    ## 2 yes                  134   835   130  1099

## Scholarship Holder Analysis

### Non-Scholarship Holders (No):

- Total number of students without scholarships: 3325
- Dropouts: 1287 (approximately 38.7% of non-scholarship holders)
- Graduates: 1374 (about 41.3% of this group)
- Currently Enrolled: 664 (roughly 20% of non-scholarship holders)

### Scholarship Holders (Yes):

- Total number of scholarship holders: 1099
- Dropouts: 134 (approximately 12.2% of scholarship holders)
- Graduates: 835 (constituting roughly 76% of the scholarship holders)
- Currently Enrolled: 130 (around 11.8% of students with scholarships)

### Comparative Insights:

- The dropout rate for scholarship holders is significantly lower than
  for non-scholarship holders, indicating that financial support is
  likely to positively impact students’ persistence in their education.
- The graduation rate for scholarship holders is considerably higher
  than for non-scholarship holders, suggesting that scholarships may
  alleviate financial burdens that can distract from or hinder academic
  success.
- A smaller proportion of scholarship holders are enrolled compared to
  non-scholarship holders, which may suggest that scholarship recipients
  either graduate more promptly or receive scholarships at later stages
  in their academic careers.

Overall, the data suggests that scholarships have a strong correlation
with positive academic outcomes, reducing dropout rates and increasing
graduation rates among recipients. This insight could serve as a strong
argument for educational institutions and policymakers to bolster
scholarship funding as an effective tool to enhance student success.

``` r
# Load necessary library
library(ggplot2)

# Plotting tuition fees status against academic target status
ggplot(data_test, aes(x = `Tuition.fees.up.to.date`, fill = Target)) +
  geom_bar(position = "dodge") +
  scale_fill_manual(values = c("Dropout" = "#fcbad3", "Enrolled" = "lightblue", "Graduate" = "#77dd77")) +
  scale_x_discrete(labels = c('No', 'Yes')) +
  labs(x = 'Tuition Fees Up to Date', y = 'Number of Students') +
  theme_minimal()
```

![](STAProject-4--1--2--1--1-upload_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

``` r
# tuition_fees_summary
library(dplyr)
library(tidyr)

# Tibble with a total column for the Tuition Fees Status and Academic Success
tuition_fees_summary <- data_test %>%
  count(Tuition.fees.up.to.date, Target) %>%
  pivot_wider(names_from = Target, values_from = n, values_fill = list(n = 0)) %>%
  rowwise() %>%
  mutate(Total = sum(c_across(where(is.numeric)))) %>%
  ungroup()
```

### Academic Status Distribution by Marital Status

    ## Warning: No shared levels found between `names(values)` of the manual scale and the
    ## data's fill values.
    ## No shared levels found between `names(values)` of the manual scale and the
    ## data's fill values.

![](STAProject-4--1--2--1--1-upload_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->

    ## # A tibble: 6 × 5
    ##   Marital.status      `1`   `2`   `3` Total
    ##   <fct>             <int> <int> <int> <int>
    ## 1 Single             1184  2015   720  3919
    ## 2 Married             179   148    52   379
    ## 3 Widower               1     1     2     4
    ## 4 Divorced             42    33    16    91
    ## 5 Facto union          11    11     3    25
    ## 6 Legally separated     4     1     1     6

### Academic Status by Marital Status Analysis

- **Single**: The largest group with 3,919 students, with 1,184
  dropouts, 2,015 graduates, and 720 enrolled. Single students represent
  the majority in all categories, indicating a high level of academic
  engagement and success among them.

- **Married**: Comprising 379 students, with 179 dropouts, 148
  graduates, and 52 enrolled. Although smaller in number, married
  students have a relatively balanced distribution across the academic
  statuses, suggesting that marriage might have a neutral impact on
  academic success.

- **Widower**: A very small group of 4 individuals, with 1 dropout, 1
  graduate, and 2 enrolled. Given the small sample size, it’s difficult
  to draw definitive conclusions, but the data suggests that widowhood
  does not significantly deter academic participation.

- **Divorced**: Consists of 91 students, with 42 dropouts, 33 graduates,
  and 16 enrolled. The relatively high number of dropouts might indicate
  that divorce has a negative impact on academic success.

- **Facto union**: With 25 students, having 11 dropouts, 11 graduates,
  and 3 enrolled. This group shows an equal number of dropouts and
  graduates, indicating that students in a de facto union have a
  balanced outcome in their academic endeavors.

- **Legally separated**: The smallest group, with 6 students, including
  4 dropouts, 1 graduate, and 1 enrolled. Despite the small numbers, the
  high proportion of dropouts could suggest that legal separation has a
  challenging impact on academic success.

#### Implications

- The data shows that single students are the largest demographic and
  have the highest graduation rate, which might reflect the demographic
  makeup of the student body or perhaps the different life stages and
  responsibilities affecting academic engagement and success.
- Married students also have a strong graduation rate, which might
  indicate stability or support systems that positively impact their
  academic success.
- The smaller groups (Divorced, Facto union, Legally separated, and
  Widower) have varied outcomes, and their small sample sizes make it
  difficult to draw broad conclusions without further contextual
  information.
- Institutions might consider targeted support or counseling services
  for students undergoing personal transitions (like divorce or legal
  separation) to help them navigate their academic journey effectively.

This analysis highlights the importance of understanding the diverse
life situations of students and how these situations might impact their
academic performance and outcomes.

![](STAProject-4--1--2--1--1-upload_files/figure-gfm/unnamed-chunk-18-1.png)<!-- -->

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   17.00   19.00   20.00   23.27   25.00   70.00

### Descriptive Statistics of Age at Enrollment

- **Minimum (Min.)**: The youngest age at enrollment is 17 years.
- **First Quartile (1st Qu.)**: 25% of the students enrolled at the age
  of 19 or younger.
- **Median**: The middle value in the age data is 20 years, meaning half
  of the students enrolled at age 20 or younger.
- **Mean**: The average age of enrollment is approximately 23.27 years.
- **Third Quartile (3rd Qu.)**: 75% of the students enrolled at the age
  of 25 or younger.
- **Maximum (Max.)**: The oldest age at enrollment is 70 years.

## Academic Status Distribution by Special Needs

``` r
library(ggplot2)

data_test$`Educational.special.needs` <- factor(data_test$`Educational.special.needs`)
data_test$Target <- factor(data_test$Target)

# Create the count plot
ggplot(data_test, aes(x = `Educational.special.needs`, fill = Target)) +
  geom_bar(position = "dodge") +
  scale_x_discrete(labels = c('No', 'Yes')) +
  labs(x = "Educational Special Needs", y = "Number of Students") +
  scale_fill_manual(values = c("Dropout" = "#fcbad3", "Enrolled" = "lightblue", "Graduate" = "#77dd77")) +
  theme_minimal()
```

![](STAProject-4--1--2--1--1-upload_files/figure-gfm/unnamed-chunk-19-1.png)<!-- -->

### Academic Status by Distribution by Special Needs Analysis

- **Students without educational special needs:**
  - There is a substantial group of students without educational special
    needs.
  - Among these students, a majority have graduated, with a considerably
    lower number of enrollments and even fewer dropouts.
  - This distribution indicates that students without special
    educational needs tend to have a high graduation rate.
- **Students with educational special needs:**
  - Compared to their counterparts, there are fewer students with
    educational special needs.
  - In this group, the numbers of graduates and dropouts are roughly
    comparable, with the number of enrolled students being slightly
    lower.
  - The near-equal count of graduates and dropouts suggests that
    students with special needs may face challenges that affect their
    completion rates.
  - These observations may point to a need for enhanced support systems
    to improve graduation rates among students with special needs.

## Academic Status Distribution by Scholarship Holder

![](STAProject-4--1--2--1--1-upload_files/figure-gfm/unnamed-chunk-20-1.png)<!-- -->

    ## # A tibble: 2 × 5
    ##   Scholarship.holder   `1`   `2`   `3` Total
    ##   <fct>              <int> <int> <int> <dbl>
    ## 1 no                  1287  1374   664  3325
    ## 2 yes                  134   835   130  1099

## Scholarship Holder Analysis

### Non-Scholarship Holders (No):

- Total number of students without scholarships: 3325
- Dropouts: 1287 (approximately 38.7% of non-scholarship holders)
- Graduates: 1374 (about 41.3% of this group)
- Currently Enrolled: 664 (roughly 20% of non-scholarship holders)

### Scholarship Holders (Yes):

- Total number of scholarship holders: 1099
- Dropouts: 134 (approximately 12.2% of scholarship holders)
- Graduates: 835 (constituting roughly 76% of the scholarship holders)
- Currently Enrolled: 130 (around 11.8% of students with scholarships)

### Comparative Insights:

- The dropout rate for scholarship holders is significantly lower than
  for non-scholarship holders, indicating that financial support is
  likely to positively impact students’ persistence in their education.
- The graduation rate for scholarship holders is considerably higher
  than for non-scholarship holders, suggesting that scholarships may
  alleviate financial burdens that can distract from or hinder academic
  success.
- A smaller proportion of scholarship holders are enrolled compared to
  non-scholarship holders, which may suggest that scholarship recipients
  either graduate more promptly or receive scholarships at later stages
  in their academic careers.

Overall, the data suggests that scholarships have a strong correlation
with positive academic outcomes, reducing dropout rates and increasing
graduation rates among recipients. This insight could serve as a strong
argument for educational institutions and policymakers to bolster
scholarship funding as an effective tool to enhance student success.

## Implementation of Machine Learning

- **Model Building Preparation:**
  - A new data frame `feature_selection` is created by selecting columns
    from `categorical_attributes`, excluding specific columns (e.g.,
    Daytime.evening.attendance, Nationality, etc.).
    - This step prepares the data by choosing relevant features for the
      modeling process.

``` r
#Model Building
feature_selection <- categorical_attributes %>%
  select(-Daytime.evening.attendance, -Nationality, -Educational.special.needs, -International, -Displaced, -Father.s.occupation) 
```

    Splitting Data:
        The script splits the data into two parts:
            X_train: This part contains most of the data (80%) and will be used for training the model.
            X_test: This part contains the rest of the data (20%) and will be used for testing the trained model.
    Setting Up Predictors and Target:
        y: This variable holds the target variable values (Target) from the data.
        x: This variable holds all other variables except the target (Target).
    Converting Target Variables:
        The target variable y is converted to numeric format for further processing.
        Similarly, the target variables for the test set are also converted to numeric format.

``` r
#Target and Predictor Variables:
library(caret)
```

    ## Loading required package: lattice

    ## 
    ## Attaching package: 'lattice'

    ## The following object is masked from 'package:gnm':
    ## 
    ##     barley

``` r
y <- feature_selection$Target
x <- feature_selection %>%
  select(-Target)
index <- createDataPartition(y, p=0.8, list = FALSE)
X_train <- x[index,]
X_test <- x [-index,]
Y_train <- y[index]
Y_test <- y[-index]
Y_train_numeric <- as.data.frame(lapply(Y_train, as.numeric))
Y_test_numeric <- as.data.frame(lapply(Y_test, as.numeric))

library(pROC)
```

    ## Type 'citation("pROC")' for a citation.

    ## 
    ## Attaching package: 'pROC'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     cov, smooth, var

``` r
library(e1071)
```

- **Data Cleaning:** - Removes any rows with missing values from both
  the training (`X_train`, `Y_train`) and testing (`X_test`, `Y_test`)
  datasets. - Converts the remaining data to a numeric format for model
  compatibility.

- **Cross-Validation Setup:**

  - Sets up cross-validation using the `trainControl` function with the
    following parameters:
    - `method = "cv"`: Specifies cross-validation.
    - `number = 10`: Indicates 10-fold cross-validation, splitting the
      data into 10 equal parts for training and validation.
    - `classProbs = TRUE`: Enables probabilities for classification.
    - `sampling = "smote"`: Specifies Synthetic Minority Over-sampling
      Technique (SMOTE) for addressing class imbalance (if present).

- **Random Forest Model Training:**

  - Trains a Random Forest model (`rf_model_cv`) using the `train`
    function with the following setup:
    - `x = X_train_numeric`: Predictor variables from the cleaned and
      numeric training set.
    - `y = Y_train`: Target variable from the cleaned training set.
    - `method = "rf"`: Specifies the Random Forest algorithm.
    - `trControl = train_control`: Utilizes the previously defined
      cross-validation settings.
    - `ntree = 1000`: Specifies the number of trees in the Random
      Forest.
    - `tuneGrid = expand.grid(mtry = 5)`: Specifies tuning parameters,
      here the number of variables randomly sampled as candidates at
      each split (mtry).
    - `importance = TRUE`: Requests variable importance measures.

- **Model Evaluation:**

  - Prints the trained Random Forest model (`rf_model_cv`) to inspect
    its details.
  - Prints performance metrics such as accuracy, Kappa, and ROC
    statistics (`rf_model_cv$results`).
  - Calculates and prints variable importance using
    `varImp(rf_model_cv)`.

- **Model Prediction:**

  - Uses the trained model to make predictions on the test set
    (`X_test_numeric`) with
    `predict(final_rf_model, newdata = X_test_numeric)`.
  - Extracts predicted classes from the probabilities (`rf_predictions`)
    using the maximum probability for each observation.
  - Prints a confusion matrix to evaluate the model’s performance on the
    test set.

- **Area Under the Curve (AUC) Calculation:**

  - Calculates the AUC using multiclass ROC
    (`roc_obj <- multiclass.roc(Y_test, rf_predictions)`).
  - Prints the AUC to assess the model’s performance in distinguishing
    between classes.

``` r
#Random Forest
library(randomForest)
```

    ## randomForest 4.7-1.1

    ## Type rfNews() to see new features/changes/bug fixes.

    ## 
    ## Attaching package: 'randomForest'

    ## The following object is masked from 'package:dplyr':
    ## 
    ##     combine

    ## The following object is masked from 'package:ggplot2':
    ## 
    ##     margin

``` r
library(caret)
complete_cases <- complete.cases(X_train, Y_train)
X_train <- X_train[complete_cases, ]
X_train_numeric <- as.data.frame(lapply(X_train, as.numeric))
Y_train <- Y_train[complete_cases]
Y_train_numeric <- as.data.frame(lapply(Y_train, as.numeric))
complete_cases_test <- complete.cases(X_test, Y_test)
X_test <- X_test[complete_cases_test, ]
Y_test <- Y_test[complete_cases_test]
X_test_numeric <- as.data.frame(lapply(X_test, as.numeric))
# Y_test <- Y_test[complete_cases_test]
View(X_train_numeric)

#Cross val
train_control <- trainControl(method = "cv", number = 10, classProbs = TRUE, sampling = "smote")

#Model
rf_model_cv <- train(
  x = X_train_numeric,
  y = Y_train,
  method = "rf",
  trControl = train_control,
  ntree = 1000,
  tuneGrid = expand.grid(mtry = 5),  
  importance = TRUE
)
```

    ## Loading required package: recipes

    ## 
    ## Attaching package: 'recipes'

    ## The following object is masked from 'package:stats':
    ## 
    ##     step

``` r
#Model Result
print(rf_model_cv)
```

    ## Random Forest 
    ## 
    ## 3541 samples
    ##   17 predictor
    ##    3 classes: 'Dropout', 'Graduate', 'Enrolled' 
    ## 
    ## No pre-processing
    ## Resampling: Cross-Validated (10 fold) 
    ## Summary of sample sizes: 3188, 3189, 3187, 3186, 3186, 3188, ... 
    ## Addtional sampling using SMOTE
    ## 
    ## Resampling results:
    ## 
    ##   Accuracy  Kappa    
    ##   0.744415  0.5793117
    ## 
    ## Tuning parameter 'mtry' was held constant at a value of 5

``` r
#performance metrics
print(rf_model_cv$results)
```

    ##   mtry Accuracy     Kappa AccuracySD    KappaSD
    ## 1    5 0.744415 0.5793117 0.01642149 0.02525077

``` r
#importance
varImp(rf_model_cv)
```

    ## rf variable importance
    ## 
    ##   variables are sorted by maximum importance across the classes
    ##                                        Dropout Graduate Enrolled
    ## Curricular.units.1st.sem..approved.     36.941  100.000    80.02
    ## Tuition.fees.up.to.date                 87.054   62.183    86.75
    ## Curricular.units.2nd.sem..evaluations.  50.029   40.506    82.50
    ## Curricular.units.2nd.sem..grade.        51.894   77.690    76.11
    ## Course                                   8.698   45.975    71.45
    ## Mother.s.occupation                     28.103   15.093    60.11
    ## Age.at.enrollment                       48.044   26.432    58.57
    ## Scholarship.holder                      42.080   45.692    55.36
    ## Father.s.qualification                  25.215    8.373    54.85
    ## Curricular.units.1st.sem..grade.        20.460   39.408    47.45
    ## Mother.s.qualification                  29.399    7.502    45.61
    ## Application.mode                        25.668   21.228    42.08
    ## Application.order                       24.596    5.493    41.69
    ## Gender                                  23.968   25.905    39.54
    ## Debtor                                  18.458   30.410    34.08
    ## Previous.qualification                  17.315    9.367    22.91
    ## Marital.status                           0.000   15.580    21.69

``` r
#predictions
final_rf_model <- rf_model_cv$finalModel
predictions <- predict(final_rf_model, newdata = X_test_numeric)
print(predictions)
```

    ##        1        2        3        4        5        6        7        8 
    ##  Dropout  Dropout Graduate Graduate Graduate  Dropout  Dropout  Dropout 
    ##        9       10       11       12       13       14       15       16 
    ##  Dropout Enrolled Enrolled Graduate Graduate Graduate  Dropout Graduate 
    ##       17       18       19       20       21       22       23       24 
    ## Enrolled Graduate Enrolled Graduate Graduate  Dropout  Dropout Enrolled 
    ##       25       26       27       28       29       30       31       32 
    ##  Dropout Graduate  Dropout  Dropout Graduate Graduate Graduate Graduate 
    ##       33       34       35       36       37       38       39       40 
    ## Graduate Graduate Graduate Graduate  Dropout Graduate  Dropout Enrolled 
    ##       41       42       43       44       45       46       47       48 
    ## Graduate  Dropout Graduate Enrolled Graduate Graduate Graduate Graduate 
    ##       49       50       51       52       53       54       55       56 
    ## Graduate Graduate  Dropout Graduate Graduate Graduate Graduate Graduate 
    ##       57       58       59       60       61       62       63       64 
    ## Graduate  Dropout  Dropout Graduate Graduate Graduate Graduate Enrolled 
    ##       65       66       67       68       69       70       71       72 
    ## Graduate Graduate Enrolled Graduate  Dropout Enrolled Enrolled Graduate 
    ##       73       74       75       76       77       78       79       80 
    ## Graduate Enrolled  Dropout  Dropout Graduate Graduate Graduate  Dropout 
    ##       81       82       83       84       85       86       87       88 
    ##  Dropout Graduate Graduate Graduate Graduate  Dropout  Dropout Graduate 
    ##       89       90       91       92       93       94       95       96 
    ## Graduate Graduate Enrolled Enrolled  Dropout Enrolled  Dropout Graduate 
    ##       97       98       99      100      101      102      103      104 
    ##  Dropout  Dropout  Dropout  Dropout Enrolled Enrolled Enrolled  Dropout 
    ##      105      106      107      108      109      110      111      112 
    ## Graduate  Dropout  Dropout Graduate Graduate Enrolled  Dropout  Dropout 
    ##      113      114      115      116      117      118      119      120 
    ## Enrolled  Dropout  Dropout  Dropout Graduate Enrolled Graduate Graduate 
    ##      121      122      123      124      125      126      127      128 
    ## Graduate Graduate Graduate Enrolled Graduate  Dropout Enrolled Graduate 
    ##      129      130      131      132      133      134      135      136 
    ## Graduate  Dropout Graduate Graduate  Dropout Graduate  Dropout Enrolled 
    ##      137      138      139      140      141      142      143      144 
    ## Enrolled Graduate Graduate Graduate Graduate Graduate Enrolled Graduate 
    ##      145      146      147      148      149      150      151      152 
    ##  Dropout Enrolled Enrolled  Dropout Graduate Graduate Enrolled Graduate 
    ##      153      154      155      156      157      158      159      160 
    ##  Dropout  Dropout  Dropout Graduate  Dropout Enrolled Graduate Graduate 
    ##      161      162      163      164      165      166      167      168 
    ## Graduate  Dropout Graduate  Dropout  Dropout Enrolled Enrolled Graduate 
    ##      169      170      171      172      173      174      175      176 
    ##  Dropout Graduate Enrolled  Dropout  Dropout Graduate  Dropout Graduate 
    ##      177      178      179      180      181      182      183      184 
    ##  Dropout Graduate Graduate Enrolled Graduate Graduate  Dropout Graduate 
    ##      185      186      187      188      189      190      191      192 
    ## Graduate Graduate  Dropout Enrolled Enrolled Graduate  Dropout Graduate 
    ##      193      194      195      196      197      198      199      200 
    ## Enrolled  Dropout Graduate Graduate Enrolled Enrolled Enrolled Graduate 
    ##      201      202      203      204      205      206      207      208 
    ## Graduate  Dropout Graduate Graduate Graduate Graduate  Dropout Graduate 
    ##      209      210      211      212      213      214      215      216 
    ## Graduate Graduate Graduate Graduate Graduate Graduate Enrolled Graduate 
    ##      217      218      219      220      221      222      223      224 
    ## Graduate  Dropout  Dropout  Dropout Graduate Graduate Graduate Graduate 
    ##      225      226      227      228      229      230      231      232 
    ## Graduate  Dropout Graduate Graduate Graduate Graduate Graduate Enrolled 
    ##      233      234      235      236      237      238      239      240 
    ## Graduate Graduate Enrolled Enrolled Enrolled Enrolled Graduate Graduate 
    ##      241      242      243      244      245      246      247      248 
    ##  Dropout Graduate Graduate Graduate Graduate Enrolled Graduate Graduate 
    ##      249      250      251      252      253      254      255      256 
    ## Enrolled Enrolled  Dropout Graduate  Dropout  Dropout Enrolled Graduate 
    ##      257      258      259      260      261      262      263      264 
    ##  Dropout Graduate Graduate Graduate Graduate Graduate Enrolled Enrolled 
    ##      265      266      267      268      269      270      271      272 
    ## Graduate Enrolled Enrolled Graduate Graduate Graduate Graduate Enrolled 
    ##      273      274      275      276      277      278      279      280 
    ##  Dropout Enrolled  Dropout  Dropout Graduate Graduate  Dropout Graduate 
    ##      281      282      283      284      285      286      287      288 
    ## Graduate  Dropout Graduate Graduate Graduate Graduate Enrolled Enrolled 
    ##      289      290      291      292      293      294      295      296 
    ## Graduate  Dropout  Dropout  Dropout Enrolled Enrolled Graduate Graduate 
    ##      297      298      299      300      301      302      303      304 
    ## Enrolled  Dropout Graduate Graduate Graduate Graduate Graduate Enrolled 
    ##      305      306      307      308      309      310      311      312 
    ##  Dropout  Dropout Enrolled  Dropout Graduate Graduate Graduate Graduate 
    ##      313      314      315      316      317      318      319      320 
    ##  Dropout Graduate  Dropout Graduate Graduate  Dropout Enrolled Graduate 
    ##      321      322      323      324      325      326      327      328 
    ## Graduate Graduate Graduate Graduate  Dropout  Dropout Graduate Graduate 
    ##      329      330      331      332      333      334      335      336 
    ## Graduate Graduate Graduate  Dropout Graduate Graduate Graduate Graduate 
    ##      337      338      339      340      341      342      343      344 
    ## Enrolled  Dropout Graduate Enrolled  Dropout  Dropout Graduate Graduate 
    ##      345      346      347      348      349      350      351      352 
    ## Graduate Graduate Graduate  Dropout  Dropout Enrolled Graduate Graduate 
    ##      353      354      355      356      357      358      359      360 
    ##  Dropout  Dropout  Dropout Graduate  Dropout Graduate Enrolled  Dropout 
    ##      361      362      363      364      365      366      367      368 
    ## Graduate  Dropout Graduate Graduate Graduate Enrolled Graduate Enrolled 
    ##      369      370      371      372      373      374      375      376 
    ##  Dropout  Dropout Graduate Graduate  Dropout Graduate Graduate  Dropout 
    ##      377      378      379      380      381      382      383      384 
    ## Enrolled Enrolled  Dropout Graduate Graduate Enrolled Graduate Graduate 
    ##      385      386      387      388      389      390      391      392 
    ## Graduate Graduate Graduate Enrolled Graduate Enrolled Graduate Enrolled 
    ##      393      394      395      396      397      398      399      400 
    ## Graduate  Dropout Graduate  Dropout Graduate  Dropout Graduate  Dropout 
    ##      401      402      403      404      405      406      407      408 
    ##  Dropout Graduate  Dropout  Dropout Graduate Graduate Graduate Enrolled 
    ##      409      410      411      412      413      414      415      416 
    ## Graduate Graduate Graduate Graduate Enrolled Graduate Enrolled Graduate 
    ##      417      418      419      420      421      422      423      424 
    ## Enrolled Enrolled Graduate Graduate Graduate  Dropout Graduate Graduate 
    ##      425      426      427      428      429      430      431      432 
    ##  Dropout  Dropout Graduate Graduate Graduate Graduate Enrolled Graduate 
    ##      433      434      435      436      437      438      439      440 
    ## Graduate Graduate Graduate Graduate Graduate Graduate  Dropout Graduate 
    ##      441      442      443      444      445      446      447      448 
    ## Enrolled Graduate  Dropout Graduate  Dropout Graduate Enrolled  Dropout 
    ##      449      450      451      452      453      454      455      456 
    ##  Dropout Graduate Graduate Graduate Graduate Enrolled  Dropout  Dropout 
    ##      457      458      459      460      461      462      463      464 
    ##  Dropout Enrolled  Dropout Graduate  Dropout Graduate  Dropout Enrolled 
    ##      465      466      467      468      469      470      471      472 
    ## Graduate Enrolled Enrolled Graduate  Dropout  Dropout  Dropout  Dropout 
    ##      473      474      475      476      477      478      479      480 
    ## Graduate Graduate Graduate  Dropout Enrolled  Dropout Enrolled Graduate 
    ##      481      482      483      484      485      486      487      488 
    ## Graduate  Dropout  Dropout  Dropout Graduate  Dropout  Dropout  Dropout 
    ##      489      490      491      492      493      494      495      496 
    ## Enrolled  Dropout  Dropout Graduate  Dropout  Dropout Graduate  Dropout 
    ##      497      498      499      500      501      502      503      504 
    ## Graduate Graduate Graduate Graduate Graduate  Dropout  Dropout Graduate 
    ##      505      506      507      508      509      510      511      512 
    ## Graduate Graduate Graduate Graduate Graduate Graduate Enrolled Graduate 
    ##      513      514      515      516      517      518      519      520 
    ## Graduate Graduate  Dropout Graduate  Dropout Enrolled Graduate Enrolled 
    ##      521      522      523      524      525      526      527      528 
    ## Graduate Graduate Enrolled  Dropout Graduate Graduate Graduate Graduate 
    ##      529      530      531      532      533      534      535      536 
    ## Graduate  Dropout Enrolled  Dropout Graduate  Dropout Graduate  Dropout 
    ##      537      538      539      540      541      542      543      544 
    ## Graduate  Dropout  Dropout Enrolled Graduate Graduate Graduate Graduate 
    ##      545      546      547      548      549      550      551      552 
    ##  Dropout Graduate  Dropout Graduate Graduate Graduate Graduate  Dropout 
    ##      553      554      555      556      557      558      559      560 
    ## Enrolled Graduate Graduate Enrolled Graduate Graduate  Dropout  Dropout 
    ##      561      562      563      564      565      566      567      568 
    ## Graduate Graduate Graduate Graduate Graduate Graduate Enrolled  Dropout 
    ##      569      570      571      572      573      574      575      576 
    ## Graduate  Dropout Enrolled Graduate Graduate  Dropout Graduate  Dropout 
    ##      577      578      579      580      581      582      583      584 
    ##  Dropout  Dropout Graduate Graduate Graduate Enrolled  Dropout Graduate 
    ##      585      586      587      588      589      590      591      592 
    ##  Dropout Graduate  Dropout Enrolled Graduate Graduate Graduate Graduate 
    ##      593      594      595      596      597      598      599      600 
    ## Graduate Graduate Graduate Graduate Enrolled Graduate Graduate Enrolled 
    ##      601      602      603      604      605      606      607      608 
    ## Graduate Enrolled Enrolled  Dropout Graduate Graduate Graduate Graduate 
    ##      609      610      611      612      613      614      615      616 
    ##  Dropout Graduate Graduate  Dropout Graduate Graduate Graduate Graduate 
    ##      617      618      619      620      621      622      623      624 
    ## Graduate Enrolled Graduate  Dropout  Dropout Graduate  Dropout  Dropout 
    ##      625      626      627      628      629      630      631      632 
    ## Enrolled Graduate  Dropout Graduate Graduate Graduate  Dropout Enrolled 
    ##      633      634      635      636      637      638      639      640 
    ## Graduate Graduate Graduate  Dropout Enrolled Graduate Graduate  Dropout 
    ##      641      642      643      644      645      646      647      648 
    ## Graduate  Dropout  Dropout Graduate Graduate  Dropout Enrolled Graduate 
    ##      649      650      651      652      653      654      655      656 
    ## Enrolled Graduate  Dropout  Dropout  Dropout Enrolled  Dropout Graduate 
    ##      657      658      659      660      661      662      663      664 
    ##  Dropout  Dropout Graduate Graduate  Dropout Graduate Graduate Graduate 
    ##      665      666      667      668      669      670      671      672 
    ## Graduate Graduate Graduate Enrolled Enrolled  Dropout  Dropout Graduate 
    ##      673      674      675      676      677      678      679      680 
    ##  Dropout Graduate Graduate Graduate Graduate Graduate Enrolled  Dropout 
    ##      681      682      683      684      685      686      687      688 
    ## Graduate Graduate Enrolled Enrolled Graduate Graduate  Dropout Graduate 
    ##      689      690      691      692      693      694      695      696 
    ## Graduate  Dropout Enrolled  Dropout  Dropout Enrolled Enrolled  Dropout 
    ##      697      698      699      700      701      702      703      704 
    ## Enrolled Graduate  Dropout  Dropout  Dropout Enrolled  Dropout  Dropout 
    ##      705      706      707      708      709      710      711      712 
    ##  Dropout Graduate Graduate Graduate Graduate  Dropout Graduate  Dropout 
    ##      713      714      715      716      717      718      719      720 
    ## Enrolled Graduate Graduate Enrolled Graduate Graduate Graduate Graduate 
    ##      721      722      723      724      725      726      727      728 
    ## Graduate Graduate Graduate Enrolled  Dropout Enrolled  Dropout Graduate 
    ##      729      730      731      732      733      734      735      736 
    ## Graduate  Dropout Enrolled  Dropout Graduate  Dropout Enrolled  Dropout 
    ##      737      738      739      740      741      742      743      744 
    ## Graduate Enrolled Graduate Graduate Graduate Graduate Enrolled Graduate 
    ##      745      746      747      748      749      750      751      752 
    ## Graduate Graduate  Dropout  Dropout Graduate Graduate Graduate  Dropout 
    ##      753      754      755      756      757      758      759      760 
    ##  Dropout Enrolled Enrolled Enrolled  Dropout  Dropout Enrolled Graduate 
    ##      761      762      763      764      765      766      767      768 
    ##  Dropout Graduate  Dropout  Dropout Graduate Graduate Graduate Graduate 
    ##      769      770      771      772      773      774      775      776 
    ##  Dropout  Dropout Enrolled Enrolled Graduate Graduate Graduate Graduate 
    ##      777      778      779      780      781      782      783      784 
    ##  Dropout Enrolled Graduate Graduate Graduate Graduate Graduate Enrolled 
    ##      785      786      787      788      789      790      791      792 
    ## Graduate  Dropout Graduate Graduate Graduate Graduate  Dropout  Dropout 
    ##      793      794      795      796      797      798      799      800 
    ## Graduate  Dropout  Dropout Graduate Graduate  Dropout Graduate Graduate 
    ##      801      802      803      804      805      806      807      808 
    ## Graduate  Dropout  Dropout Graduate Graduate  Dropout Graduate Graduate 
    ##      809      810      811      812      813      814      815      816 
    ##  Dropout Graduate Enrolled  Dropout Graduate Enrolled Enrolled Graduate 
    ##      817      818      819      820      821      822      823      824 
    ## Graduate Graduate  Dropout Graduate Graduate Graduate Enrolled Graduate 
    ##      825      826      827      828      829      830      831      832 
    ## Enrolled Graduate Enrolled Graduate Enrolled Graduate Graduate Graduate 
    ##      833      834      835      836      837      838      839      840 
    ## Enrolled  Dropout Enrolled Graduate Graduate Graduate Graduate Graduate 
    ##      841      842      843      844      845      846      847      848 
    ## Graduate Graduate Graduate Graduate Enrolled  Dropout Graduate Graduate 
    ##      849      850      851      852      853      854      855      856 
    ##  Dropout Graduate  Dropout  Dropout  Dropout Graduate  Dropout Graduate 
    ##      857      858      859      860      861      862      863      864 
    ## Graduate  Dropout Graduate Enrolled  Dropout Graduate  Dropout Enrolled 
    ##      865      866      867      868      869      870      871      872 
    ##  Dropout Graduate  Dropout Graduate Graduate  Dropout Graduate Graduate 
    ##      873      874      875      876      877      878      879      880 
    ## Graduate Graduate  Dropout Enrolled Enrolled  Dropout Graduate  Dropout 
    ##      881      882      883 
    ## Graduate  Dropout Graduate 
    ## Levels: Dropout Graduate Enrolled

``` r
###########



threshold <- 0.50

# Make predictions on the filtered test set
rf_predictions <- predict(rf_model_cv, newdata = X_test_numeric, type = "prob")

rf_predictions <- rf_predictions[complete_cases_test, ]

#probabilities to class labels 
predicted_classes <- apply(rf_predictions, 1, function(row) {
  classes <- which.max(row)
})

Y_test <- as.factor(Y_test)
predicted_classes <- as.factor(predicted_classes)

# AUC
roc_obj <- multiclass.roc(Y_test, rf_predictions)


print(paste("AUC:", roc_obj$auc))
```

    ## [1] "AUC: 0.847376355952337"

``` r
#Confusion Matrix
conf_matrix <- table(Actual = Y_test, Predicted = predicted_classes)
print("Confusion Matrix:")
```

    ## [1] "Confusion Matrix:"

``` r
print(conf_matrix)
```

    ##           Predicted
    ## Actual       1   2   3
    ##   Dropout  209  36  39
    ##   Graduate  17 384  40
    ##   Enrolled  28  54  76

``` r
# Calculate AUC
roc_obj <- multiclass.roc(Y_test, rf_predictions)

# Print the AUC
print(paste("AUC:", roc_obj$auc))
```

    ## [1] "AUC: 0.847376355952337"

# Conclusion

This approach has the potential to offer practical value to those
interested in the academic progress of students (Education
psychologists, Educators, Parents) by utilizing a straightforward and
objective tool, such as AI-based feature analysis, to stratify students
based on dropout risk. Additionally, this work provides insights to
educational psychologists, parents, and even the students themselves by
identifying the key contributors to enrollment status.

# References

DataCamp. (n.d.). ASSOCSTATS: Association statistics. RDocumentation.
<https://www.rdocumentation.org/packages/vcd/versions/1.4-12/topics/assocstats>

Realinho V, Machado J, Baptista L, Martins MV. Predicting Student
Dropout and Academic Success. Data. 2022; 7(11):146.
<https://doi.org/10.3390/data7110146>

TheDevastator. (2023, April). Higher Education Predictors of Student
Retention \[Data set\]. Kaggle. \[Online\]. Available:
<https://www.kaggle.com/datasets/thedevastator/higher-education-predictors-of-student-retention/data>

Zach. (2021, September 30). How to interpret Cramer’s V (with examples).
Statology. <https://www.statology.org/interpret-cramers-v/>

## Books

Navarro, D. (2019, January 1). Learning statistics with R. Learning
Statistics with R. <https://learningstatisticswithr.com/>

Witten, I. H., Frank, E., & Hall, M. A. (2011). Data Mining: Practical
Machine Learning Tools and Techniques (Third Edition). Morgan Kaufmann.
<https://doi.org/10.1016/B978-0-12-374856-0.00023-7>
