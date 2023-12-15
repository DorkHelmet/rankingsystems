# The Current System

The following tiers exist:
* Bronze - Where you start, at 300 points.
* Silver
* Gold
* Platinum
* Diamond
  * Gladiator - The Top 11-110 in Diamond
  * Champion - The Top 1-10 in Diamond

## Rules of the Current System
* The First 30 games you play, you do not lose Leaderboard Points (LPs), except if you pass Platinum 250 points, then you will lose LPs if you lose.
* When a new Era starts, everyone starts in Bronze with 300 points.
* How many points you earn/lose is based on your underlying ELO rating (which cannot be seen, but to understand how it is calculated see  [ELO in CTA](#elo-in-cta)), but it is now 2x that from what is outputted from the ELO adjustment, so it can range from 14-90 depending on the difference in ELO.
* The first 4 tiers each have a total of 350 LPs, if you pass e.g. 350 Bronze you will go into Silver and the overflow number is your new Silver LP.
* You can drop a tier if you lose LPs. e.g. Gold at 10 LPs, and a loss with -50 points, you would end up in Silver 310.
* Match Making is still using the hidden ELO this can mean that you sometimes lose/gain more points than you would assume based on your opponent's current ranking on the leaderboard.

The current system moved the old system, which was a more pure skilled-based ELO system, towards a progression system but it is still a strange mix.

# Proposal for changes to the Leaderboard
League of Legends has by far one of the most successful online leaderboard implementations (it is similar in Legends of Runeterra) so instead of re-inventing the wheel when it comes to leaderboards why not do something similar? Have already decided to embrace the naming of the tiers, though LoL and LoR has a lot more active players than CTA does, so scaling it down a bit might be the way to go, and keep things similar to what it is now.

## The Tiers
* Bronze
* Silver
* Gold
* Platinum
* Diamond
  * Gladiator - The Top 11-110 in Diamond
  * Champion - The Top 1-10 in Diamond

Each tier (Bronze - Platinum) is split into two divisions "II" and "I", Each Division is made up of 150 LPs. where it goes from Bronze II -> Bronze I -> Silver II ... 

## Bronze
* A new player starts in Bronze II, with 100 LPs.
* In bronze a player cannot lose LPs for the first 10 games.
* A win rewards 50 LPs
* A loss (after the first 10), is -10 LPs.
* A new player would require a total of 4 wins to get promoted to Silver II (assuming no losses, or losses taking place in the first 10 games)

## Silver
* A win rewards 50 LPs
* A loss, is -20 LPs

## Gold
* A win rewards 40 LPs
* A loss, is -30 LPs

* ## Platinum
* A win rewards 30 LPs
* A loss, is -20 LPs

* ## Diamond
* A win rewards 25 LPs
* A loss, is -25 LPs

#Propsaol for changes to the Match Making Algo






# ELO in CTA
Explanation of how ELO works in CTA.

The expected result of the match for player $E_A$ where $R_A$ = Rating of Player A, and $R_B$ = Rating of Player B.
$$E_A= \frac{1}{1+10^{\frac{R_B-R_A}{400}}}$$

Same for Expected result of Player B $E_B$.
$$E_B= \frac{1}{1+10^{\frac{R_A-R_B}{400}}}$$

to calculate the new rating of player A, $R\'_A$

$$R\'_A = R_A + K * (S_A - E_A)$$

$S_A$ is the score of the game, 1 = win , 0 = loss
$K$ (K-Factor) scales, as per Quentins post[^1], for ratings below 1750 $K = 40$ 

CTA used to use a scaling K-Factor (do not know if that is still the case, it used to be) I believe this might no longer be the case.
| Rating        | K-Factor      | 
| ---------- |:----------:|
|< 1750 | 40 |
|1751 - 2250 |  30|
|2251 - 2550|  20|
|2550 < |  10|
