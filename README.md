# Topic

# 1. ELO in CTA

Expected result of the match for player $E_A$ where $R_A$ = Rating of Player A, and $R_B$ = Rating of Player B.
$$E_A= \frac{1}{1+10^{\frac{R_B-R_A}{400}}}$$

Same for Expected result of Player B $E_B$.
$$E_B= \frac{1}{1+10^{\frac{R_A-R_B}{400}}}$$

to calculate the new rating of player A, $R\'_A$

$$R\'_A = R_A + K * (S_A - E_A)$$

$S_A$ is the score of the game, 1 = win , 0 = loss
$K$ (K-Factor) scales, as per Quentins post[^3], for ratings below 1750 $K = 40$ 

CTA uses a scalling K-Factor.
| Rating        | K-Factor      | 
| ---------- |:----------:|
|< 1750 | 40 |
|1751 - 2250 |  30|
|2251 - 2550|  20|
|2550 < |  10|




# CTA ranking system

## Skill, Progression or Hybrid?
In chess ELO (or chess.com rating) rule all, everything is based on your rating, and that is what people chase. This is also what we have been experimenting with in CTA since the OpenBeta. This is what I would consider a pure "Skill" system, the alternative is a "progression system" like we know from RPGs etc you level up, you can have setbacks but generally you are progressing, and finally we got the hybrid solution which can combine the two systems, e.g. for new players its a progression system but for the top players its a pure skill system. Most online card games have either a progression system or a hybrid system. In the next Section I explain how some of the most popular online TCG/CCGs have implemented their system, but for now lets dive into my proposal for CTA.

## Tierd ranking system
The purpose of a tierd system is to make sure people get to play with other players that are similar in strength because feeling like you can win is very important to make sure people come back and play again, anyone that regularly get dominiated by stronger players is probably going to quite playing soon. It is also important to have an area where the skilled competitive players can face others like them, where there is real competition. This proposal is based on existing games and their systems (see below), I have just tweaked it to what I think is a CTA context.

I propose the following system for CTA:

There are 5 tiers (naming of course can be anything)
* Neophyte  - New player area
* Apprentice - Players with Experience
* Disciple - Players with Experience
* Primus - Players with Experience
* Legendary - Leader board

The first four tiers consist of 3 levels each, Level 3 is the lowest level in a tier, Level 1 highest, it goes Neophyte 1 -> Apprentice 3. 

Each level is made up of 100 RP (Ranking points). When you win a game you earn a certain amount of RPs based on the tier you are in, when you loose a game you will loose a certain amount of RPs, with 3 levels per tier the player need to accumulate a total of 300 RP to get promoted to the next tier. It is not possible to get Demoted from a tier, though players can move from Level 1 to Level 2.

All of the following numbers are sugestions and can of course bet tweaked as needed.
|Tier | Win RPs | Loss RPs|
|-----|---------|---------|
|Neophyte| 20 | 0 |
|Apprentice| 20 | 5 |
|Disciple| 20 | 10 |
|Primus| 20 | 20 |

### Neophyte 
Neophyte is the new player area, this is where everyone starts when they are new to the game, its important that people "graduate" out of this area as soon as they are comfortable with the game. This area should contain bots, which can be used when human opponent can't be found within 20-30 seconds.

To make players feel progress, in the Neophyte tier it is not possible to loose RPs, they can only be gained, each win rewards you 20 points, this means in 15 wins you will be promoted into the "Real" ranked area no matter how many losses.

### Apprentice
20 RPs for wins and -5 RPs for loss, this is very generous, for every win you can loose 4 times without really loosing your progress. 

### Disciple
20 RPs for wins and -10 RPs for loss, for every win you can loose twice, competition will get more fierce here but players will still feel they are making progress and climbing. 

### Primus
To progress in primus requires a larger than 50% win rate, this is where it gets challanging.

