---
title: SQL - Analyzing Standard de Liège's Performance
publishDate: 2019-10-02 00:00:00
img: /assets/Football.png
img_alt: IMBd
description: "Analyzing Standard de Liège's Performance."
tags:
 - SQL
---

### Introduction
This SQL project aims to analyze the performance of the football team Standard de Liège during the 2014/2015 season. The primary goal is to determine the number of victories for Standard de Liège based on the matches played, whether at home or away. To achieve this, I used an SQL query combining several tables, including those for matches and teams, along with a window function to rank the matches based on the goal difference.
<img
    alt="Hugo Bouchez"
    width="1500"
    height="1500"
    src="/assets/Team table.png"
/>

<img
    alt="Hugo Bouchez"
    width="1500"
    height="1500"
    src="/assets/Match table.png"
/>

### Explanation of the Code
In this query, I used two CTEs (Common Table Expressions) to distinguish the results for Standard de Liège depending on whether they played at home or away. Here is a breakdown of the process:

#### CTE Home (home games)
This part of the query checks if the home team (identified by the `team` table and linked by the `hometeam_id` key in the `match` table) is Standard de Liège. Based on the goals scored, an outcome is assigned: either "Standart Win" (victory for Standard), "Standart Loss" (defeat), or "Tie" (draw).

#### CTE Away (away games)
Similarly, this part analyzes the results of matches where Standard de Liège played away. The process is the same, with reversed conditions since this time Standard is the visiting team.

#### Window Function
The window function `RANK()` is used to rank matches based on the goal difference (absolute difference between home and away goals). This allows matches to be compared in a neutral way, regardless of whether Standard played at home or away. Thus, we can quickly identify the matches with the most significant goal differences, and therefore, the most important victories.

#### Final Selection
The final query selects matches from the 2014/2015 season where Standard de Liège won, whether at home or away. This selection is made using the results from the CTEs to verify if the team won.

<img
    alt="Hugo Bouchez"
    width="1500"
    height="1500"
    src="/assets/code.png"
/>

<img
    alt="Hugo Bouchez"
    width="1500"
    height="1500"
    src="/assets/Query result.png"
/>


### Analysis and Justification of the Approach
The chosen approach is based on a detailed analysis of the data available in the `match` and `team` tables, allowing a fine-grained exploration of the team's performance. Using CTEs makes the code more readable and structured by clearly separating cases where Standard played at home from those where they played away.

The decision to use a window function to rank the matches is justified because it offers a simple and effective comparative view of performance without manually reworking the data. In particular, the goal difference is a key indicator to assess a team's performance, and the use of the `RANK()` function makes this comparison immediate.

Lastly, filtering by the 2014/2015 season helps to focus the analysis on a well-defined period, which is important for the clarity and relevance of the results.

### Conclusion
This SQL project demonstrates the usefulness of CTEs and window functions for conducting complex analyses on sports data. The structured approach adopted makes it easy to identify the victories of Standard de Liège, whether at home or away, by ranking the matches according to the goal difference. This not only provides a clear view of the team's results but also allows an evaluation of the impact of victories within the context of the 2014/2015 season.

This type of analysis can be adapted to other teams or seasons by simply adjusting the filtering parameters, showcasing the flexibility and power of this SQL approach.
