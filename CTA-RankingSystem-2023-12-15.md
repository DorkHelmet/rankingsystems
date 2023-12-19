# The Current System

The following tiers exist:
* Bronze - Where you start
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
* Leaderboard camping is prevented by forcing a number of games played based on the tier, or no reward will be awarded.

The new system currently in place replaced the old system, which was a more pure skilled-based ELO system, and moved everything more towards a progression system but it is a strange mix, below follows a proposal to continue towards a more progression-oriented leaderboard system.


# Proposal for changes to the Leaderboard
League of Legends has by far one of the most successful online leaderboard implementations (it is similar in Legends of Runeterra) so instead of re-inventing the wheel when it comes to leaderboards why not do something similar? Though LoL and LoR have a lot more active players than CTA does, so scaling it down a bit might be the way to go, and keep some things things similar to what it is now. The minimum number of games that has to be played, I think is good, and would recommend leaving as it is.

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
* A loss, is -25 LPs

* ## Diamond
* A win rewards 25 LPs
* A loss, is -25 LPs

## Demotions (moving down a tier)
There are many ways to handle demotions, and in some games, it's not possible between tiers(e.g. LoL), but to stay with the theme/ethos of CTA where it is possible to fall a tier if you lose this could be kept. However I will recommend some safeguards to make it less painful because as we know everyone strives to make it into the next tier to earn the next great reward and it can be quite devastating/demoralizing to fall out of a tier, players need to face a challenge and overcome hardship but there is a thin line between a challenging environment and demoralizing one that turns players off the game.

* if LP is larger than 0, but the lost LP is more than LPs remaining, LP is set to 0
* If LP is 0 and Loss, the player is demoted to the lower division and LP is set to 140.

**Division example:**
* The player is currently in Gold I with 15 LPs.
* The player loses one match and will get -20 LPs, but instead of going down a division right away, the player is set to 0 LP in Gold I.
* The player loses one more match and will get -20 LPs, but since the player is already at 0 the player will be demoted to Gold II with 140 LPs.

**Tier example:**
* The player is currently in Platinum II with 15 LPs.
* The player loses one match and will get -25 LPs, but instead of going down tier, the player is set to 0 LP in Platinum II.
* The player loses one more match and will get -25 LPs, but since the player is already at 0 the player will be demoted to Gold I with 140 LPs.

## Promotion (moving up a tier)
When a player breaks through to a new Division or Tier they will automatically get set to 10 LPs at a minimum, and 30 LPs at a maximum. This allows for some carryover from the last win in the previous tier and prevents anyone from starting with 0 LPs in the new division/tier.

## Streak Bonus
A thing to consider is a streak bonus, e.g. if you win 3 in a row, maybe you get an extra 20 LPs, and then if you win 7 in a row an extra 50 LPs. This helps to keep players motivated and the excitement for getting win streaks is a thing people want to talk about on social media, which is good advertisement. Furthermore, it also helps to accelerate top players at the start of an Era so they can get to the top faster and not demoralize too many lower-ranking players as the top players climb back to their normal ranking at the top.

# Propsal for changes to the Match Making Algo
Switching to TrueSkill MMR system would be preferable, But I do realize that is quite a lot of work and the math for the TrueSkill system is not that easy to work through, so lets assume that the current ELO system is kept. But the ELO rating should only be kept in the background and never shown to players, the ELO rating should be kept through Eras (never reset) assuming the K-factor is scaled as described in [ELO in CTA](#elo-in-cta) as ELO only make sense over thousands of matches to establish the skill of a player. But there is another very important part of the Match Making, It should only be possible to be matched with players following some basic criteria:
* Players will first be tried to be matched with other players in their division.
* Players can only be matched with Players +1/-1 Division
* When multiple options are available use ELO to try to match similar ELO.

**Example Gold II:**
* first 60 seconds it will try to match with any other player in Gold II and if multiple possible opponents pick the opponent with closest ELO
* from 61 seconds opponent pool will be expanded to players in Gold I and Silver I, and if multiple possible opponents are available, match with the one closest in ELO

**Example Platinum I:**
* first 60 seconds it will try to match with any other player in Plat I and if multiple possible opponents pick the opponent with closest ELO
* from 61 seconds opponent pool will be expanded to players in Diamond with less than 150 LPs and Platinum II, and if multiple possible opponents are available, match with the one closest in ELO

**Player in Diamond**
* first 60 seconds it will try to match with any player in Diamond +/- 100 LPs, if multiple possible opponents pick the opponent with closest ELO
* from 61 seconds opponent pool will be expanded to any players Diamond, if multiple possible opponents pick the opponent with closest ELO 
* from 90 seconds opponent pool will be expanded to Players in Platinum I, if multiple possible opponents pick the opponent with closest ELO



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