### Legendary
In legendary you no longer use RPs, but start using raw ELO (or which ever type of ranking system is used) to represent a users standing. Leaderboard shows the ELO raiting (as current leader board). if ELO is used, everyone starts with 1200, use sliding K factor (1000-1500 = 30, 1501-1750 = 25, 1751 - 2000 = 22, 2001-2250 = 20, 2251 - 2500 = 18, 2500+ = 15). Not possible to go below 1000 ELO.


### Match Making
Match making finds a pool of possible opponent, the pool of opponents is expanded in the following order, each expansions happens every 20-30 seconds, always avoid matching with last 3 opponents:
1. Same tier and same Level
3. Same tier and if not Neophyte tier, Level 1 add level 3 from higher tier, if Level 3 add level 1 from lower tier 
4. If Neophyte pair with bot.
5. previous faced Opponents (but not last played)
6. last played opponent.

#### Legendary match makging
Continue itterate on the ELO mach making system currently being used.


### Games required to reach Legendary
Following is a table of the number of games that is required to reach the next tier starting from Neophyte 3 RP = 0, with a specific win %, this does not account for the level drop protection of 2 losses while being at 0 RP at a level.


|Win Rate|Apprentice|Disciple|Primus|Legendary|Total|
|--------|--------|--------|--------|--------|--------|
|100%| 15 | 15| 15| 15 | 60 |
|90% | 17 | 18 | 18 | 19 | 72 |
|80%| 19 | 20 | 22 | 25 | 86 |
|75%| 20 | 22 | 24 | 30 | 96 |
|70%| 22 | 24 | 28 | 38 | 112 |
|65%| 24 | 27 | 32 | 50 | 133 | 
|60%| 25 | 30 | 38 | 75 | 168 |
|55%| 28 | 35 | 47 | 150 | 260 |
|50%| 30 | 40 | 60 | N/A | 

It could be argued that these numbers are too small, and too many players might end up on Legendary status, but the argument could be, that is good because at Legendary tier is where the real competitive player starts so make it doable for playes to qualify to that level in the first month of Leaderboard Season feels reasonable, though an easy way to slow things down would be to make each tier 4 levels instead of the proposed 3 levels, this would show things down.

