Sabancı University DSA-210 Term Project: Premier League Midfielders

Project Overview:
------------------
Football and its tactics has been going through a major evolution over the last decade. How the game is played and what players are being asked to do on the football pitch has drastically changed. I believe where this can be seen the most is in the midfield, as it is the most versatile and, for many people, the most important role within the game. In this project, I will be analyzing game and player data over the last eight years and try to analyze how this shift in player game patterns can be recognized analytically and try to analytically show how the role of midfielder has evolved. Are they more creative, more attacking, more defending, or are they turning into all-round “do-it-all”  players? I will be analyzing the English Premier League, as it has been the biggest (monetarily and according to viewing numbers) league in the last ten years.

Motivation:
-----------------
As an avid football watcher, I have spent years seemingly observing the tactical shifts that define the modern game. From the stands or the screen, it is clear that the game has undergone a massive evolution over the last decade. I have always been particularly fascinated by the midfield—the "engine room" of the pitch. To me, it is the most versatile and vital role, often serving as the bridge between a team's defensive structure and its offensive ambition. I want to see if I can turn this evolution that I observed with the "eye-test" into an analytical understanding.

Objectives:
----------------
- Quantitative Proof of Evolution (or non-evolution) : Statistically prove (or not) whether the mean performance of English Premier League midfielders in different aspects of the game has changed significantly across different seasons.
- Defined Midfield Archetypes: Define and clearly label 2-4 distinct statistical archetypes of midfielders (e.g., "High-Volume Passer," "Modern Box-to-Box," "Deep Playmaker") based on the advanced metrics we create.
- Time-Series Metric Analysis: Generate Time-Series Line Plots that track the average rates of our advanced metrics across the seasons, visually confirming the direction and speed of positional change (if there are any).
- Positional Role Shift Visualization: Produce Positional Quadrant Plots that clearly illustrate the shift in the entire population of midfielders between the beginning and end of the decade (if there is any), showing whether players are becoming more "all-round" or more specialized.
- Iconic Player Profile Comparison: Create Radar Charts comparing the statistical profiles of at least two iconic midfielders from different eras, showcasing the specific differences in the skill demands of the role.


Data Sources:
-------------------
- FB.ref
- Transfermarkt
- Kaggle EPL Data

Analysis Plan:
--------------------
1) Data Collection
My primary data set will be collected from FB.ref. I will be collecting data concerning all players that have primarily played as a midfielder in any of the selected seasons. Some of the data points I will be collecting will be goals, assists, tackles, xG (expected goals), passing numbers (progressive, line breaking, into the final third), xA (expected assists), running distances. I will use other sources of data that I have mentioned, in the case that the data I get from FB.ref is incomplete.

2) Creating Advanced Metrics for Positional Archetypes
In football analysis, advanced metrics that are driven from simpler metrics are used in order to get a better statistical understanding of a player’s actions. Throughout the project, I will be creating my own advanced metrics from the data I collected, or will be using pre-determined advanced metrics with my own data. An example of an already used advanced metric is XOva (Expected Offensive Value Added), which mathematically uses the expected goals, expected assists and expected assist received metrics in order to isolate a player’s individual offensive impact. I will be creating various advanced metrics such as this one, so that I can “simplify” one of the aspects of being a midfielder into a statstical value, and use those for my analysis.

3) Statistical Analysis
I will use statistical tests (such as the T-test) to definitively prove if the mean (average) advanced metrics of midfielders have changed.
	
	Hypothesis Example: I will test if the xOVA of midfielders in the last ten seasons is statistically higher than the average in the first five seasons.

I will also be using different visualizations with my data. These may include:
- Time-Series Line Plots: Track the average P90 rate for key metrics (e.g., Progressive Passes, Tackles Won) across all 10 seasons - In order to show the overall direction of change over the decade.
- Positional Quadrant Plots: Scatter plot players on a 2-D graph (e.g., Defensive Index vs. Progressive Index) for 2015/16 and 2024/25. - In order to see if midfielder roles (archetypes) have clustered or shifted over time.
- Radar Charts: Compare the detailed statistical profile of an "old-school" midfielder versus a "modern" midfielder. - In order to highlight the change in the required skill set for the position.


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

Key Findings and Statistical Analysis
----------------------------------------
2.1 Overall Trend Visualization:

The following graph illustrates the average Index scores for all core midfielders (>= 1000 mins) from 2017 to 2025.

<img width="1189" height="590" alt="download" src="https://github.com/user-attachments/assets/d8066b61-0941-47e0-bde6-bf8a4353d387" />

The most prominent feature of the graph is the divergence between Offense and Progression. While midfielders are being pushed further forward to contribute to the attack, their traditional role as the primary "ball-progressors" from deep areas is being offloaded to other positions (like inverted fullbacks).

2.2 Longitudinal Study: Start (2017) vs. End (2025):


Metric            | Start Mean   | End Mean     | % Change   | P-Value
Offense_Index     | 21.70        | 23.52        | +8.4     % | 0.2350
Defense_Index     | 32.55        | 30.77        | -5.5     % | 0.2751
Progression_Index | 31.10        | 26.44        | -15.0    % | 0.0136

The Progression Breakthrough: With a p-value of 0.0136, we have statistically significant evidence that the progression role of central midfielders has diminished. A 15% drop in a core KPI over 8 years indicates a fundamental change in the league's "tactical assembly line."

Gradual Offense/Defense Shift: While Offense rose by 8% and Defense fell by 5%, their p-values (> 0.05) suggest these changes are more varied across the league. This indicates that while some teams have moved toward "attacking 8s," others still maintain traditional defensive anchors, keeping the variance high.

2.3 Sequential Change (Year-on-Year):

To see if there was a "sudden shock" to the system (like the COVID-19 break or a major rule change), we analyzed consecutive seasons.

Comparison                | Offense P  | Defense P  | Prog P    
2017-2018 vs 2018-2019  | 0.9726     | 0.6888     | 0.4517    
2018-2019 vs 2019-2020  | 0.6660     | 0.3074     | 0.3298    
2019-2020 vs 2020-2021  | 0.3062     | 0.2977     | 0.2307    
2020-2021 vs 2021-2022  | 0.1026     | 0.9696     | 0.2413    
2021-2022 vs 2022-2023  | 0.2712     | 0.8701     | 0.9529    
2022-2023 vs 2023-2024  | 0.2898     | 0.3348     | 0.5304    
2023-2024 vs 2024-2025  | 0.3993     | 0.5241     | 0.2882

The high p-values for consecutive seasons prove that football evolution is a "Continuous Improvement" process (Kaizen). There is no single year where the game changed overnight; instead, small tactical adjustments each season have compounded into the significant 15% drop in progression we see today.
