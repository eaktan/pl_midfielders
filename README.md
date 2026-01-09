Sabancı University DSA-210 Term Project: Premier League Midfielders

Project Overview:
------------------
Football and its tactics have undergone a major evolution over the last decade. Both the way the game is played and the demands placed on players on the pitch have drastically changed. I believe this shift is most visible in the midfield, as it is the most versatile and—for many—the most important role in the game. In this project, I will examine game and player data from the last eight years to identify how these changing patterns can be recognized and to demonstrate analytically how the role of the midfielder has evolved. Are they becoming more creative, more defensive, or are they turning into all-round, “do-it-all” players? I will focus my analysis on the English Premier League, as it has been the world’s largest league (both financially and by viewership) over the last decade.

Motivation:
-----------------
As an avid football follower, I have spent years observing the tactical shifts that define the modern game. From the stands or the screen, it is clear that the sport has undergone a massive evolution over the last decade. I have always been particularly fascinated by the midfield—the "engine room" of the pitch. To me, it is the most versatile and vital role, often serving as the bridge between a team's defensive structure and its offensive ambition. In this project, I aim to translate the evolution I have observed through the "eye-test" into a rigorous analytical understanding.

Objectives:
----------------
Quantitative Proof of Evolution (or Consistency): Statistically determine whether the mean performance metrics of English Premier League midfielders have changed significantly across different seasons.

Defined Midfield Archetypes: Define and label 2–4 distinct statistical archetypes (e.g., "High-Volume Passer," "Modern Box-to-Box," "Deep-Lying Playmaker") based on the advanced metrics developed in this study.

Time-Series Metric Analysis: Generate time-series line plots to track the average rates of advanced metrics across seasons, visually confirming the direction and velocity of positional change.

Positional Role Shift Visualization: Produce positional quadrant plots to illustrate the shift in the midfielder population between the beginning and end of the decade, identifying whether players are becoming more "all-round" or more specialized.

Iconic Player Profile Comparison: Create radar charts comparing the statistical profiles of at least two iconic midfielders from different eras, showcasing the specific differences in the skill demands of the role.


Data Sources:
-------------------
- FB.ref

Analysis Plan:
--------------------
1) Data Collection:
My primary dataset will be sourced from FBref, covering all players who primarily operated as midfielders during the selected seasons. The data points will include goals, assists, tackles, xG (Expected Goals), passing statistics (progressive passes, line-breaking passes, passes into the final third), xA (Expected Assists), and running distances. I will supplement this with secondary sources if the FBref data is incomplete for specific seasons.

2) Creating Advanced Metrics for Positional Archetypes:
In football analytics, advanced metrics derived from basic stats are essential for a nuanced understanding of player performance. Throughout this project, I will develop custom advanced metrics or apply established formulas to my dataset. An example of such a metric is xOVA (Expected Offensive Value Added), which mathematically combines expected goals and expected assists to quantify a player’s individual offensive impact. By "simplifying" complex phases of play into these statistical values, I can better categorize and analyze midfielder behavior.

3) Statistical Analysis:
I will employ statistical tests—specifically the T-test or ANOVA—to determine if the mean values of these advanced metrics have shifted significantly over time.

Hypothesis Example: I will test whether the average xOVA of midfielders in the most recent five seasons is statistically higher than the average from the first five seasons of the decade.

I will also utilize the following visualizations:

Time-Series Line Plots: To track the average Per 90 (P90) rates for key metrics (e.g., Progressive Passes, Tackles Won) across the decade, illustrating the overall trajectory of the position.

Positional Quadrant Plots: To scatter plot players on a 2-D graph (e.g., Defensive Index vs. Progressive Index) comparing the 2015/16 and 2024/25 seasons. This will reveal if midfielder archetypes have clustered or shifted over time.

Radar Charts: To compare the multi-dimensional statistical profiles of "old-school" vs. "modern" midfielders, highlighting the evolution of the required skill set.

Analysis:
------------------------
1.1 Statistical Filtering:

