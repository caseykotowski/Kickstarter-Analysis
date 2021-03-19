# Kickstarter Campaign Analysis
## Overview
An analysis of Kickstarter data to uncover trends in successful vs unsuccessful fundraising campaigns
### Purpose
This analysis of Kickstarter campaigns was created to guide future campaigns, with an emphasis on US based plays, and British based musicals.
I am focused on US plays to help a playwrite named Louise plan a Kickstarter campaign to fund a production of a play in the US. She has estimated that it will cost her $10,000 to produce her play, "Fever", and she wants to know if there are any lessons she can learn from previous campagins. 

## Analysis and Challenges
The first step in analysis was breaking down the types and subtypes of campaigns, and sorting by outcome. The potential outcomes were 'successful', 'failed', 'canceled', and 'live'. I disregarded the 'live' outcome, since it would be difficult to draw conclusions from a campaign not yet finished. 

In the file is a pivot chart showing the subtypes' outcomes for all campagins in my data set. Plays are by far the most commonly started, but also successful campagin subcategory. Below is a stacked bar chart of campagin outcomes by subcategory. You can see the volume of plays, but also the towering amount of successful plays. This first basic analysis proves hopeful for Louise. 


![Visualization of Campaigns by Subcategory](https://github.com/caseykotowski/Kickstarter-Analysis/blob/main/Kickstarter%20Outcomes%20by%20SubCategory.PNG "Outcomes by Subcategory")


To confirm this, I further sorted the outcomes by subcategory for just the Theater category group. 
![Visualization of Campaigns by Theater Subcategory](https://github.com/caseykotowski/Kickstarter-Analysis/blob/main/Kickstarter%20Outcomes%20by%20Theater%20Subcategory.png "Outcomes by Theater Subcategory")

Next, I wanted some descriptive statistics. I started with the central tendencies of mean, and median for all US based kickstarters. The average successful campagin asked for around $5,000, whereas the average failed campagin doubled the goal with an average of over $10,000. The Upper Quartiles of successful and failed campaigns confirm that successful campagins tend to ask for less money.

I also took those data points for how much was pledged for successful and failed US kickstarters. The successful campagins' data points for pledged line up closely with the goal, showing that they were able to get just enough people to pledge to reach their goal. For failed campagins, the pledged amounts were significantly lower. This shows that most failed campaigns are not even close to reaching their goal. 

![Descriptive Statistics](https://github.com/caseykotowski/Kickstarter-Analysis/blob/main/Descriptive%20Statistics%20Capture.png "Descriptive Stats-All US")

Digging in a little deeper, and for the play subcategory specifically, I pitted successful, failed, and canceled play campaigns against each other by goal ranges. 
To do this, I used the `COUNTIFS` function, and created a line graph to visualize outcomes by goal range. 



### Analysis of Outcomes Based on Launch Date
Now that we understand that it's possible to be successful in fundraising for a play, I wanted to see if there are any other variables that increase success. We have the data for when campagins are started, so I sorted by date. Looking at the below chart time of year is correlated to success in plays, and it shows that the summer months are the most common time of year to start theater campaigns and the most common time of year for successes. Specifically, May is the most successful month. As for months to avoid, failed theater campaings peak in October. If Louise wants to maximize her chances at success, she should avoid starting in October and wait for May - even if that's well before she wants to begin production. 


![Theater Outcomes by Launch Date](https://github.com/caseykotowski/Kickstarter-Analysis/blob/main/Resources/Theater_Outcomes_vs_Launch.png "Outcomes by Launch Date")


### Analysis of Outcomes Based on Goals

Earlier, I did some surface level analysis of average goals for the different outcomes for all US Kickstarters. Now, I want to show Louise which goal ranges are most successful for a US based play. The ranges went up incrementally by $5,000 , and I counted for how many successful, failed, and canceled US based play campaigns to find the optimum range for success. Louise thinks she needs $10,000 , but will she be successful asking for that? 

Using the `COUNTIFS` function, I filtered for the dollar range, the plays subcategory, and the United States. 

After double checking my code by hand counting some of the goal ranges, I was confident that my criteria and ranges were correct. Below is a sample of the way I used the function.

`=COUNTIFS(Kickstarter!F:F,"successful",Kickstarter!D:D,">=15000",Kickstarter!D:D,"<=19999", Kickstarter!R:R,"plays", Kickstarter!G:G, "US")`

I summed for total projects in the range, and took the percentages, I then converted the data into a line chart that shows which outcome dominates the different goal ranges. 

![Outcomes by Goals](https://github.com/caseykotowski/Kickstarter-Analysis/blob/main/Resources/Outcomes_vs_Goals.png "Outcomes by Launch Date")

The outcomes occilate between ranges, but under $15,000 play campagins are more often success than failures. This was an interesting result to me, because when analyzing all of the US kickstarters, the average successful goal was around $5,000.

### Challenges and Difficulties Encountered

The `COUNTIFS` function was my greatest challenge. I understood they syntax of listing the range the function would look at, and then the criteria for counting (and then repeating for all of the criteria I wanted applied), but understanding exactly how to count the range was difficult. It took several tries to count all of data points in between each goal value. I made sure to use the greater than **or equal to** and the less than **or equal to** to capture all of the points. I initially wanted the whole range in one criteria, but I finally understoon I could use two criteria and both filters would apply to the count. Then I had to add in all of the other filters. Remembering to filter by subcategory and by country led to a chart that looked very different from the checkpoint listed in the challenge instructions. 


## Results
To summerize outcomes by month, plays are most likely to succeed in April through August, with the greatest frequency of success in May. There are the fewest successes in December, but there is a peak of failed kickstarters in October, so I do not recommend starting fundraising in the Fall and Winter. 

For outcomes by goals, plays consistently have more success with goals under $15,000. 

So, my overall recommendation is for Louise to set the goal for the full $10,000 and to start the campaign in May. 

These recommendation come with a caveat, there are some limitations to pure data analysis for this questions. Kickstarter is all about convincing people - possibly complete strangers - to fund your passion project. There are going to be subjective qualities that cause people to want to donate. Creating a compelling introduction to your project is crucial, as are the rewards for pledges. Many campaigns offer rewards for different levels of donation. 

I think the best way to quantatatively measure successful pledge rewards is to analyze average pledge per person vs outcome, and collect data on number of pledge levels. I would like to see frequency of pledge levels in a histograph to show how much the average person is willing to donate. 

But despite the limitations, I hope my analysis can be helpful to those planning a kickstarter campaign. 
