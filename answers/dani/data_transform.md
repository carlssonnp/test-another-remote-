1. Find all the flights that: (answering with nrow())

Departed in summer. **86995**

That flew to Houston (IAH or HOU). **9313**

There were operated by United, American, or Delta. **139504**

That were delayed by more two hours. **9723**

That arrived more than two hours late, but didn’t leave late. **3**

Were delayed by at least an hour, but made up over 30 minutes in flight. **0**

Departed between midnight and 6am. **133**


2. How many flights have a missing dep_time? What other variables are missing? What might these rows represent?
3. 
	**8255 missing dep_time. Also missing dep_delay, arr_time, arr_delay, air_time. These are probably cancelled flights**

3. How could use arrange() to sort all missing values to the start? (Hint: use is.na()).

	**arrange(df, desc(is.na(x)))**

4. Sort flights to find the most delayed flights. Find the flights that left earliest. 
 
    **done in R**

5. Brainstorm as many ways as possible to select dep_time, dep_delay, arr_time, and arr_delay from flights.

	**select(flights, dep_time, dep_delay, arr_time, arr_delay)**
	**select(select(flights, dep_time:arr_delay), starts_with("dep"), starts_with("arr"))**

6. Currently dep_time and arr_time are convenient to look at, but hard to compute with because they’re not really continuous numbers. Convert them to a more convenient representation of number of minutes since midnight.

	**done in R**

7. Compare airtime with arr_time - dep_time. What do you expect to see? What do you see? Why?

	**should be pretty close, but in fact arr_time - dep_time is usually a lot bigger than air_time - this could be due to "padding" some airlines do, or perhaps air_time is a precise measure air control keeps track of versus arr_time and dep_time is not.**

8. Find the 10 most delayed flights each day using a ranking function. How do you want to handle ties? Carefully read the documentation for min_rank().

	**get it with something like (not exactly ...)
	by_day <- group_by(flights, year, month, day)
	mutate(by_day, rank = min_rank(desc(dep_delay)))**

9. Brainstorm at least 5 different ways to assess the typical delay characteristics of a group of flights. Consider the following scenarios:

	A flight is 15 minutes early 50% of the time, and 15 minutes late 50% of the time.

	A flight is always 10 minutes late.

	A flight is 30 minutes early 50% of the time, and 30 minutes late 50% of the time.

	99% of the time a flight is on time. 1% of the time it’s 2 hours late.


	**The same flight every day (from same departure to arrival) is delayed
		or early by a certain percentage.**
	**A certain carrier experiences more delay than other carriers.**
	**More delays are experienced by flights in certain months (winter, summer?)**
	**Discover the flights "rush hour", time of the day when most flights are delayed**
	**Study if delays increase during holiday times, how often before a holiday delays begin and when after a holiday delays return to "normal"**


10. Which is more important: arrival delay or departure delay?

	**I'd argue that from a customer perspective, departure delay is more important because customers experience more anxiety to get on the plane. Once they are on the plane, they get closer to their destination and believe the captain can speed up arrival.**

11. Look at the number of cancelled flights per day. Is there are pattern? Is the proportion of cancelled flights related to the average delay?

	**
	flights %>% 
	filter(is.na(dep_delay), is.na(arr_delay)) %>%
	group_by(year, month, day) %>%
	summarise(n = n()) %>%
	ggplot(aes(day, n)) + geom_point() 

	flights %>% 
	  group_by(year, month, day) %>% 
	  summarise(day_delay = mean(dep_delay, na.rm = TRUE)) %>%
	    ggplot(aes(day, day_delay)) +
	    geom_point() + 
	    geom_smooth(se = FALSE)
    **
	Yes, there is a pattern between cancelled flights and avg delay. It appears that both delays and cancellations begin to increase in the first few days of the month, decline in the middle of the month, and increase again.


12. Which carrier has the worst delays? Challenge: can you disentangle the effects of bad airports vs. bad carriers? Why/why not? (Hint: think about flights %>% group_by(carrier, dest) %>% summarise(n()))
	**
	flights %>% 
	  group_by(carrier) %>% 
	  summarise(car_dep_delay = mean(dep_delay, na.rm = TRUE), car_arr_delay = mean(arr_delay, na.rm = TRUE)) %>%
	  arrange(desc(car_dep_delay), desc(car_arr_delay))

	  Frontier Airlines has the worst departure and arrival delays.

	  flights %>% 
  group_by(dest, carrier) %>% 
  summarise(car_dep_delay = mean(dep_delay, na.rm = TRUE), car_arr_delay = mean(arr_delay, na.rm = TRUE)) %>%
  arrange(desc(car_dep_delay), desc(car_arr_delay))

  I speculate that airports with delays are + corr. with airlines with delays.
  **

13. Refer back to the table of useful mutate and filtering functions. Describe how each operation changes when you combine it with grouping.
* **after using group_by(), all operations used within mutate and filtering are applied per group, not on the entire dataset.**


Which plane (tailnum) has the worst on-time record?
* flights %>% 
  group_by(tailnum) %>% 
  summarise(on_time = mean(arr_delay, na.rm = TRUE)) %>%
  arrange(desc(on_time))
* **N844MH has the most arrival delay**

What time of day should you fly if you want to avoid delays as much as possible?
* flights %>% 
group_by(hour) %>% 
summarise(hour_delay = mean(dep_delay, na.rm = TRUE)) %>%
ggplot(aes(hour, hour_delay)) +
geom_point() + 
geom_smooth(se = FALSE)

* **To avoid departure and arrival delays (which steadily increases later in the day), it's best to travel in the early morning.** 

Delays are typically temporally correlated: even once the problem that caused the initial delay has been resolved, later flights are delayed to allow earlier flights to leave. Using lag() explore how the delay of a flight is related to the delay of the flight that left just before.

* **observed some small positive corr. between dep_delay and the lag**

Look at each destination. Can you find flights that are suspiciously fast? (i.e. flights that represent a potential data entry error). Compute the air time a flight relative to the shortest flight to that destination. Which flights were most delayed in the air?
* flights %>%
group_by(dest) %>%
mutate(airtime_sd = (air_time - min(air_time, na.rm = TRUE)), r = rank(desc(airtime_sd))) %>%
select(dest, r, airtime_sd) %>%
filter(r == 1) %>%
arrange(desc(airtime_sd)) 

* **Flights to SFO had the highest airtime difference from the minimum airtime**

Find all destinations that are flown by at least two carriers. Use that information to rank the carriers. 
* flights %>%
group_by(dest) %>% 
summarise(carriers = n_distinct(carrier)) %>% 
filter(carriers > 1) %>%
arrange(desc(carriers))
* **there are 76 destinations that are flown by at least 2 carriers. **