I first, had to eliminate players that had minimal playing time througout to seasons in order to prevent "statistical noise" that may be created by late-game substitutes or youth players. In order to achieve this, a strict filter was applied. CIES Football Observatory, the biggest football analysis institution in the world, uses 1000 as its minimum limit for played minutes when including players into their statistical analysis. I also picked 1000 minutes for my minimum limits. This reduced the dataset to approximately 130 "Core Midfielders" per season, representing the true tactical backbone of the league.

1.2 Advanced Indices:

Three composite indices were created to quantify distinct aspects of midfield play. To combine metrics with different units (e.g., yards vs. counts), Min-Max Scaling was applied across the entire 8-year pool. This created a consistent 0–100 benchmark:

- Offense Index: A composite of non-penalty Expected Goals (npxG), Expected Assisted Goals (xAG), Key Passes (KP), and Passes into the Penalty Area (PPA).

- Defense Index: A composite of Tackles + Interceptions (Tkl+Int), Blocks, and Clearances (Clr).

- Progression (Creativity) Index: A composite of Progressive Passing Distance (PrgDist), Passes into the Final Third (1/3), and Progressive Passes (PrgP).

1.3 Hypothesis Testing:

To validate if the observed tactical shifts were statistically significant or merely random fluctuations, Independent Samples T-Tests were used to compare the 2017 and 2025 eras. Additionally, One-Way ANOVA was performed across all eight seasons to detect overall "process drift" in the league's midfield profile.

1.4 Machine Leaarning Methods:

For the predictive backbone of this study, I utilized a k-Nearest Neighbors (k-NN) machine learning algorithm, specifically focused on Similarity Search through Euclidean Distance mapping. Unlike traditional supervised learning that requires pre-defined labels, I implemented this Instance-Based Learning approach to identify functional redundancies within a 3-dimensional feature space (Offense, Defense, and Progression).In terms of accuracy, since this is an unsupervised similarity task, I measured the model's performance through Functional Fidelity rather than a traditional percentage-based accuracy score. The accuracy is "self-validated" by the Similarity Distance (d) metric: a distance near 0.0 represents a perfect functional clone, while distances between 1.0 and 2.0 indicate high-confidence "interchangeable components." The model proved remarkably accurate in identifying "face validity" within the Premier League ecosystem. For example, I found that the algorithm correctly identified Kevin De Bruyne as a "Custom Asset" with low interchangeability (as his nearest neighbors were his own past seasons), whereas Jorginho and Thiago were identified as "Standardized Parts" due to their extremely low similarity distance (approx 1.1). By using MinMaxScaler to standardize all inputs to a 0–100 scale before the k-NN search, I ensured that the model's accuracy was not skewed by different units of measurement, providing a mathematically robust framework for squad optimization and talent replacement.

Key Findings
----------------------------------------
2.1 Overall Trend Visualization:

The following graph illustrates the average Index scores for all core midfielders (>= 1000 mins) from 2017 to 2025.

<img width="1189" height="590" alt="download" src="https://github.com/user-attachments/assets/d8066b61-0941-47e0-bde6-bf8a4353d387" />

The most prominent feature of the graph is the divergence between Offense and Progression. While midfielders are being pushed further forward to contribute to the attack, their traditional role as the primary "ball-progressors" from deep areas is being offloaded to other positions (like inverted fullbacks).

2.2 Longitudinal Study: Start (2017) vs. End (2025):


|Metric            | Start Mean   | End Mean     | % Change   | P-Value|
|-----------------|--------------|--------------|------------|--------|
|Offense_Index     | 21.70        | 23.52        | +8.4     % | 0.2350|
|Defense_Index     | 32.55        | 30.77        | -5.5     % | 0.2751|
|Progression_Index | 31.10        | 26.44        | -15.0    % | 0.0136|

The Progression Breakthrough: With a p-value of 0.0136, we have statistically significant evidence that the progression role of central midfielders has diminished. A 15% drop in a core KPI over 8 years indicates a fundamental change in the league's "tactical assembly line."

Gradual Offense/Defense Shift: While Offense rose by 8% and Defense fell by 5%, their p-values (> 0.05) suggest these changes are more varied across the league. This indicates that while some teams have moved toward "attacking 8s," others still maintain traditional defensive anchors, keeping the variance high.

