### Overview
All around us, there is some form of technology that exits; yet, even surrounding us, we can't help but wonder on those who aren't able to actually utilize these tools. Since the beginning of the COVID-19 outbreak, technology and Internet usage have rapidly evolved, but in doing so, have furthered a digital divide among populatons. Students and families were thrown into remote learning that relied heavily on quality Internet services. 

Even before the pandemic, there's been findings that suggest school-age children face tech-related obstacles that prevent them from completing schoolwork at home. In an analysis of 2015 U.S. Census Bureau data by Pew Research Center, there were indications approximately '15% of U.S. households with school-age children did not have a high-speed internet connection at home.' Dubbed the "homework gap", this implication was prevalent in low-income households who lacked the financial resources to access reliable computer or internet services. The one-in-four lower-income teens identified are now compelled to find locations with public Wi-Fi ([*source*](https://www.pewresearch.org/fact-tank/2018/10/26/nearly-one-in-five-teens-cant-always-finish-their-homework-because-of-the-digital-divide/)). Some opinions call for the government to provide basic technological support (e.g. laptop, tablet, hotspots) for all K-12 students ([*source*](https://www.pewresearch.org/internet/2021/09/01/the-internet-and-the-pandemic/#:~:text=The%20share%20who%20say%20it,and%20those%2065%20and%20older)). 

The SAT and ACT are standardized tests that measure college readiness and aptitude ([*source*](https://www.minotdailynews.com/news/local-news/2017/04/a-brief-history-of-the-sat-and-act/)). However, if students encounter technological obstaces in completing homework, it brings the idea that standardized testing may be impacted as well. Thus, we begin an evaluation on the hypothesis on whether technology is connected to the average mean of ACT and SAT scores, in 2019. 

### Problem Statement
This project seeks to evaluate if a relationship exists between student ACT/SAT scores and high-speed Internet access, in 2019, to develop recommendations for school administrations on distribution of resources. 

### Datasets
* [`act_2019.csv`](../data/act_2019.csv): 2019 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))

