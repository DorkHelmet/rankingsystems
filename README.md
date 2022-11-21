# CTA ranking system

## Skill, Progression or Hybrid?
In chess, ELO (or chess.com rating) rule all, everything is based on your rating, and that is what people chase. This is also what we have been experimenting with in CTA since the OpenBeta. This is what I would consider a pure "Skill" system, the alternative is a "progression system" like we know from RPGs etc you level up, you can have setbacks but generally you are progressing, and finally we got the hybrid solution which can combine the two systems, e.g. for new players its a progression system but for the top players its a pure skill system. Most online card games have either a progression system or a hybrid system. In a [later section](#existing-systems) I explain how some of the most popular online TCG/CCGs have implemented their system, but for now lets dive into my proposal for CTA.

## Tierd ranking system
The purpose of a tierd ranking system is to make sure people get to play with other players that are similar in strength because feeling like you can win is very important to make people come back and play again, anyone that regularly get dominiated by stronger players is probably going to stop playing. It is also important to have an area where top players can face each other, where there is real competition. This proposal comes from my person interest in ranking/match making system and having played and read a lot about many different ranking system.

I propose the following system for CTA:

There are 5 tiers (naming of course can be anything)
* Neophyte  - New player area
* Apprentice - Players with Experience
* Disciple - Players with Experience
* Primus - Players with Experience
* Legendary - Leader board

The first four tiers consist of 3 levels each, Level 3 is the lowest level in a tier, Level 1 highest, it goes Neophyte 1 -> Apprentice 3. 

Each level is made up of 100 RP (Ranking points). When you win a game you earn a certain amount of RPs based on the tier you are in, when you loose a game you will loose a certain amount of RPs, with 3 levels per tier the player need to accumulate a total of 300 RP to get promoted to the next tier. It is not possible to get demoted from a tier, though players can move from Level 1 to Level 2.

All of the following numbers are sugestions and can of course be tweaked as needed.
|Tier | Win RPs | Loss RPs|
|-----|---------|---------|
|Neophyte| 20 | 0 |
|Apprentice| 20 | -5 |
|Disciple| 20 | -10 |
|Primus| 20 | -20 |

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
In legendary you no longer use RPs, but start using raw ELO (or whichever type of ranking system is used) to represent a users standing. Leaderboard shows the ELO raiting (as the current leaderboard). if ELO is used, everyone starts with rating of 1200, use sliding K factor (1000-1500 = 30, 1501-1750 = 25, 1751 - 2000 = 22, 2001-2250 = 20, 2251 - 2500 = 18, 2500+ = 15). Not possible to go below 1000 ELO.

### Promotion & Demotions

#### Promotion
Once a player goes past 100 RP for a level they are promoted to the next level (possible tier promation, if it was Level 1). Each promation the player will autoamtically get 5 RP in the new level. 

#### Demotion
While a season is ongoing a player cannot be demoted to a lower tier, if the player is at 0 RP at a Level 3, loosing again will not change anything. A player start each level with 5 RPs, if a player loose a game and would end up with 0 or less than 0 RPs he will have 0 RPs for that level. A level demotion will only happen on the second loss while having 0 RPs. e.g.
* Player A at level Primus 2, has 5 RPs, he looses a game, he will now be at Primus 2, with 0 RP, he looses again, but because it was the first loss at RP 0 there was no demotion, but if the player loose again the player will be demoted to Primus 3. 


### Match Making
Match making finds a pool of possible opponent, the pool of opponents is expanded in the following order, each expansions happens every 20-30 seconds, always avoid matching with last 3 opponents as long as possible:
1. Same tier and same Level
3. Same tier and if not Neophyte tier, Level 1 add level 3 from higher tier, if Level 3 add level 1 from lower tier 
4. If Neophyte pair with bot.
5. previous faced Opponents (but not last played)
6. last played opponent.

#### Legendary match making
Continue itterate on the ELO ranking system currently being used.


### Games required to reach Legendary
Following is a table of the number of games that is required to reach the next tier starting from Neophyte 3 RP = 0, with a specific win %, this does not account for the level demotion protection of 2 losses while being at 0 RP at a level.


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

It could be argued that these numbers are too small, and too many players might end up on Legendary status, but the counter argument is that it is good because at Legendary tier is where the real competitive play starts. So make it doable for playes to qualify to that level in the first month of Leaderboard Season feels reasonable, though an easy way to slow things down would be to make each tier 4 or even 5 levels instead of the proposed 3 levels, this would slow things down, but still make people feel like they are making progress.

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


### Conclusion
The proposed system is an amalgation of many of the most prominent competitive online card games currently. I have tried to include some of what I consider the best features and put them together with the purpose to make gaming the most fun for the most players, where players can feel a sense of progress, but also making players feel that reaching "Legendary" status is not easy and require a certain amount of dedication but not an obecene amount of it. Obiviously there are many numbers and features that can be tweaked, but I strongly think that a system like this would greatly enhance the player experience for both old and new players. One thing that I did not deleve into here, but which is closely linked to the ranking system is of course the rewards! There are 2 schools of thoughts on this either you give a bigger reward at the end of the season based on highest achivement, or you have one time (ever, or per season) rewards as players reach certain milestones e.g. Levels, tiers etc. Very common in other card games is of course the granting of avatars, card backs, frames, borders and other cosmetic things for players to show off how far they reached in a previous season.


# 1. ELO in CTA
Explanation how ELO works in CTA.

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



## Existing Systems
### 1.1 Magic Arena
MA uses a hidden MMR, but like most other system they have choosen to implement a tierd progressing system for ranked games:
* There are six tiers: Bronze, Silver, Gold, Platinum, Diamond, and Mythic. Each non-Mythic rank has four levels, with level 1 being the best and level 4 being the worst within that tier. For Constructed, each level consists of 6 steps. For Limited, Bronze consists of 4 steps and all other tiers consist of 5 steps.
* Tiers operate separately for Constructed and Limited. To tier up in Constructed, you’ll want to play in the “Ranked” best-of-one games or in the “Ranked” best-of-three games. Both contribute towards the same tier. To tier up in Limited, you’ll want to enter the best-of-one Draft events.
* Everyone initially starts at Bronze level 4. You gain steps with wins: in best-of-one, it’s 2 steps gained per win in Bronze and Silver and 1 step gained per win in Gold, Platinum, and Diamond. You lose steps with a defeat: in best-of-one, it’s 0 steps lost per win in Bronze and 1 step lost per win in all other ranks.
* In best-of-three, these gains and losses are doubled, and only the match result counts. So if you win a match 2-1 in Gold, you move up 2 steps. 
* Once you get enough steps, you’ll move into the next leve of that tier, or if you’re at level 1, into the next tier.
Once you ascend into a new tier, you’re safe for the rest of the season. No matter how many times you lose, you can’t fall from a tier (e.g., from Gold 4 to Silver 1).
Although losses can push you down a level within a tier (e.g., from Gold 3 to Gold 4), there is some protection when you move into a level (but has not been official published)

[Channel fireball more information about the ranking system](https://strategy.channelfireball.com/all-strategy/mtg/channelmagic-articles/how-many-games-do-you-need-to-play-to-hit-mythic-in-mtg-arena/#:~:text=There%20are%20six%20ranks%3A%20Bronze,tier%20consists%20of%206%20steps.)

### 1.2 Legends of Runeterra
LoR uses a very similar system to LoL, basically:
* There are 7 tiers, ordered: Iron, Bronze, Silver, Gold, Platinum, Diamond and Master.
* Within each tier are numbered divisions, namely I, II, III and IV. The lower the division within a given tier, the closer each player is to the next tier. By earning enough points in Silver I, a player will be promoted to Gold IV.
* Master tier functions a bit differently than the rest of the ranked system. It doesn't have divisions. Within the Master tier, players are ranked by Matchmaking Rating (MMR) from highest to lowest.
* Players earn League Points (LP) by winning ranked matches in LoR, and lose points when lose ranked games. LP represents a numerical value from 1 to 100 that will rise and fall within a division based on your wins and losses. Once player LP exceed 100, they will climb to the next division, or the next tier.
* Players who exceed 100 LP will get a promote. After getting a promote, the player LP is set to 10.
* Player demote from a division when lose a game at 0 LP. As long as player has any LP, they won't demote from a lost match.
* Players can demote from a higher division to a lower one, but they can't demote to a lower tier.
* A Ranked season starts whenever a new expansion is released and shares its name.
 

LP gains per tier:
|Rank|LP Gain|LP Loss|Tie |Games needed on 50% WR|
|-----|----|-----|------|----------|
|Iron	|+50|-0|+10|16|
|Bronze|+40|-10|+6|26.66|
|Silver|+35|-15|0|40|
|Gold|+30|-15|0|53.33|
|Platinum|+25|-20|0|160|
|Diamond|+22|-22 |0|-|

so climing from Iron -> Dimond with a 50% win ration would take almost 300 games.

Master works differently, as its more like an ELO style of gain/losses is based on opponent, as well as those around your ranking, but it has been made clear that it is impossible to climb in Master unless you can maintain a 62.5%+ win ratio.

#### Season Reset
Each season lasts two months. At the end of season, ranks will be partially reset for the new season.

Master accounts will reset to Platinum 4, regardless of how much LP they have.
Diamond and Platinum accounts will drop 750 LP.
Gold and Silver accounts will drop 675 LP.
Bronze and Iron accounts will reset to Iron IV.


* https://leagueoflegends.fandom.com/wiki/Rank_(Legends_of_Runeterra)
* https://www.reddit.com/r/LegendsOfRuneterra/comments/x3f8dr/new_lp_gainloss_changes_per_ranked_tier/
* https://support-legendsofruneterra.riotgames.com/hc/en-us/articles/360041193433-Ranked-FAQ-Legends-of-Runeterra


### 1.3 Gwent

When you're playing in Ranked Mode, you will be matched against opponents of the same rank. The ranks start from Rank 30 and go up to Rank 0 (also called Pro Rank). To go from a rank to another one, you need to earn 5 mosaic pieces and once you reach a new rank, you cannot go down during the season. You get a mosaic piece when you win a game, you lose one when you lose a game.

Between rank 30 and 8 (included), you can get 2 pieces if you are on a winning streak (more than 3 wins in a row).

At the end of the season, after getting your rewards, you will lose 0-3 rank(s) based on your final rank. Players at Rank 0 will drop to Rank 3 unless they're in top 500. Players from Rank 1 to 13 will lose 2 ranks and players with Rank from 14 to 23 will drop by one rank. Each season last a month and usually ends the last working day of the month at 10 AM (CET). Next one starts the same day at 12 PM (CET) or after patch if a patch is planned.

https://www.reddit.com/r/gwent/wiki/ranked/#wiki_ranked_mode

### 1.4 Yu-Gi-Oh Master Duel

there are five ranks that can be earned, all of which contain different tiers that you can rise through. The YuGiOh Master Duel tiers are Rookie, Bronze, Silver, Gold, and Platinum, which all have a five further levels except Rookie, which has two.

https://www.ggrecon.com/guides/yu-gi-oh-master-duel-ranks-ranked-system/

### 1.5 Pokemon Online
doens't really have a ranking system.. 
https://forums.pokemontcg.com/topic/76579-competitive-modes-on-ptcgo/

### 1.6 HeartStone

Heartstone tracks players win through the ranking system using "Stars", get enough stars and you will rank up. 

* There are 40 new player ranks, 50 regular ranks, and a prestigious Legend rank above all other ranks. 
* New players to Hearthstone start in the Apprentice League, which contains 40 ranks, from Apprentice 40 to Apprentice 1. These ranks are exclusive to new players only, and players cannot lose stars in these ranks.
* There are five Tiers for established Hearthstone players: Bronze, Silver, Gold, Platinum, and Diamond. Each league has a range of 10 levels, numbered from 10 to 1 in increasing level. For example, a player can be categorized as being in "Gold 5", "Gold 2", or "Diamond 1".
* Players advancing out of Diamond 1 of the normal player ranks will be inducted into the prestigious Legend rank.
* 

Winning matches earns players stars, and stars are needed to advance ranks. Each rank contains three "star slots", so only three stars are needed to advance out of each rank. The number of stars awarded for winning each match is determined by a Star Bonus, which is given at the start of each season, and also by a winning streak bonus. Players are awarded a Star Bonus based on both the player's MMR and numbered rank in the previous season.This Star Bonus is a multiplier on the number of stars a player earns from each match win.

For example, a Star Bonus of 7x means that a player will earn 7 stars for winning a match. Every player starts with at least 2 Star Bonus at the beginning of a season.

Losing games causes players to lose a star, unless they are at a level floor. At a level floor, a player can never fall below that level for the remainder of the season. level floors occur at every 5 level in the ladder, for example at "Bronze 5" or "Gold 10". Upon climbing and hitting each level floor, a player's Star Bonus will decrease by 1, meaning that as a player climbs up in level, it will become more challenging for the player to climb up to higher ranks.

Each month of Ranked play is called a season. The first time the player logs in or enters a match following the start of a new season, they will be shown a special announcement informing them of their rank at the end of the last season, their best rank during that season (which determines end-of-season rewards and next season's initial rank), their rewards for that season, and their rank at the start of the new season.

At the start of each Ranked play season, all players are reset back to Bronze 10.

https://hearthstone.fandom.com/wiki/Ranked

# Alternatives to ELO

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

[^3]: https://discord.com/channels/917028207566401586/917028207566401593/1041989794550530098