2.3 Sequential Change (Year-on-Year):

To see if there was a "sudden shock" to the system (like the COVID-19 break or a major rule change), we analyzed consecutive seasons.

|Comparison                | Offense P  | Defense P  | Prog P| 
|------------------------|-------------|-------------|-------|
|2017-2018 vs 2018-2019  | 0.9726     | 0.6888     | 0.4517 |   
|2018-2019 vs 2019-2020  | 0.6660     | 0.3074     | 0.3298  |  
|2019-2020 vs 2020-2021  | 0.3062     | 0.2977     | 0.2307  |  
|2020-2021 vs 2021-2022  | 0.1026     | 0.9696     | 0.2413  |  
|2021-2022 vs 2022-2023  | 0.2712     | 0.8701     | 0.9529  |  
|2022-2023 vs 2023-2024  | 0.2898     | 0.3348     | 0.5304  |  
|2023-2024 vs 2024-2025  | 0.3993     | 0.5241     | 0.2882|

The high p-values for consecutive seasons prove that football evolution is a "Continuous Improvement" process (Kaizen). There is no single year where the game changed overnight; instead, small tactical adjustments each season have compounded into the significant 15% drop in progression we see today.

Midfielder Archetype Classification & Statistical Methodology
-------------------------------------------------------------

3.1 Introduction to Functional Archetypes:
Traditional football analysis often categorizes players by their starting positions (e.g., "Central Midfielder"). However, from a systems-engineering perspective, a position does not necessarily define a function. To capture the true tactical evolution of the Premier League, this study developed a Functional Archetype Model. By grouping players based on their statistical output across three dimensions, we can identify how the "job description" of the midfielder has changed over time.

3.2 Categorization Methodology (Percentile-Based Scoring):
To ensure the archetypes were robust and relative to the elite standards of the league, a Percentile-Based Classification was utilized. Rather than using arbitrary thresholds, each player's index score was ranked against the entire population of core midfielders (1000+ minutes) from 2017 to 2025.

I defined four primary archetypes based on high-performance "bottlenecks" (Top 30% performance) and one baseline category:

- Creative Engine: Elite offensive threat and ball progression (Top 30% in both).

- Deep-Lying Progressor: Elite defensive coverage and ball progression (Top 30% in both).

- Midfield Anchor: Pure defensive specialization (Top 30% in Defense, Bottom 40% in Offense).

- Modern Box-to-Box: Functional versatility (Balanced output; Top 60% across all three metrics).

- System Rotational: The tactical baseline; players who provide reliable output without extreme specialization in one area.

3.3 Quantitative Analysis:
By applying these labels to 1,049 player-seasons, I generated an "Inventory Count" of archetypes for each year. This allowed us to track the Supply and Demand of specific skill sets in the league.

<img width="1388" height="790" alt="download (1)" src="https://github.com/user-attachments/assets/72747029-b30b-491a-aac2-e3686237fdf3" />

The most significant structural shift is the 47.3% decline in Deep-Lying Progressors (dropping from 19 to 10 players), which suggests a deliberate decentralization of the ball-progression process away from the midfield engine room. Conversely, the 20% growth in the Modern Box-to-Box archetype—peaking at 21 players in the 2023-2024 season—highlights a systemic move toward functional versatility and multi-purpose operational units. Interestingly, the Midfield Anchor remains a "Fixed Constraint" within the league, maintaining a nearly constant count (25 vs. 24), which proves that regardless of offensive evolution, the system requires a consistent "Safety Stock" of defensive specialists to maintain equilibrium.

3.4 Statistical Validation of Archetype Shifts:
To verify if the observed changes in the league's tactical composition were statistically significant, a Chi-Square Test of Independence was performed by comparing the archetype distributions of the baseline (2017-2018) and the most recent era (2024-2025). This analysis evaluates whether the "Product Mix" of the Premier League has truly shifted or if the fluctuations are within the bounds of expected variance.