### Season reset
CTA has already said there will be seasons, its not clear yet if those seasons are going to conside with the release of new set of cards, or the ladder reset is going to be more frequent, e.g. every 6 month based on card set release cycle, or monthly. I will make some suggestions on how to do reset, assuming a 6 month cycle for card releases (e.g. as we know Arkhante -> Mantris -> Rift, they are suppose to be roughly 6 month apart, so lets go with that assumption and for this proposal I will refer to it as Set Season vs Leaderboard Season.

So, Set Season = 6 months, I would propose then that Leaderboard Season = 2 Months. This would allow for 3 Leaderboard seasons for each Set Season.

#### Leaderboard Season reset
Leaderboard seasons can be refeered to as "Arkhante LS I" meaning "Arkhante Set Season, Leaderboard Season I" 
Move players down according to this:
* Neophyte is unafected by reset.
* Apprentice all players are reset to Apprentice level 3 and RP = 0.
* Disciple all players are reset to Apprentice level 2 and RP = 0.
* Primus all players are reset to Apprentice level 1 and RP = 0.
* Legendary all players are reset to Disciple level 3 and RP = 0. 


This will let players climb up again, and it will also allow for people of similar skill to be faced off against each other for the initial hectic moments after a reset. Each Leaderboard Season should be archivied and saved, so people can go back and look at it (players do like to look at their previous ATH achiements etc).

#### Set Season reset
The set will take place at the same time as the 3rd Leaderboard Season reset for the Set Season, and same procedure will be be used, but it will be possible to have a Set Season leaderboard based on ther average performance across all the 3 leaderboard seasons, and thus possible to crown a Set Season  winner, (deault to 1100 ELO for Legendary players that did not make it to legendary for other seasons).

#### Climbing after reset
To accelerate Legendary players climb back to Legendary status, a boost could be used for the first week after a reset, e.g. instead of earning 20 RP for a win ex-legendary players would earn 30 points while in disciple, 25 points in primus. This serves two purposes:
1. minimizes the amount of times strong players might get matched up with much weaker players.
2. makes the grind for legendary players shorter.

#### Match Making after reset
To minimize pairing legendary players with players that have never reached legendary before, all legendary players will first be matched with other Legendary players based on ELO raitings in the same tier, if no other legendary players can be found in tier after 30-45 second match with other players in the tier.

## . Existing Systems
### 1.1 Magic Arena
MA uses a hidden MMR, but like most other system they have choosen to implement a tierd progressing system for ranked games
reference[^1].

### 1.2 LoR
Sources: [^2]
### 1.3 Gwent
https://www.reddit.com/r/gwent/wiki/ranked/#wiki_ranked_mode
### 1.4 YMD
https://www.ggrecon.com/guides/yu-gi-oh-master-duel-ranks-ranked-system/
### 1.5 PTCGO
https://forums.pokemontcg.com/topic/76579-competitive-modes-on-ptcgo/
### 1.6 HeartStone
https://hearthstone.fandom.com/wiki/Ranked

# Other Systems

## Glicko

Glicko was designed as an improvment to ELO, the math is more complicated, but what it introduces is a variable called $RD$ Rating Deviation, to track how active a player is and how this might make their rating deviate away from the actual number. Its adding variability over time. This translates to less variability in ratings gained/lost for players that play more regularly and are generally more active. For unrated players, or people that play rarely the rating jumps can be significant, this is done in an attempt to faster find the correct level of the player. One other big differences vs ELO is that ratings are not a zero sum, e.g. winner and loose will not gain/loose the same number of rating points, this is all related to the rating variablity.

for an easy overview of the glicko system: https://www.englishchess.org.uk/wp-content/uploads/2012/04/The_Glicko_system_for_beginners1.pdf

and of course wikipedia got good coverage of it, and refernce to the original paper. https://en.wikipedia.org/wiki/Glicko_rating_system

## Glicko 2

Glicko 2 is an extenstion of the Glicko system. Glicko 2 adds a 3rd variable to the equaiton $\sigma$ which measures the degree of expected fluctuation in a player’s rating, based on how erratic the player's performances are. For instance, a player's rating volatility would be low when they performed at a consistent level, and would increase if they had exceptionally strong results after that period of consistency. The math gets a lot more complicated.

## TrueSkill (1 and 2)

This is Microsofts propritary system that probably require some type of licencing to use. It was designed to accomodate for team battles and infer a team 's strength based on the team members and matching against other teams and create rating system for both teams as well as induviduals. Math gets a lot more complicated, though it can be slightly simplified for the 1v1 environement.

https://www.microsoft.com/en-us/research/uploads/prod/2018/03/trueskill2.pdf

## Bayesian ELO
The idea is take into account previous games and the relative strength of those oponents.
https://www.remi-coulom.fr/Bayesian-Elo/


## Great resources on the Ranking System/Match making topic:
* Josh Menke is one of the most known ranking system "experts" having worked at Blizard/ActiVision (Hearstone, StartCraft etc), Microsoft (Halo), and currently working for Riot (wild rift, LoL, LoR, Valorant). from GDC 2016: https://www.youtube.com/watch?v=-pglxege-gU great talk about ranking/match making.
* interesting talk from Mario Izquierdo GDC 2017: https://www.youtube.com/watch?v=VnOVLBbYlU0 https://twitter.com/joshua_menke
* Bayesian Approximation Method for Online Ranking - https://jmlr.csail.mit.edu/papers/volume12/weng11a/weng11a.pdf
* An Elo-like System for Massive Multiplayer Competitions - https://arxiv.org/pdf/2101.00400.pdf



## Footnotes

[^1]: [fireball explanation of current ranking system](https://strategy.channelfireball.com/all-strategy/mtg/channelmagic-articles/how-many-games-do-you-need-to-play-to-hit-mythic-in-mtg-arena/#:~:text=There%20are%20six%20ranks%3A%20Bronze,tier%20consists%20of%206%20steps.)

[^2]: asd

[^3]: https://discord.com/channels/917028207566401586/917028207566401593/1041989794550530098
