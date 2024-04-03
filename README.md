# Scheduler v0.1
- This is a Java program which reads in a list of teams from a txt file and generates a schedule for them. The user can then simulate a season and track each team's schedule and win/loss record.
- This program is a prototype to be implemented in my upcoming Matchup League project.

# Reading in teams
- Currently, the program is hard coded to read in teams from the Florida.txt file in the resources folder.
- There should be one team per line.
- Most teams have a skill number associated with them, separated from the name by a colon.
  - If no skill number is given for a team, A random one between 1-100 will be given to it.
 
## Florida.txt
- To test the program, I made a league consisting of the ten largest population centers in Florida.
- The skill number for each team was determined by the population of the surrounding area and dividing by 10,000 (ie a population of 1 million = skill of 100)
  - An eleventh team, Space Coast, was added with no skill number to test random skill function.
- The map I used to determine each team's population can be found here: https://davesredistricting.org/maps#viewmap::d3f51294-8e9e-49bf-8a27-d466d35fbd68
- The map for the Minnesota.txt file can be found here: https://davesredistricting.org/maps#viewmap::f0b743fb-e7a4-43c3-a45d-d72008bf4255
- When assinging the skill number to the team, the program adds an offset to the number from the file, which is currently between -5 and 5. This is done to make each simulation unique.
    
# Generating the schedule
- The schedule is generated using a round robin format (Every team plays every other team exactly once).
  - A more detailed description can be found here: https://en.wikipedia.org/wiki/Round-robin_tournament  
- If there is an odd number of teams, a dummy "bye" team is added, and games involving the bye will not count as a win or a loss.

# Simulating the season
- At the start of each round, the program will give the user several options:
## 1. Next round
- This will simulate the next round of games.
- Games are simulated as such:
  - Team A's skill (a) is combined with Team B's skill (b).
  - A random number is generated from 1 to a+b.
  - If this number is less than or equal to a, Team A wins the game. If it's higher than a, Team B wins the game.
  - For example, if team A has skill of 50 and team B has skill of 100, a random number between 1-150 is generated. If the number is 1-50, A wins. If the number is 51-150, B wins.
## 2. Print standings
- Displays the list of teams and their number of wins and losses, in order of winning percentage (wins / (wins+losses)).
- At the end of the round, the updated standings are automatically displayed.
- The team with the highest winning percentage at the end of the season is declared the winner.
## 3. Print teams by skill
- Displays the list of teams and their skill number for the current simulation, ranked by skill number
## 4. Print a team's schedule
- After selecting this option, you will be prompted to choose a team to view.
- After choosing a team, their list of opponents will display, including the bye round if one exists.
- Games that have already been played will also show the result, a W for a win and an L for a loss.
