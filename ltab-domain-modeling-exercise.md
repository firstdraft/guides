# LTAB Domain Modeling Exercise

Imagine we've been hired to build an app for a youth poetry slam festival. Over a thousand poets from over a hundred schools will compete over a month of spoken-word bouts. The staff currently manage scorekeeping using paper and spreadsheets, but it would be nice if we could build an app that streamlines the process and makes it easier for the coaches from the schools to see what's going on in real-time.

## Stories

### Team sign-up

 - A **coach** (first name, last name, email) signs up for an account and registers a **school** (name, address).
 - The coach adds all of their **poets** (first name, last name) to their school.

### Tournament set-up

 - A staff member creates a **tournament**, e.g. LTAB 2019.
 - A staff member sets up all of the **levels** for the tournament, e.g. Prelims, Quarterfinals, Semifinals, Finals.
 - For the first level, a staff member sets up enough **bouts** so that each school can compete in 2 bouts (with 4 schools in each bout). E.g. Bout 1, Bout 2, ..., Bout 70.
 - For each bout, a staff member assigns 4 schools.

### Day of the bout

#### Before the performances

 - A staff member has the team captains draw from a hat and assigns a **draw order** to each team — A, B, C, or D.
 
#### Structure of the bout

 - There are five **rounds** of poems in each bout:
 - The first four rounds are **solo** rounds. Each team sends up one poet to perform alone.
    - The order of performances is determined by the draw order of the teams; the first round is ABCD, second round is BCDA, CDAB, DABC.
 - The final round is the **group piece** round. Each team sends up 4 poets to perform together.
    - The order of performances is determined by the outcome of the first four rounds — the lowest scoring team goes first, the highest scoring team goes last.

#### Scoring

 - Each poem is scored by five judges.
    - Judges will assign a numerical score between 0.0 and 10.0.
    - The lowest and highest scores will be dropped, and the other three scores will be summed to find the total score for the poem.
 - There are potential **deductions** that can be made by a staff member to a poem's score:
    - **Time**: If the poem goes over 3 minutes and 10 seconds, 0.5 points is deducted for every additional 10 seconds. For example,
        - 3:10 and under: no penalty
        - 3:11—3:20: `-0.5`
        - 3:21—3:30: `-1.0`
        - 3:31—3:40: `-1.5`
        - etc
    - There may be other deductions made at the staff member's discretion. Examples:
        - Using a prop: `-0.5`
        - Profanity: `-0.5`
        - Plagiarism: `-30.0` (final scores can never go under `0.0`, however).
 - Ultimately, each team's final score from each of the five rounds is added up to get the team's overall score.
 - The team's **bout rank** is determined by their overall score; if two teams have the same overall score, then they get the same bout rank (and the next team has a bout rank that is two greater than theirs). Example:
    - Team A: overall score `135.2`, bout rank `1`
    - Team B: overall score `134.7`, bout rank `2`
    - Team C: overall score `134.7`, bout rank `2`
    - Team D: overall score `130.9`, bout rank `4`

### After all bouts

 - Once all bouts are complete, overall team rankings (and who proceeds to the next level) will be determined by:
    1. Sum of a team's bout ranks across both bouts. Lower is better.
    2. Sum of a team's overall scores across both bouts. Higher is better.
    3. Sum of a team's raw scores (scores including the highest/lowest that were dropped) across both bouts. Higher is better.

### Domain Modeling

 - What information does the app need to keep track of? What are your tables? What are your columns?
 - What things need to be captured in the database, and what things will be handled by the application/view logic?
