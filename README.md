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



For more deep dives in understanding ELO: 

## 1. Existing Systems
### 1.1 MA
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


## Great resources on the Ranking System/Match making topic:
* Josh Menke is one of the most known ranking system "experts" having worked at Blizard/ActiVision (Hearstone, StartCraft etc), Microsoft (Halo), and currently working for Riot (LoL, LoR, Valorant). from GDC 2016: https://www.youtube.com/watch?v=-pglxege-gU great talk about ranking/match making.
* interesting talk from Mario Izquierdo GDC 2017: https://www.youtube.com/watch?v=VnOVLBbYlU0 https://twitter.com/joshua_menke
* Glicko
* Glicko2
* Bayesian Approximation Method for Online Ranking - https://jmlr.csail.mit.edu/papers/volume12/weng11a/weng11a.pdf
* An Elo-like System for Massive Multiplayer Competitions - https://arxiv.org/pdf/2101.00400.pdf
* 



## Footnotes

[^1]: [fireball explanation of current ranking system](https://strategy.channelfireball.com/all-strategy/mtg/channelmagic-articles/how-many-games-do-you-need-to-play-to-hit-mythic-in-mtg-arena/#:~:text=There%20are%20six%20ranks%3A%20Bronze,tier%20consists%20of%206%20steps.)

[^2]: asd

[^3]: https://discord.com/channels/917028207566401586/917028207566401593/1041989794550530098
