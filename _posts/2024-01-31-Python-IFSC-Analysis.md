---
title: Python Sport Climbing Analysis
date: 2024-01-31 21:00:00 -0500
categories: [Python]
tags: [Pandas, Selenium, Seaborn]
---

# Python ~ IFSC Climbing World Cups 2023

## **Project Overview:**

This project aims to analyze the results of different events in the Sport Climbing World Cups 2023 across different categories to gain insights into performance trends, athlete rankings, and potential areas of improvement. 

## Objectives:

- Identify and analyze performance trends in sport climbing across different World Cup events.
- Explore patterns and correlations within the data to understand factors influencing climbing performance.
- Compare and contrast results across different categories such as bouldering, lead climbing, and speed climbing.
- Investigate potential predictors of success in sport climbing events.

## **Data Collection:**

The primary source of data for this analysis is the official website of the International Federation of Sport Climbing (IFSC). The IFSC website provides comprehensive and up-to-date information on Sport Climbing World Cup results, including details on athletes, categories, and event outcomes.

First, I grabbed all the events that went down in 2023. Then, I went ahead and gathered info on the athletes that competed. I ****used Python with the Selenium library to scrape the website. Selenium's like a magician for automating web browser stuff, perfect for snagging dynamic content from websites. The end result was four csv files, one for each category with the results and one with the athlete information. 

## **Data Cleaning Steps:**

Once the data was extracted, a series of cleaning steps were applied to ensure the dataset's quality and usability:

1. **Handling Missing Data:**
    - Dealt with missing height values for 424 athletes by replacing them with the mean height based on country and gender. Subsequently, 94 athletes with remaining missing height values had them replaced with the mean height by gender.
    - Left missing values in category CSV files (boulder, lead, speed) as they indicated that athletes did not progress to the next round.
    - Removed certain athletes from the dataset, including those who registered but didn't participate and those not present in the athlete CSV file containing personal information.
2. **Data Type Conversion:**
    - Ensured consistency in data types by converting variables to appropriate formats (e.g., dates, numerical values).
3. **Consistent Naming Conventions:**
    - Maintained uniform naming conventions for athletes, events, and categories.
    - Dropped columns that did not contribute to the analysis.
