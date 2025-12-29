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

