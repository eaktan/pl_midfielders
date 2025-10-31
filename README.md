Sabancı University DSA-210 Term Project: Premier League Midfielders

Project Overview:

Football and its tactics has been going through a major evolution over the last decade. How the game is played and what players are being asked to do on the football pitch has drastically changed. I believe where this can be seen the most is in the midfield, as it is the most versatile and, for many people, the most important role within the game. In this project, I will be analyzing game and player data over the last century and try to analyze how this shift in player game patterns can be recognized analytically and try to analytically show how the role of midfielder has evolved. Are they more creative, more attacking, more defending, or are they turning into all-round “do-it-all”  players? I will be analyzing the English Premier League, as it has been the biggest (monetarily and according to viewing numbers) league in the last ten years.

Data Sources:

- FB.ref
- Transfermarkt
- Kaggle EPL Data

Analysis Plan:

1) Data Collection
My primary data set will be collected from FB.ref. I will be collecting data concerning all players that have primarily played as a midfielder in any of the selected seasons. Some of the data points I will be collecting will be goals, assists, tackles, xG (expected goals), passing numbers (progressive, line breaking, into the final third), xA (expected assists), running distances. I will use other sources of data that I have mentioned, in the case that the data I get from FB.ref is incomplete.

2) Creating Advanced Metrics for Positional Archetypes
In football analysis, advanced metrics that are driven from simpler metrics are used in order to get a better statistical understanding of a player’s actions. Throughout the project, I will be creating my own advanced metrics from the data I collected, or will be using pre-determined advanced metrics with my own data. An example of an already used advanced metric is XOva (Expected Offensive Value Added), which mathematically uses the expected goals, expected assists and expected assist received metrics in order to isolate a player’s individual offensive impact. I will be creating various advanced metrics such as this one, so that I can “simplify” one of the aspects of being a midfielder into a statstical value, and use those for my analysis.

4) Statistical Analysis
I will use statistical tests (such as the T-test) to definitively prove if the mean (average) advanced metrics of midfielders have changed.
	
	Hypothesis Example: I will test if the xOVA of midfielders in the last ten seasons is statistically higher than the average in the first five seasons.

I will also be using different visualizations with my data. These may include:
- Time-Series Line Plots: Track the average P90 rate for key metrics (e.g., Progressive Passes, Tackles Won) across all 10 seasons - In order to show the overall direction of change over the decade.
- Positional Quadrant Plots: Scatter plot players on a 2-D graph (e.g., Defensive Index vs. Progressive Index) for 2015/16 and 2024/25. - In order to see if midfielder roles (archetypes) have clustered or shifted over time.
- Radar Charts: Compare the detailed statistical profile of an "old-school" midfielder versus a "modern" midfielder. - In order to highlight the change in the required skill set for the position.

4) Outcomes 
- Quantitative Proof of Evolution (or non-evolution) : Statistically prove (or not) whether the mean performance of English Premier League midfielders in different aspects of the game has changed significantly across different seasons.
- Defined Midfield Archetypes: Define and clearly label 2-4 distinct statistical archetypes of midfielders (e.g., "High-Volume Passer," "Modern Box-to-Box," "Deep Playmaker") based on the advanced metrics we create.
- Time-Series Metric Analysis: Generate Time-Series Line Plots that track the average rates of our advanced metrics across 10 seasons, visually confirming the direction and speed of positional change (if there are any).
- Positional Role Shift Visualization: Produce Positional Quadrant Plots that clearly illustrate the shift in the entire population of midfielders between the beginning and end of the decade (if there is any), showing whether players are becoming more "all-round" or more specialized.
- Iconic Player Profile Comparison: Create Radar Charts comparing the statistical profiles of at least two iconic midfielders from different eras, showcasing the specific differences in the skill demands of the role.