4. **Data Verification:**
    - Validated the accuracy of extracted data by cross-referencing it with official IFSC records.
    - For the Seoul World Cup, clarified that boulder finals were canceled due to weather conditions. However, the [IFSC website](https://www.ifsc-climbing.org/index.php/component/ifsc/?view=event&WetId=1292) states that semi-final results were used to determine the finalists.

## **Exploratory Data Analysis (EDA):**

The athletes csv file contains 750 records and 8 columns (Name, AthleteUrl, Gender, Height, Active, Participations, Age, Country')

The **height** variable represents the recorded height of athletes in centimeters. The dataset includes 750 entries with a mean height of 169.74 cm and a standard deviation of 7.57 cm. Heights range from a minimum of 149 cm to a maximum of 198 cm. The median height is 171 cm, with the 25th percentile at 163.20 cm and the 75th percentile at 175 cm.

The **participations** variable indicates the number of times an athlete has participated in sport climbing competitions. The mean number of participations is 36.21, with a wide range from a minimum of 1 to a maximum of 247. The median (50th percentile) is 22, and the interquartile range spans from 11 to 52 participations.

The **age** variable represents the age of athletes in years. The dataset includes ages ranging from a minimum of 16 years to a maximum of 39 years. The mean age is 22.51 years, with a standard deviation of 4.51 years. The median age is 22 years, and the interquartile range spans from 19 to 25 years. The total participating countries during the 2023 sport climbing competitions are 67.

![01_athlete_boxplot.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/01_athlete_boxplot.png)

In the 2023 sport climbing competitions, a total of 67 countries were represented, with Japan having the largest contingent of participating athletes. Following closely were France, the USA, and Korea.

![02_Athlete_Count_per_Country_-_2023_Competitions.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/02_Athlete_Count_per_Country.png)

The boulder CSV file comprises 1,232 records and 8 variables. This category was featured in 7 events throughout 2023, with a predominant number of male participants. The accompanying bar chart illustrates the distribution of athletes and reveals a decline in participation during the Hachioji, Seoul, and Salt Lake City competitions. Conversely, there is an upward trend in athlete numbers for the remaining competitions.

![03_Athlete_Count_in_Bouldering_by_Event_and_Gender.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/03_Athlete_Count_in_Bouldering_by_Event_and_Gender.png)

The lead CSV file contains 1,133 records and 8 variables. This category exhibits a slightly lower count of athletes, demonstrating a fluctuating pattern in the participation numbers.

![04_Athlete_Count_in_Lead_by_Event_and_Gender.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/04_Athlete_Count_in_Lead_by_Event_and_Gender.png)

Finally, the speed CSV file comprises a total of 833 records and includes 10 variables. In this category, there is a higher number of male participants, and the distribution of participants across competitions is nearly equal.

![05_Athlete_Count_in_Speed_by_Event_and_Gender.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/05_Athlete_Count_in_Speed_by_Event_and_Gender.png)

For men, the mean score in the qualifications round is 5.96, with a standard deviation of 0.92, while in the final round, the mean score is slightly lower at 5.86, with a standard deviation of 1.05. This indicates a relatively consistent performance pattern with a slight decrease in the finals. On the other hand, women exhibit a higher mean score of 8.32 in the qualifications round, with a standard deviation of 1.44, and a lower mean score of 7.52 in the final round, with a standard deviation of 1.14. The data suggests that men tend to have lower times that women.

![06_speed_boxplot.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/06_speed_boxplot.png)

## **Data Analysis:**

### Number of Medals Won during 2033

Out of the 67 countries participating in the 2023 sport climbing competitions, only 18 managed to secure medals. Japan emerged as the leader with an impressive total of 26 medals, followed by France with 16, and Indonesia securing 14. The accompanying bar chart illustrates a noteworthy trend—most medal-winning countries are situated in Europe, followed closely by Asian countries. This observation suggests that sport climbing exhibits a stronger presence in these continents. The distribution of medals reflects the prominence of climbing achievements in European and Asian nations, shedding light on the global landscape of sport climbing excellence.

![07_Total_Medals_Won_by_Country.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/07_Total_Medals_Won_by_Country.png)

![08_Total_Medals_Won_by_Gender.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/08_Total_Medals_Won_by_Gender.png)

Japan stands out as a standout performer in the Lead category, securing the highest number of medals among all countries. Additionally, Indonesia and China stand out in the Speed category, demonstrating their specialization in this fast-paced discipline. On the other hand, France emerges as a powerhouse in the Bouldering category, showcasing exceptional skill and dominance in this particular aspect of sport climbing. This diversity in strengths among countries adds an intriguing dynamic to the overall landscape of the 2023 sport climbing competitions, revealing a mix of specialties and expertise across different categories.

![09_Medals_Won_by_Discipline.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/09_Medals_Won_by_Discipline.png)

![10_Medals_Won_by_Country.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/10_Medals_Won_by_Country.png)

### Amount of Problems Solved in the Boulder Category

In the boulder category, the athlete who solves the most problems in the lowest number of attempts wins. The qualifications rounds have a set of 5 different problems and the finals a set of 4 different boulder problems. For instance, during the finals a perfect score would be 4 tops 4 zones 4 tops attempts 4 zone attempts (4t 4z 4 4), which means that the athlete complete each problem during the first try, also knows as flashed routes (In Finals, competitors can preview the boulder problems during a collective observation time (2 minutes per Boulder) but cannot attempt the problems.), each problem can be solved in different ways.

![11_Boulder_Final_Tops_Zones.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/11_Boulder_Final_Tops_Zones.png)

During the qualifications round across all competitions events, only three athletes were able to have a perfect score (5t 5z 5 5). 

![Screenshot from 2024-01-31 21-34-54.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/Screenshot_from_2024-01-31_21-34-54.png)

Only one athlete was able to have a perfect score during the semi finals and finals by first placed athlete Janja Garnbret during the Bern and Innsbruck competitions

![Screenshot from 2024-01-31 21-39-34.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/Screenshot_from_2024-01-31_21-39-34.png)

Boulder Final results

![boulder_finals.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/boulder_finals.png)

### Number of Tops and Highest Hold Reached in the Lead Category

In the Lead category, the aim for the competitors is to go as high as possible in an individual attempt on a 15 meters wall. The Lead ranking is set based on the height (hold number) achieved by the competitors. A competitor gets a “+” added to their score if moving in the direction of the next hold.

Athletes that reached top during semi final rounds

![lead_semi_finals.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/lead_semi_finals.png)

The semifinal rounds brought out some stellar performances, setting the stage for an exciting competition. In the men's category, Sorato Anraku from Japan proved his prowess by making it through both the Villars and Briançon events, showcasing a strong and consistent performance. Masahiro Higuchi, also from Japan, demonstrated his skills in the tough competition in Briançon. Taisei Homma and Colin Duffy, hailing from Japan and the USA respectively, secured their spots in the semifinals, adding an international flair to the mix. In the women's category, Janja Garnbret from Slovenia, Ai Mori, and Natsuki Tanii from Japan showed their mettle by navigating through the challenging rounds in Villars and Wujiang.

Athletes that reached top during the final rounds

![lead_finals.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/lead_finals.png)

Four athletes demonstrated impressive performances, reaching the top in the final rounds of their respective competitions. Janja Garnbret showcased exceptional skills by conquering the route in three different events: Villars, Bern, and Koper. Her consistency across these competitions underscores her prowess in the sport. Another notable performer is Sorato Anraku, who successfully completed two tops, one in Briançon and another in Koper.

![12_Count of Max Hold Reached by All Athletes Excluding TOPS.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/12_Count_of_Max_Hold_Reached_by_All_Athletes_Excluding_TOPS.png)

### Speed world records

The Speed results are based on who is the fastest to reach the top of a 15 meter wall. The competitors compete (race) in pairs on identical routes and the winner is the first to reach the top of the route.

![speed_records.png](/assets/Python%20~%20IFSC%20Climbing%20World%20Cups%202023%207454d097786e4060ad1aa6b03035f05a/speed_records.png)

The 2023 speed competitions witnessed a flurry of record-breaking moments, with athletes from around the world pushing the boundaries of what's possible in the sport of speed climbing. Veddriq Leonardo of Indonesia emerged as a trailblazer, smashing the 5-second barrier and setting a new world record in the men's category with an astonishing time of 4.98 seconds. This remarkable feat also secured him the Asian world record.

Not to be outdone, Aleksandra Miroslaw from Poland delivered a spectacular performance, breaking the women's world record not once but twice. During the Seoul speed competition qualification round, she blazed through the route in 6.37 seconds. However, it was in the finals where she truly left her mark, shattering the record with an incredible 6.25 seconds, establishing a new world and European record in the women's category.

Matteo Zurloni of Italy showcased his speed prowess in the Men's category, breaking the European record twice. His first triumph came in Seoul with a fast time of 5.23 seconds, only to outdo himself in the Chamonix event, where he set a new record at 5.14 seconds.

Crossing continents, Samuel Watson from the United States holds the current Men's Pan American record with a swift 5.02 seconds. On the women's side, Emma Hunt demonstrated exceptional speed, breaking the record twice – first in Seoul with 6.82 seconds and later in Villars with an improved time of 6.68 seconds.

Over in Oceania, Julian David of New Zealand showcased his speed prowess by breaking the men's record not once, but twice. Starting with 6.43 seconds in Seoul, he improved significantly in Villars with 5.83 seconds and further in Chamonix with an impressive 5.80 seconds.

Lastly, in the Men's category, the African speed record underwent a triple transformation by Hoshua Bruyns from South Africa. Beginning in Salt Lake City with 6.41 seconds, he broke it again in Chamonix with 5.99 seconds, and now holds the current record at an incredible 5.95 seconds in Bern.

## **Statistical Analysis:**

For this analysis, I want to measure if there is a linear correlation between the number of participations and the athlete’s height (based of gender) and reaching the finals. For this test, I will be using Pearson Correlation coefficient from scipy,stats.

**Null Hypothesis:** There is no significant linear relationship between the number of 'Participations' and reaching the finals. 

**Alternative Hypothesis:** There is a significant linear relationship between the number of 'Participations' and reaching the finals. 

- Pearson Correlation Coefficient: 0.0899601034970185
- P-value: 3.7487072552111553e-07

The p-value is extremely small (much smaller than the common significance level of 0.05), indicating strong evidence against the null hypothesis. Therefore, I would reject the null hypothesis that there is no significant linear relationship between the number of 'Participations' and reaching the finals.

The positive Pearson correlation coefficient (0.0899601034970185) suggests a positive correlation, but it's important to note that the correlation is relatively weak.

In summary, based on the results, I have statistical evidence to support the alternative hypothesis that there is a significant, albeit weak, positive linear relationship between the number of participations and reaching the finals.

---

**For Men:**

- **Null Hypothesis**: There is no significant linear relationship between the 'Height' and reaching the finals for men.
- **Alternative Hypothesis**: There is a significant linear relationship between the 'Height' and reaching the finals for men.
- **Pearson Correlation Coefficient:** -0.0620857939160329
- **P-value:** 0.009441085278548082

**For Women:**

- **Null Hypothesis**: There is no significant linear relationship between the 'Height' and reaching the finals for women.
- **Alternative Hypothesis**: There is a significant linear relationship between the 'Height' and reaching the finals for women.
- **Pearson Correlation Coefficient:** -0.09829249197061751
- **P-value:** 0.0001940484341312957

In both cases, the p-values are below the common significance level of 0.05, suggesting that I have enough evidence to reject the null hypothesis for both men and women. Therefore, there is a significant negative linear relationship between 'Height' and reaching the finals for both men and women.

The negative correlation coefficients indicate that as 'Height' decreases, the likelihood of reaching the finals increases. It's important to note that while the correlation is statistically significant, the strength of the correlation is relatively weak.