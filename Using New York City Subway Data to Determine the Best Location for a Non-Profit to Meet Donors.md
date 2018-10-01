### Using New York City Subway Data to Determine the Best Location for a Non-Profit to Meet Donors

![image-20180930200423852](/Users/brenner/Library/Application Support/typora-user-images/image-20180930200423852.png)

I recently began a 12 week Data Science Immersive course with Metis in downtown Seattle. Our first project, code named "Project Benson," was to use data science and exploratory data analysis to select the best New York City subway stations for a non-profit to deploy their street team. The data set we worked with was large, with over 2 million rows of data - and the conclusions we ended up with were not what you might expect.



---



**Background & Problem Statement**

Our client,  Women Tech Women Yes (WTWY), was a non-profit focused on empowering women in technology. They asked us to help them determine which subway stations would be the best to deploy their Street Team to, to get as much "bang for the buck" as possible. Their goal with the Street Team was not simply to meet people, but to meet people who would be:

1. Supportive of the type of work that WTWY does,
2. Interested in WTWY's annual gala, held in early Summer each year, and
3. Capable of becoming long time donors.



Given these goals, WTWY pointed us towards New York's MTA Turnstile Data set, [available here](http://web.mta.info/developers/turnstile.html). They asked us to use our knowledge of data science to inform their decision.



---



<u>**Data**</u>

*MTA Turnstile Data*

The MTA Turnstile data set has detailed counts of the number of people who entered and exited each individual station - by date, time, and location. We looked at data from 4 weeks in May & June of 2018, because WTWY's Gala is held in early Summer every year.

*Google Maps API*

We used the Google Maps API to determine the exact location and zip code of every single station in the New York City metro area.

*U.S. Census Income Data*

Building upon the Station location data we collected via the Google Maps API, we were able to find the number of households near each station with income over $100k.



---



<u>**Our Approach to the Problem**</u>

![image-20180930172643750](/Users/brenner/Library/Application Support/typora-user-images/image-20180930172643750.png)

We took a 3-pronged approach: focusing on the intersection of *volume, commuters*, and *high income.*

1. ***VOLUME*** - *Target subway stations with the greatest traffic.*
   Charitable outreach is 100% a game of numbers. Street teams need to reach enough people to effectively engage and interest potential donors and gala attendees. Focusing on the subway stations with the greatest number of visitors was a no-brainer.

2. ***COMMUTERS*** - *Find "commuter" stations with a greater population of Native New Yorkers (not tourists).*

   We chose to target stations that were likely to be frequented by local New Yorkers - residents, rather than stations like Times Square frequented by Tourists.

   The best proxy for local New Yorkers was to target *commuters*, those who take the subway on weekdays to get to and from work.

   The reason for this was simple. WTWY's goal was not to simply spread their message, but to get people to attend their upcoming gala. Tourists and visitors might be interested in the organization’s message, but would not be likely to attend the gala.

3. ***HIGH INCOME*** - *Target donors with enough disposable income to attend the Gala and become long-term donors.*

   There's an old saying. Someone asked the notorious outlaw John Dillinger,

   ​	"Why do you rob banks?"

   John responded,

   ​	"*Because that's where the money is!!*"

   Wealthy New Yorkers are much more attractive targets for the organization than non-wealthy New Yorkers who have less disposable income. Therefore, we used our knowledge of local geography and income demographics to identify areas where wealthy potential donors lived.


---



**Results**

![img](https://lh6.googleusercontent.com/WQgeOoK1Axgk4Ylp3dBOEPI_Sd7LSRpCh-TzsPK5Ubr8doU359wtIYCMNf6s-4ejDNX3ZrBHRILiAwBXr6X2dQbtyT6FIkEn0Gbg43kiOtIFwiyWfcZ8W2ezD31BoqGNxKqd9-Jzsdo)

 ![img](https://lh4.googleusercontent.com/s6vyyMw6H1LJt24hDnbiPhD6zju3lnKFc1k55P2M8BdIBgok5drw11QaRtbLyoJTXHSnXaO9aGKU4A_9640vmU3a0sa8qcP7W4dfP4CTG_-9Uwibe0Xl6nWA16AQYXjo1PiQk4hlB9Q)

![img](https://lh3.googleusercontent.com/klGo6vIrKkWTSmiVN3ddqi7AJdjM_PlFifv7xkMPICX0JRP9-FB6kozsCsiVbUS6XaSP3SNBnO4A5oV7lpH-rqmbYpqtv8h_I-yEURvN3J8w-3MNekscWR2-M_NSrSPYbEwlhy9FEeg)

![img](https://lh6.googleusercontent.com/2fv84ZU3HwACPrv5Elnk4mPPPe2bSlip5E7KRf306_apc2_sdYrSGvjoNjOG4uy_9Qb9mzaGy8hNL5M9Fhl18Iv3bJXRInQJuEO4IVVp6g0gqjyM7iYEHoO7uKGYerLDLTFTuMM4vCc)

![img](https://lh4.googleusercontent.com/2ANS__JXFslx7HHUMvNS6Uxbg9hd6-5Fzzwws5WDbLRJ83vn8TiihmiboE_qCSRrwGfswX78xvkFXm8D3d4Co27ixArl9rpmmQdOhC5rBIvP6m5FaZxR6aoDr-2V02oMKaexTZXzbUI)![image-20180930200857636](/Users/brenner/Library/Application Support/typora-user-images/image-20180930200857636.png)