The p-values for individual archetypes reveal a high degree of "Tactical Resilience" within certain roles while highlighting areas of rapid evolution. The Midfield Anchor archetype returned a P-value of 1.000, confirming it as a permanent system constraint that remains virtually untouched by modern tactical trends. In contrast, the Deep-Lying Progressor showed the most aggressive shift with a 47.3% decline and a P-value of 0.1725. While this does not meet the strict 0.05 threshold for total statistical significance, the magnitude of the net change (-9 players) indicates a strong operational trend toward decentralizing the ball-progression process. Furthermore, the Modern Box-to-Box and Creative Engine archetypes returned p-values of 0.6884 and 0.6722, respectively, suggesting that while their roles have evolved in quality (as shown in our earlier index tests), the quantity of these specialists in the league remains relatively stable. Overall, the statistical data supports a narrative of gradual systemic re-engineering rather than a sudden, disruptive transformation.

3.5 Exemplary Role Models by Archetype:
To validate the statistical model and provide qualitative context to the identified archetypes, we extracted the top-performing player for each category across the eight-season study. This peer-group analysis ensures that the mathematical indexing aligns with the "eye test" of football scouting and tactical reality.

Season | Creative Engine | Deep-Lying Progressor | Midfield Anchor | Modern Box-to-Box| 
--------|----------------| ----------------------| ----------------| -----------------|  
2017-18	| Cesc Fàbregas (CHE)| 	Fernandinho (MCI)	| Wilfred Ndidi (LEI)	| Granit Xhaka (ARS)| 
2018-19	| David Silva (MCI)	| Romain Saïss (WOL)|	Ricardo Pereira (LEI)|	Felipe Anderson (WHU)| 
2019-20	| Kevin De Bruyne (MCI)| Jorginho (CHE)| 	Philip Billing (BOU)	| Dani Ceballos (ARS)| 
2020-21	| Kevin De Bruyne (MCI)| Rúben Neves (WOL)| 	Ethan Ampadu (SHU)| 	Thiago Alcántara (LIV)| 
2021-22	| Thiago Alcántara (LIV)| Pierre Højbjerg (TOT)| 	Wilfred Ndidi (LEI)| 	Bruno Guimarães (NEW)| 
2022-23	| Kevin De Bruyne (MCI)	| Enzo Fernández (CHE)| 	Wilfred Ndidi (LEI)	| Rodri (MCI)| 
2023-24	| Kevin De Bruyne (MCI)	| Pierre Højbjerg (TOT)	| Edson Álvarez (WHU)	| Declan Rice (ARS)| 
2024-25	| Bruno Fernandes (MUN)	| Casemiro (MUN)| 	Kalvin Phillips (IPS)| 	Youri Tielemans (AVL)| 

The consistency of certain names—most notably Kevin De Bruyne and Wilfred Ndidi—serves as a benchmark for the model's reliability. De Bruyne's multi-year dominance in the Creative Engine category highlights the "Elite Standard" of the modern playmaker.

The evolution within the Modern Box-to-Box category is particularly telling for this project. The shift from Granit Xhaka (2017) to Declan Rice and Rodri (2023-24) illustrates a systemic change in player profiles: the modern all-rounder is now expected to provide elite ball control and physical defensive coverage simultaneously. Furthermore, the presence of Casemiro and Fernandinho as Deep-Lying Progressors confirms that this role, while declining in volume, remains the domain of highly experienced technical leaders who anchor complex systems.

3.6 Iconic Player Profile Comparison Xhaka (2017) vs. Tielemans (2024):
To ground the statistical trends in real-world application, a comparative analysis was performed on two prominent midfielders representing the "Modern Box-to-Box" archetype from the start and end of the study period.

<img width="1059" height="875" alt="download (2)" src="https://github.com/user-attachments/assets/6618474b-ccfd-4718-b751-14daac779e8b" />

