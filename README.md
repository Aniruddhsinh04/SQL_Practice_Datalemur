# Practicing SQL with DataLemur
This repository documents my SQL practice journey using [DataLemur](https://datalemur.com), a platform designed for honing SQL skills through real-world problems. I'm excited to share my learning process with you!
# About This Repository
This repository is a living document, showcasing my SQL practice and the lessons I learn along the way. Each entry will detail the problem, my solution, and key takeaways. I aim to present the code in a clear and organized manner, highlighting the different SQL concepts I'm mastering.

Thanks for visiting my portfolio!
# Disclosure
The questions represented herein are from "How to Ace the Data Science Interview". The reproduction of questions here is not a statement of ownership, creation, or done for or with the intent for profit. This is an educational exercise intended to demonstrate my commitment to learning more about the tools used in the analytics industry. The full question along with data dictionaries can be located on the Datalemur site and have not been consistently, if at all reproduced, here for the author's convenience.
# How Entries Are Logged
- Question Title | Difficulty | Company Question is From | Date Completed
- Question
- Code Answer
- Number of Tries
- Lessons Learned, New Skills Practiced, Notable Failures
# Table of Contents  

## Easy Questions
- [Data Science Skills | Easy | LinkedIn | 09/07/2024](https://github.com/Aniruddhsinh04/SQL_Practice_Datalemur?tab=readme-ov-file#data-science-skills--easy--linkedin--09072024)
- [Average Post Hiatus (Part 1)| Easy | Facebook | 09/20/2024](https://github.com/Aniruddhsinh04/SQL_Practice_Datalemur?tab=readme-ov-file#average-post-hiatus-part-1-easy--facebook--09202024)
- [Laptop Vs Mobile Viewership | Easy | New York Times | 09/14/2024](https://github.com/Aniruddhsinh04/SQL_Practice_Datalemur?tab=readme-ov-file#laptop-vs-mobile-viewership--easy--new-york-times--09142024)
- [App Click-through Rate (CTR) | Easy | Facebook | 09/20/2024](https://github.com/Aniruddhsinh04/SQL_Practice_Datalemur?tab=readme-ov-file#app-click-through-rate-ctr--easy--facebook--09202024)
- [Who Made Quota? | Easy | Oracle | 09/21/2024](https://github.com/Aniruddhsinh04/SQL_Practice_Datalemur/blob/main/README.md#who-made-quota--easy--oracle--09212024)

## Medium Questions
- [Placeholder]()

## Hard Questions
- [Placeholder]()

# Question Responses
Note: Questions ordered by most recent date.

## Who Made Quota? | Easy | Oracle | 09/21/2024
- Question: Write a query that outputs each employee id and whether they hit the quota or not ('yes' or 'no'). Order the results by employee id in ascending order.
````
SELECT DISTINCT deals.employee_id,
CASE 
  WHEN SUM(deal_size) OVER(PARTITION BY deals.employee_id) >= quota THEN 'yes' 
  ELSE 'no'
END AS made_quota
FROM deals
JOIN sales_quotas
  ON deals.employee_id = sales_quotas.employee_id
ORDER BY deals.employee_id ASC;
````
![Image](https://github.com/Aniruddhsinh04/SQL_Practice_Datalemur/blob/main/Images/Who_Made_Quota/snap.png)
- Number of Tries: 5
- Lessons Learned: 

## Average Post Hiatus (Part 1)| Easy | Facebook | 09/20/2024
- Question: Write a query to find the number of days between each user’s first post of the year and last post of the year in the year 2021. Output the user and number of the days between each user's first and last post.
````
SELECT user_id,
ROUND(EXTRACT(EPOCH FROM (MAX(post_date) - MIN(post_date))) / 86400) AS days_between 
FROM posts
WHERE EXTRACT(Year from post_date) = '2021'
GROUP BY user_id
HAVING COUNT(user_id) >= 2
````
![Image](https://github.com/Aniruddhsinh04/SQL_Practice_Datalemur/blob/main/Images/Average_Post_Hiatus/snap.png)
- Number of Tries: 2
- Lessons Learned:

## App Click-through Rate (CTR) | Easy | Facebook | 09/20/2024
- Question: Write a query to calculate the click-through rate (CTR) for the app in 2022 and round the results to 2 decimal places.
````
SELECT app_id,
ROUND(100.0 *COUNT(CASE WHEN event_type = 'click' THEN 1 END) / COUNT(CASE WHEN event_type = 'impression' THEN 1 END), 2)
FROM events
WHERE EXTRACT(YEAR FROM events.timestamp) = '2022'
GROUP BY app_id
````
![Image](https://github.com/Aniruddhsinh04/SQL_Practice_Datalemur/blob/main/Images/App_Click_through_Rate/snap.png)
- Number of Tries: 2
- Lessons Learned:

## Laptop Vs Mobile Viewership | Easy | New York Times | 09/14/2024
- Question: Write a query that calculates the total viewership for laptops and mobile devices where mobile is defined as the sum of tablet and phone viewership. Output the total viewership for laptops as laptop_reviews and the total viewership for mobile devices as mobile_views.
````
SELECT COUNT(CASE WHEN device_type = 'laptop' THEN 1 END) AS loptop_views,
COUNT(CASE WHEN device_type = 'phone' OR device_type ='tablet' THEN 1 END) AS mobile_views
FROM viewership
````
![Image](https://github.com/Aniruddhsinh04/SQL_Practice_Datalemur/blob/main/Images/Laptop_Vs_Mobile_Viewership/snap.png)
- Number of Tries: 4
- Lessons Learned:

## Data Science Skills | Easy | LinkedIn | 09/07/2024
- Question: Write a query to list the candidates who possess all of the required skills for the job. Sort the output by candidate ID in ascending order.
````
SELECT DISTINCT candidate_id 
FROM candidates
WHERE skill = 'Python'
OR skill = 'Tableau'
OR skill = 'PostgreSQL'
GROUP BY candidate_id
HAVING COUNT(skill) = 3
````
![Image](https://github.com/Aniruddhsinh04/SQL_Practice_Datalemur/blob/main/Images/Data_Science_Skills/snap.png)
- Number of Tries: 2
- Lessons Learned:

# Appendix

**Template**

## Title | Difficulty | Company | Date
- Question: 

![Image](Path)

- Number of Tries:
- Lessons Learned: 
