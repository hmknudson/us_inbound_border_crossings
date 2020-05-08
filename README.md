# COMPARING U.S. INBOUND BORDER CROSSINGS - A/B TESTING 2012 V. 2018
## 1. Introduction

This dataset comes from [Kaggle](https://www.kaggle.com/akhilv11/border-crossing-entry-data), but the data was originally collected by the United States Bureau of Transportation Statistics. The data provide information on the number of inbound US border crossings in each type of conveyance (i.e., truck, train, pedestrian, etc.), for all 116 ports of entry in US states that share a border with either Mexico or Canada. Data for all 4 states that border Mexico and 11 of the 13 states that border Canada are included in the dataset, which covers all years from 1996 to 2019.

Border crossing in the US is an incendiary topic in current politics, as various actors claim that border crossing has increased in recent years, while others claim the opposite. Notably, the current US President, Donald Trump, campaigned on the promise to construct a [wall](https://www.nytimes.com/2019/09/18/us/politics/trump-border-wall.html) at the US-Mexico border to keep Mexicans and Central Americans from entering the country illegally. He has also [insulted](https://time.com/4473972/donald-trump-&/) Mexican-American immigrants, Mexicans, and the country of Mexico numerous times throughout his campaign and subsequent presidency. 

Moreover, the large amount of shootings that have been occurring in the US prompted Venezuela and Uruguay to issue travel [advisories](https://www.cnn.com/2019/08/06/americas/venezuela-uruguay-travel-warnings-us/index.html), warning their citizens to avoid traveling to the US, if possible.

Considering President Trump’s rhetoric and the existence of concerns about traveling to the US, it would be interesting to examine the inbound US border crossing data from several years before President Trump took office, compared to the present day, in order to see what trends there may be.

## 2. Research Question & Hypotheses

***Research Question***

Is there a significant difference in inbound US border crossings between 2012 (the year President Obama was re-elected)  and 2018 (about half of the way through President Trump’s time in office)?

***Hypotheses***

**Hypothesis 1:**

Ho: There is no significant difference in overall inbound US border crossings from 2012 to 2018.

Ha: There is a significant difference in overall inbound US border crossings from 2012 to 2018.

**Hypothesis 2:**

Ho: There is no significant difference in inbound US-Mexico border crossings between 2012 and 2018.

Ha: There is a significant difference in inbound US-Mexico border crossings from 2012 to 2018.

**Hypothesis 3:**

Ho: There is no significant difference in inbound US-Canada border crossings from 2012 to 2018.

Ha: There is a significant difference in inbound US-Canada border crossings from 2012 to 2018.

**Hypothesis 4:**

Ho: There is no significant difference in inbound US border crossings between the US-Mexico and US-Canada borders.

Ha: There is a significant difference in inbound US border crossings between the US-Mexico and US-Canada borders.

# 3. Data

The dataset is a CSV file downloaded from Kaggle, and it contains a total of 346,733 observations and 8 columns. There are no null values. 116 unique ports of entry are represented, with 80,546 records from the US-Mexico border and 266,187 records from the US-Canada border.

# 4. Methods

For this analysis, I'm going to create a dataframe called people_crossing that just includes the conveyances that count people - Personal Vehicle Passengers, Bus Passengers, Pedestrians, and Train Passengers. The other types (e.g., Rail Containers Full, Trucks, etc.) are a measure of how many of those types of conveyances crossed the border, but they aren't counting the people in them. I want to make sure I'm only looking at individuals who crossed the border, not freight containers.

Then, I will run some descriptive statistics on the people_crossing dataset as a whole, to see what we're dealing with. After that, I will move into inferential statistics and test the four hypotheses that were laid out earlier. All relevant tests will be conducted at the 95% confidence interval.

For the first hypothesis (whether or not there is a significant difference between inbound border crossings in 2012 and 2018), I will first check if the 'value' variable is normal. If it is, I'll run a t-test, and if not, I'll use the Mann-Whitney U to test the means or medians of the 'value' variable (number of crossings) between 2012 and 2018. From there, I will test for differences among the number of people who crossed in each conveyance type, and among each state's number of crossings, from 2012 to 2018. To do this, I'll separate people_crossing into 4 separate datasets - one for each type of conveyance in the year 2012. I'll then use either the independent t-test or the Mann-Whitney U to test the median amount of crossings for each conveyance type between 2012 and 2018 Then, I'll do the same for states.

For the second and third hypotheses, I will proceed in exactly the same way. For the second hypothesis, I will separate all US-Mexico records off of the original people_crossing dataset Likewise, for the third hypothesis, I will be dealing only with the US-Canada border crossings. Then, when it is time to look specifically at conveyances, rather than testing again for differences in conveyance types between 2012 and 2018, I will look within 2012 and within 2018, respectively, using an ANOVA test (either parametric or non-parametric) to see if the usage of any one conveyance type is significantly different from the other conveyance types used in a specific year. 

Supposing the chosen ANOVA test comes out significant, I'll then use either the Tukey HSD (if parametric) or Dunn's test (if non-paramentric) as a post-hoc test to determine which sample(s) stand out from the others. I will not do this with states, since I already tested for differences between states as a part of the first hypothesis.

For the fourth hypothesis, I will use either a t-test or a Mann-Whitney U test to determine if there is a significant difference between the amount of border crossings that occur at the US-Mexico border vs. the US-Canada border. I will run two tests - one for 2012 and one for 2018. Following these tests, I will make lineplots that depict the rate of border crossings by month for the US-Canada and US-Mexico borders, to better visualize the comparison between them.
