# Using New York City Subway Data to Determine the Best Location for a Non-Profit to Meet Donors



![img](https://cdn-images-1.medium.com/max/1600/0*taMWCyQ4RLbha-Qs.jpg)

*I recently began a 12 week Data Science Immersive course with* [*Metis in downtown Seattle*](https://www.thisismetis.com/)*. Our first project, code named “Project Benson,” was to use data science and exploratory data analysis to select the best New York City subway stations for a non-profit to deploy their street teams to. The data set we worked with was large, with over 2 million rows of data — and the conclusions we ended up with were not what you might expect.*

You can find the [project repository for our code on Github here](https://github.com/luketibbott/benson), or view [our final presentation on Google Slides here](https://docs.google.com/presentation/d/1jDZImbDNbeA9glFQtSarLRoZ54hxOS9yoXN7saGNJjc/edit?usp=sharing).

### **Background & Problem Statement**

Our client, Women Tech Women Yes (WTWY), was a non-profit focused on empowering women in technology. They asked us to help them determine which subway stations would be the best to deploy their Street Team to, to get as much “bang for the buck” as possible. Their goal with the Street Team was not simply to meet people, but to meet people who would be:

1. Supportive of the type of work that WTWY does,
2. Interested in WTWY’s annual gala, held in early Summer each year, and
3. Capable of becoming long time donors.

Given these goals, WTWY pointed us towards New York’s MTA Turnstile Data set, [available here](http://web.mta.info/developers/turnstile.html). They asked us to use our knowledge of data science to inform their decision. Away we went!

### **Data**

**MTA Turnstile Data**

The [MTA Turnstile data set](http://web.mta.info/developers/turnstile.html) has detailed counts of the number of people who entered and exited each individual subway station in NYC— by date, time, and location. We looked at data from 4 weeks in May & June of 2018, since WTWY’s Gala is held in early Summer every year.

**Google Maps API**

We used the Google Maps API to determine the exact location and zip code of every single station in the New York City metro area.

**U.S. Census Income Data**

Building upon the Station location data we collected via the Google Maps API, we were able to use U.S. Census data from 2017 to find the number of households near each station with income over $100k.

### **Our Approach to the Problem**



![img](https://cdn-images-1.medium.com/max/1200/0*dbQc-NVQlbIXGxHu.jpg)

The sweet spot.

We took a 3-pronged approach: focusing on the intersection of **TRAFFIC, COMMUTERS, andHIGH INCOME.**

**1. TRAFFIC — Target subway stations with the greatest traffic.**

Charitable outreach is 100% a game of numbers. Street teams need to reach enough people to effectively engage and interest potential donors and gala attendees. Focusing on the subway stations with the greatest number of visitors was a no-brainer.

**2. COMMUTERS — Find “commuter” stations with a greater population of Native New Yorkers (not tourists).**

We chose to target stations that were likely to be frequented by local New Yorkers — residents, rather than stations like Times Square frequented by Tourists.

The best proxy for local New Yorkers was to target *commuters*, those who take the subway on weekdays to get to and from work.

The reason for this was simple. WTWY’s goal was not to simply spread their message, but to get people to attend their upcoming gala. Tourists and visitors might be interested in the organization’s message, but would not be likely to attend the gala.

**3. HIGH INCOME — Target donors with enough disposable income to attend the Gala and become long-term donors.**

There’s an old saying that goes:

> Someone asked the notorious outlaw John Dillinger, “Why do you rob banks?”

> John responded,

> *“Because that’s where the money is!!*”

Wealthy New Yorkers are much more attractive targets for the organization than non-wealthy New Yorkers who have less disposable income. Therefore, we used our knowledge of local geography and income demographics to identify areas where wealthy potential donors lived.

### **Methodology**

The first thing we did was plot the stations by total traffic. This data alone was highly valuable to us. For WTWY’s street team, their success is largely a game of numbers — and getting this data allows them to be smarter about where their street teams go.



![img](https://cdn-images-1.medium.com/max/1600/0*ihVvxntqERXS4Dgn)

Once we had determined which stations had the highest traffic, we wanted to combine that knowledge with our knowledge of which areas had the highest income. Using the Google Maps API, along with the US Census Data, we were able to create a scatter plot of subway stations by median daily subway traffic and number of high income residents who live nearby.

Based upon this plot, **we chose to focus on subway stations with at least 50,000 median daily riders, and at least 8,000 high income residents who lived nearby**. The resulting plot is below.



![img](https://cdn-images-1.medium.com/max/1600/0*1KJP7_VP9lOMcJRQ)

Now that we’d compared our first two target variables (traffic and income) to one another, it was time to bring in the third (commuters). For each station, we created a ratio that I like to call the **“Commuter Ratio”** to describe which stations had the most weekday traffic, relative to weekend traffic.

The reason for this was that we needed to target New Yorkers, not tourists, since tourists would not be able to attend WTWY’s gala, which they were holding several weeks later. The best way to find New Yorkers who were likely to still be in town was to target stations that had a lot of weekday traffic, rather than weekend traffic.

Looking at this graph, we chose to filter out stations with a Commuter Ratio ≤2. When we overlaid this filter on our previous chart (of volume vs. high income residents), we narrowed the stations down to the 5 stations that had the optimal blend of **high traffic, a large number of high-income residents, and a high Commuter Score.**

### Results

Based upon our analysis, we recommended these 5 subway stations:



![img](https://cdn-images-1.medium.com/max/1600/1*w-VVvYE_A1p9Nr5T_yzzcQ.png)

Going one step further, we took the top 5 subway stations and created a heat map of their traffic by time of day and day of week. This allowed WTWY to further target their marketing efforts. As you can see, Monday — Thursday make the most sense, and the 4 PM — 8 PM timeframe offers the highest possible traffic for most stations.



![img](https://cdn-images-1.medium.com/max/2000/0*U-yIikhMYbLaEYEK)

Blue = low traffic, red = high traffic.

### Post Mortem

In data science, it’s not uncommon for clients to be short on time or money. Given an abundance of both, there are a few areas where we’d like to dig deeper. Specifically, we’d like to:

- Drill down further on income data. We were able to find number of high income residents by zip code, but with more time or know-how we’d like to be able to find and use “block-by-block” income data.
- Look into the net inflow/outflow of commuters at each station. Our analysis generally looked at the total (daily inflow+outflow) per station.
- Create a “Tech Score” similar to a “Walk Score” to determine the likelihood that people in a certain area would be most receptive to WTWY’s “women in tech” focus. We could target subway stations around large employers, for example.

Overall, our team had a great time exploring the data and coming up with recommendations for our non-profit client. The fact that we were able to pull all of this together in just 3 days (Tuesday — Thursday) for our presentation on Friday morning was somewhat of a minor miracle.

Thanks for reading. Until next time!