* [`sat_2019.csv`](../data/sat_2019.csv): 2019 SAT Scores by State ([source](https://blog.prepscholar.com/average-sat-scores-by-state-most-recent))

### Additional Data
* [`nces-2019-internet.xls`](../data/nces-2019-internet.xls): Percent of children ages 3 to 18 by type of computer in the household and percentage distributions of children agres 3 to 18 by home internet access, by poverty status and state: 2019 ([source](https://nces.ed.gov/programs/digest/d20/tables/dt20_702.60.asp))

** The data is based on sample surveys from the entire population of the United States rom the American Community Survey (ACS) administered by the U.S. Department of Commerce, Census Bureau in 2019

### Data Dictionary
|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|ACT|The states of the country| 
|comp_score|float|ACT|The average ACT composite score of a state| 
|participation|float|ACT|the percent of the state that took ACT (1.00 means required by state)| 
|state|object|SAT|The states of the country| 
|reading|int|SAT|The average reading score on the SAT of a state| 
|math|int|SAT|The average math score on the SAT of a state| 
|total_score|int|SAT|The combined reading and math scores of SAT of a state| 
|participation|float|SAT|the percent of the state that took SAT (1.00 means required by state)|

### Data & Modeling
Steps
* Calculations:
    - Created functions to calculate the mean and standard deviation of a list
    - Devised a data cleaning function to convert non-numerical data types into floats
* Cleaning Data:
    - Imported data from act_2019.csv, sat_2019.csv, nces-2019-internet.xls
    - Checked for null values, converted objects into floats, dropping null rows, and adjusting column names (act_2019 and sat_2019).
    - Created copies of Excel sheets to evaluate states of ACT and SAT states with 100% participation (nces-2019-internet).
* Processing & Observations
    - Began observations on states with the highest/lowest participation on the ACT and SAT; created scatter plots to evaluate the Composite Scores and Participation on the ACT, in 2019 and Total Score and Participation on the SAT, in 2019.
    - Using the scatter plot and EDA, focused directly on states with 100% participation (assumption = 100% means state-required) and evaluated the highest/lowest ACT and SAT scores from this grouping.
    - Identified the three states that scored the highest and lowest for the ACT (highest = Utah, Wisconsin, Nebraska; lowest = Louisiana, Mississippi, and Nevada) and the SAT (highest = Connecticut, Colorado, Illinois; lowest = Rhode Islan, Idaho, and Delaware)
    - Using the NCES data, examined the percentage of children ages 3 to 18 "with a desktop, laptop, tablet, or other portable wireless computer" and the percentage of children ages 3 to 18 that "have internet access through desktop or laptop, tablet, or some other type of computer." for the states listed above.
    
Modeling
- Scatter plot, 'Composite Score v. Participation Across All States on the ACT, in 2019'
<img src = "../project-1/graphs/comp_score_part_scatter_act.png" style="float: center; margin: 10px; height: 300px">

- Bar chart, 'Average ACT Composite Score of States with 100% ACT Participation, in 2019'
<img src = "../project-1/graphs/average_comp_score_states_act.png" style="float: center; margin: 10px; height: 300px">

- Scatter plot 'Total Score v. Participation Across All States on the SAT, in 2019' 
<img src = "../project-1/graphs/total_score_part_scatter_sat.png" style="float: center; margin: 10px; height: 300px">

- Bar chart, 'Average SAT Total Score of States with 100% SAT Participation, in 2019'
<img src = "../project-1/graphs/average_total_score_states_sat.png" style="float: center; margin: 10px; height: 300px">

### Findings
* 'Composite Score v. Participation Across All States on the ACT, 2019' and 'Total Score v. Participation Across All States on the SAT, in 2019' showed on a scatter plot what looked like a trend that the lower the participation rate, the higher the composite score; vice versa, the states that required the ACT and SAT had the lowest scores. However, if you run through the correlation of each column, we found that participation and comp_score (participation and total_score for SAT) had an unlikely correlation at -0.864154. The closer the number is to -1, the more unlikely the correlation. We will instead focus on states that required ACT or SAT participation (Participation = 1.0) to further our exploration of technological resources those states have. 

**NCES sample survey results, for the ACT, for highest-scoring states (Utah, Wisconsin, and Nebraska) and lowest-scoring states (Louisiana, Mississippi, Nevada), in 2019:**

Finding: Highest-scoring states had above 91% (children ages 3 to 18) of sample have a desktop or laptop. Within that group, above 90% had Internet access through their desktop or laptop. 
|State|Population (thous.)|% With Desktop or Laptop(D/L)|% With Internet Access on D/L|
|---|---|---|---|
|**Utah**|837|95.6|94.6| 
|**Wisconsin**|1,139|91.9|90.6|
|**Nebraska**|421|93.0|90.9|

Finding: Lowest-scoring states had between 81%-88% (children ages 3 to 18) with a desktop or laptop. Within that group above, between 79%-86% had access to Internet on their desktop or laptop
|State|Population (thous.)|% With Desktop or Laptop(D/L)|% With Internet Access on D/L|
|---|---|---|---|
|**Louisiana**|973|83.6|80.4| 
|**Mississippi**|634|81.4|79.2|
|**Nevada**|619|88.8|86.3|

**NCES sample survey results, for SAT, for highest-scoring states (Connecticut, Colorado, Illinois) and lowest-scoring states (Rhode Island, Idaho, Delaware), in 2019:**

Finding: Highest-scoring states had between 90%-94% (children ages 3 to 18) with a desktop or laptop. Within that group above, between 89%-93% had access to Internet on their desktop or laptop
|State|Population (thous.)|% With Desktop or Laptop(D/L)|% With Internet Access on D/L|
|---|---|---|---|
|**Connecticut**|653|92.7|91.9| 
|**Colorado**|1,122|93.3|92.6|
|**Illinois**|2,524|90.9|89.4|

Finding: Lowest-scoring states had between 90%-93% (children ages 3 to 18) with a desktop or laptop. Within that group above, between 89%-93% had access to Internet on their desktop or laptop. This is fairly similar findings to the highest-scoring states. 
|State|Population (thous.)|% With Desktop or Laptop(D/L)|% With Internet Access on D/L|
|---|---|---|---|
|**Rhode Island**|182|92.5|92.3| 
|**Idaho**|410|92.5|90.9|
|**Delaware**|182|91.2|89.8|


* Note: This examination does not solidify a correlation, but encourage an observation that would need to be explored further (in the recommendations in the next section)

### Conclusion & Recommendations
* The findings above do not solidify a conclusive correlation between technology obstacles and student performances on the ACT or SAT. However, it does provide a strong case for school administrators to investigate further within their own districts. Below are actions steps:
    * Identify areas within your curriculum that require technology
    * Create and administer a random survey within your district to identify the areas including: cost of Internet services, reliability of Internet services (e.g. speed, # of devices connected), type of devices used by students relating to schoolwork
    * Evaluation of statewide digital access funding and services
    
