#  2008 FAA Flight Data Analysis and Visualization
## by Gary Cheng


## Dataset


This dataset comes from the Bureau of Transportation Statistics, and contains flight on-time performance data that includes , minutes of arrival/departure delays, flight delay reason, origin/destination airport, airline, whether the flight is cancelled/diverted, flight cancellation reason, and some other flight related attributes for all scheduled domestic flights within the United States in 2008 totalling to roughly 7 million in number.

Below a summary of data wrangling steps taken:

- Changing column data types appropriate one as needed for further analysis
- Downcasting data types from Int64, Float64 to lower bit where possible without sacrificing calculation accuracy to save memory, as this a     large dataset
- Added columns to denote the arrival and departure hour, extracted from CRSArrTime and CRSDepTime
- Added column for actual name of the airport in addition to the airport code
- Added columns for the states of the origin and destination airports
- Removed columns that will be used for analysis


## Investigation Overview
From a 2010 study in an annual U.S. impact of flight delays, it was found that 

*Flight delay is a serious and widespread problem in the United States. Increasing flight delays place a significant strain on the U.S. air travel system and cost airlines, passengers and society many billions of dollars each year. The 8.3 billion airline component consists of increased expenses for crew, fuel and maintenance, among others. The 16.7 billion passenger component is based on the passenger time lost due to schedule buffer, delayed flights, flight cancellations and missed connections. The 2.2 billion cost from lost demand is an estimate of the welfare loss incurred by passengers who avoid air travel as the result of delays.*

Source: https://www.airlines.org/data/annual-u-s-impact-of-flight-delays-nextor-report/

I want to look at the impact of flight delays in terms of airports, airlines, and scheduled flight times.  These factors are directly related to airline passengers.  The answers to the questions below may help us mitigate flight delays the next time we fly. 

## Summary of Findings

- Arrival and Departure delays minutes are highly correlated. Interestingly, there's a moderate correlation bewtween TaxiIn and TaxiOut minutes with NAS Delay minutes.  It would make sense since it has to do the national aviation system and probably affects air traffic control.  All of the other highly correlated features such as ArrDelay, DepDelay, and the delay types would be expected.

- As expected, both ArrDelay and DepDelay are highly correlated with each of the delay types (carrier, weather, NAS, security, late aircraft). None of the other numeric variable pairs show significant correlation between each other.

- Flight distance seem to exhibit a weak correlation with ArrDelay and DepDelay, as well as the delay types.

- The time of year definitely affects flight delay performance. 

- There are a suprising amount of departing flights early on during the day at 6am and 7am, where I would assume there to be less flights than later on during the day.  In terms of cancellation reason, I expected a majority of cancellations to be from weather.  However, it looks like the airlines cancel flights at roughly the same number as ones due to weather.

- There are definitely more delays for shorter distance flights (between 0 and 2000 miles), but they also happen much more often as many flights are under 2000 miles within the US.

- As a whole, the amount of delays is the greatest in the month of December, and the least in October.  Weather probably plays a factor in this as 4 of the top 5 months where delay is the greatest occurs between December and March.

- States in the east coast (NJ, NY) and midwest (IL) gets hit with a lot of delays.  Suprisingly, none of the west coast states are in the top 10 list of the worst amount of delays

- The worst time in terms of flight delays is between between the hours of 5pm and 8pm, and it also makes sense that the least delay occurs between the 5am and 7am hours.

- Looking at the number of flight cancellations by origin airports, Chicago O'Hare has a significantly higher number of cancellations out of the top 10 airports, followed by Dallas-Forth Worth and Atlanta.

- Number of diverted flights peaked in December, and also in June.  I think this may be due to the winter weather in December and the hurricanes and tornadoes in the summer.

- Chicago O'Hare (ORD) has the most share of cancelled flights.  Also we see that it has also a much high percentage of cancellation due to NAS, which is the national aviation system.

-  We see that even though American Eagle has the most cancellations, only about 15% is within their control.  Whereas for #2 American Airlines we see that carrier cancellation accounts for about 60% of its cancellations.  Southwest and United also have high percentage of carrier cancellations at 50% or more.




## Key Insights for Presentation


### Overall Percentages of Delayed Flights

FAA considers a flight to be delayed when it is 15 minutes later than its scheduled time.  22.2% and 19.3% of flights experience delays of 15 minutes or more, for arriving and departing flights, respectively.

### Which airline has the most scheduled flights?

Southwest has by far the most number of flights out of all airlines, doubling that of American Airlines.  

### What are the best and worst months to fly in terms of delays?

As a whole, the amount of delays is the greatest in the month of December, and the least in October.  Weather probably plays a factor in this as 4 of the top 5 months where delay is the greatest occurs between December and March.


### What day of the week has the most and least amount of delay?

Weekdays have about the same number of scheduled flights, and is what I would expect because of business travellers.  Saturday has the least amount of scheduled flights.

### Which hour should you choose to fly to avoid delays?

The worst time in terms of flight delays is between between the hours of 5pm and 8pm, and it also makes sense that the least delay occurs between the 5am and 7am hours.

### Which airlines suffers from the most amount of arrival delays?

Chances are you will get more delay with JetBlue, though they don't have control of it most of the time.  Your best bet might be to choose Alaska, Hawaiian, Frontier, and Aloha airlines.

### Which airports suffer the most delays in the US?

Included in the top 20 list are airports with delays sorted in descending order.  Looking at the chart, I don't even know half the airports in the list. Maybe it's more useful to just plot out the top 20 airports in terms of number of scheduled flights.  This may give a better idea of the major airports which affects more passengers overall.


### Which of the busiest airports in the US suffer the most delays?

Below we have a plot that only includes the top 20 airports in the US as a subset in terms of number of scheduled flights to give a better picture of the average arrival delays where most people tend to fly to.  Newark, O'Hare, and JFK seem to be notorious ones with the worst delays in the country.  They are also major airline hubs.


### Which airlines have the high number of flight cancellations?

Of all the airlines, American Eagle and American Airlines have the most cancellations.  If you look at the cancellation due to carrier (within the airline's control), you will see that American Airlies is on the top of the list.  Even though American Eagle has the most cancellations, only about 15% is within their control.  Whereas for #2 American Airlines we see that carrier cancellation accounts for about 60% of its cancellations.  Southwest and United also have high percentage of carrier cancellations at 50% or more. Of course there are also other factors that causes cancellation that are out of the control of airlines, such as NAS, security, and weather.

### What are the best and worst months to fly in terms of cancellations?

You're least likely to experience a flight cancellation dueing the months of October and November, while the winter months tops the list, and certainly most of it due to weather!

### Which states experience the most cancellations?

Illinois, Texas, and California round out the top 3, followed by New York.  I'd say it's probably due to the large number of flights that these states have.