- The Transition from Volume to Value:
Granit Xhaka’s 2017-18 profile shows a heavy skew toward the right side of the chart, particularly in Progressive Passes and Passes into the Final Third. This indicates a role focused on "Process Volume"—acting as a high-frequency distributor from deep areas. In contrast, Youri Tielemans (2024-25) shows higher peaks in Key Passes and xAG (Expected Assisted Goals), suggesting a shift toward "Output Efficiency"—producing high-threat chances with fewer, more decisive touches.
- Defensive Baseline Consistency:
Despite the seven-year gap and the change in team styles, both players exhibit nearly identical scores in Tackles and Interceptions. This supports our finding that the "Defensive Input" is a fixed system requirement for the Premier League midfielder; while offensive duties evolve, the defensive workload remains a non-negotiable KPI.
- Decentralization of Build-up:
The significant reduction in progression metrics for the modern profile (Tielemans) compared to the 2017 profile (Xhaka) is the visual manifestation of our $P=0.0136$ significance finding. It confirms that the task of "moving the ball forward" has been partially offloaded to other units in the team's tactical assembly line (e.g., center-backs or inverted fullbacks), allowing the modern midfielder to focus on final-third creation.

ML Methods: Analysis of Functional Replacements
------------------------------------------------
In this part of the project, I tested the "interchangeability" of players within the Premier League system. By treating players as functional components with specific output specifications (Offense, Defense, and Progression), I attempted to find the closest statistical matches for three iconic profiles to see how easily they could be replaced.

4.1 Case Study: The Uniqueness of Kevin De Bruyne (2019-20):
I attempted to find a functional replacement for Kevin De Bruyne's record-breaking 2019-20 season.

The Result: The analysis showed that De Bruyne is a very unique player. The four closest matches to his prime season were actually himself in different years.

|               Player |    Season |           Squad | Similarity_Distance|
-----------------------|-----------|-----------------|--------------------|
|Kevin De Bruyne | 2019-2020 | Manchester City |            0.000000|
|   Kevin De Bruyne | 2022-2023 | Manchester City |            2.318224|
|  Kevin De Bruyne | 2023-2024 | Manchester City  |           2.969730|
|   Kevin De Bruyne | 2021-2022 | Manchester City  |           3.652083|
|   Bruno Fernandes | 2022-2023 |  Manchester Utd |            3.718293|
|  Kevin De Bruyne | 2024-2025 | Manchester City |            3.843203|

4.2 Case Study: The Standardized Deep-Lying Playmaker (Jorginho):
I looked for replacements for Jorginho's deep-lying playmaker profile to see if this role is unique to Chelsea’s system.

The Result: I found extremely high interchangeability. Players like Fernandinho (Man City) and Thiago Alcántara (Liverpool) appeared as near-perfect functional matches with very low similarity distances (~1.25).

|                Player  |   Season |           Squad  |      Similarity_Distance|
|-------------------------|---------|-------------------|-------------------|
|           Jorginho | 2019-2020  |        Chelsea       |      0.000000|
|           Jorginho | 2018-2019   |       Chelsea      |       1.152347|
|      Fernandinho  |2020-2021 | Manchester City     |        1.166858|
|  Thiago Alcántara  |2022-2023  |      Liverpool    |         1.256445|
|  Thiago Alcántara  |2020-2021   |     Liverpool   |          1.481910|
|     Thomas Partey | 2020-2021    |      Arsenal  |           1.598804|

5.3 Case Study: The Evolution of the Modern Box-to-Box (Declan Rice)
Finally, I searched for replacements for Declan Rice’s 2023-24 season at Arsenal to see which past profiles he resembles.

The Result: The analysis uncovered "hidden" similarities. While Rice is often praised for his unique modern style, the data identified Paul Pogba (2020-21) as a near-identical functional match (Distance: 1.17).


|                Player |    Season     |      Squad  |Similarity_Distance|
|-----------------------|--------------|------------|---------|
|Declan Rice|2023-2024|Arsenal|0.000000|
|Aaron Mooy|2017-2018|Huddersfield|1.161134|
|Paul Pogba|2020-2021|Manchester Utd|1.171569|
|Jordan Henderson|2019-2020|Liverpool |1.226344|
|Youri Tielemans|2024-2025|Aston Villa |1.292387|
|Youri Tielemans|2022-2023|Leicester City |1.344559|
