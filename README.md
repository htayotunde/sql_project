# sql_project The project involves analysing data from hotel booking for a period of 3 years to determine some trends and answer questions that can improve the hotel's revenue.
This data set contains booking information for a city hotel and a resort hotel, and includes information such as when the booking was made, length of stay, the number of adults, children, and/or babies, and the number of available parking spaces, among other things. In the project, I answered questions such as:
Is the hotel revenue growing per year?
Should the parking lot size be increased?
What trend can we see.
The data was imported into sql server, and queries were written to join the tables from 3 years booking, market survey and meal cost.
After merging the tables, visualization of the data was done using power bi. I visualized the trends in revenue over 3 years of hotel running, the average discount per year, total night bookings per year and required parking space per year. The revenue of the hotel grew between 2018 and 2019 and had a decline in 2020. There's no evidence to prove that there is a need to increase parking lot space as no regular trend was observed in the data.
The following are the queries from sql
with hotels as (
select * from dbo.['2018$']
union
select * from dbo.['2019$']
union
select * from dbo.['2020$'])
--select 
--arrival_date_year,hotel,
--sum ((stays_in_week_nights+stays_in_weekend_nights)*adr) as revenue from hotels
--group by arrival_date_year, hotel

--select * from dbo.market_segment$

select * from hotels
left join dbo.market_segment$
on hotels.market_segment = market_segment$.market_segment

left join dbo.meal_cost$
on meal_cost$.meal = hotels.meal
