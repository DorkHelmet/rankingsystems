# Making Crafting Fairer
This is a proposal on how to make crafting feel more fair, without skewing the numbers in a significant way, but it will mitigate "bad luck" and reduce people's frustration with RNG in crafting.

## Normal distribution and randomness
Crafting is currently completely random, every awakening/combo making is treated as a singular event and basically, a D100 dice is rolled and whatever value is rolled determines the grade of the awakened/combo card. The problem with randomness is how normal distribution works, the classic bell curve:
![Alt text](Normal-distribution-bell-shaped-curve.png?raw=true "Title")

To explain what this graph means. Let's imagine that everyone did 1000 awakenings, then you might think that well everyone should get close to % of C, B, A, S, but this is not the case, the majority of e.g. the two 34% blocks in the middle means 
This shows how the majority will have a very close to the "ideal" numbers, while the absolute center will have the exact numbers, but then the further out you go in each direction the bigger the divergence will be e.g. going towards the right could mean that you have more "luck" and ending up with a much larger % of S, A, B than is the norm, and the same going in the other direction you might not have any S at all, this is just how random distribution works. Of course, being on the right side will be great while being on the left would be terrible and would be quite demoralizing and feel very "unfair", I will now describe a proposal to make things feel more fair, without disturbing the total distribution too much, but will remove the extreme on the left side, while leaving most of the upside on the right.

## The pack stock system
Inspiration for this comes from the current way that pack stock/pools are done, we have all seen the booster pools, each pool has X cards from each type in them, and you get one pool from, it is explained in this [noria article](https://noria.crosstheages.com/hc/en-gb/articles/19685337754385-Mythic-and-Permanent-Series) and more flavour from the original patch notes:
* <I>New chests have a personal stock which guarantees you that after opening 1200 packs, you will get everything possible and everyone will have the same exact amount of cards including foil and non-foil cards.[0.13.4349](https://github.com/crosstheages/public-data/blob/main/patch-notes.md#0134349-patch)
* In the Arkhante serie: You are now able to reset your serie. As you know, earlier this year we introduced the stock system to the shop. Meaning that cards have a specific amount of personal stock that you can have when buying packs to guarantee you will have all cards after buying sufficient packs. You can look at the state of your serie on the Arkhante collection. You can now reset that stock to start with a fresh stock.
  * Example: You can only have 1 Foil Sarash card within your serie. If you got it by opening your first Neo Plenition, you won't be able to get it until you run out of stock for all your other cards. With the Reset, you are able to fill up all the stock, and you might be able to get another Foil Sarash on your next Omega if you are lucky. [0.16.5787](https://github.com/crosstheages/public-data/blob/main/patch-notes.md#0165787-patch)</I>

## Current crafting %
To get the current official awaken numbers check this [Noria article](https://noria.crosstheages.com/hc/en-gb/articles/17715859811089-Awakening)

|Grade|% pure cards|% impure cards|Bonus for owned cards|
|-----|----|-----|------|
|C|60%|70%|-10|
|B|27.5%|22%|+5.5|
|A|10.5|7%|+3.5|
|S|2%|1%|+1|

for merge/combo making check this [Noria article](https://noria.crosstheages.com/hc/en-gb/articles/17715860877713-Merge)
|Grade|% lowest C|% lowest B|% lowest A|% lowest S|
|-----|----|-----|------|------|
|C|70%|0|0|0|
|B|22%|73.33%|0|0|
|A|7%|23.33%|87.5|0|
|S|2%|3.33%|12.5|100%|

## Proposal
In a similar way to packs, I believe crafting can be made to feel more fair but still have randomness, but still some guarantees of getting things over the long haul.

**For Awakening**
* there are 2 pools, one pure and one impure.
* Each consisting of 100 Awakenings.
* Each pool contains the exact number as the awakening numbers above( (rounding down to offset the skew)
  * Pure: 2S, 10A, 27B, 61C
  * Impure: 1S, 7A, 22B, 70C
* There is no difference between the rarities of the cards awakened, it is all taken from the same pool.
* Same as with boosters, anyone can "reset" their stock at any time by the press of a button, and the "stock" will be refilled.

**Combo/Merge**
* There are 3 pools, based on the lowest card in the combo, C, B, and A.
* there are 100 Combos in each pool.
* stock for each pool is as the % above:
  * C: 2S, 7A, 22B, 70C
  * B: 3S, 23A, 74B, 0C
  * A: 12s, 88A, 0B, 0C
* There is no difference between the rarity, it is all taken from the same pool.
* Same as with boosters, anyone can "reset" their stock at any time by the press of a button, and the "stock" will be refilled.

### Questions
**What happens if the stock grade is empty?**
just roll again, until you get one that is not empty, until ALL grade pools are empty, when the 100th and last grade is handed out from a pool the pool is automatically reset.

**What about foils?**
There is an argument to be made to have a full set of pools for Foil cards as well, or you could leave foils random like it is now. This is more of a decision that will have to be made by CTA
* but having foil pools is an option
* Everything part of the same pool foil and none foil
* Not using pools for foils.
I would probably lean towards Foil having its own pools.

**What about Static, Flex, Eternal cards?**
same as with foils, maybe the pools only work for Eternal cards, or maybe there are different pools for everything? For CTA to decide, I would lean towards the stock/pool system only works for Eternal cards. Static and Flex cards remain as it is now, this would encourage people to upgrade their Flex cards to Eternal cards before awakening/merging hence increasing the value of the CTA token.

## Conclusion
Since the majority of players will fall in the 2 center blocks above (in the bell curve graph) this will not affect what grade their card get since they will be mostly on the distribution, and those that do get lucky and get 1-2S or a large number of As early on always have the option to reset their pools and as such can continue to have luck. Where the above proposal is significant is for those unlucky people on the extreme left side of the distribution, for them, this would be a strong motivation to continue to awaken cards because they know that eventually, they will get their ratio of S, A and B cards. I assume some people are already thinking about ways that this could be "gamed" Yes, it is possible that early on you awaken more common, uncommon, and rare cards, and assuming you are "lucky" to do more than 60% Cs at those times, you have a good chance, later on, to focus on UR, M and get those at a higher grade, BUT there are a lot "maybes" involved in this, and probabilistically it is not something to be overly concerned about. Over time, would this skew the total supply to have a slightly higher distribution of S, A, B than the pure awaken numbers? Yes, it would because people can get lucky and reset, so we would not have the extremely unlucky to counter the extremely lucky, but I strongly feel that this is well worth it from player satisfaction and retention point of view. Players can feel a little bit more in control and not be totally victim to RNG, the same way that I think the majority of players think the stock system for packs is a good thing and helps combat bad RNG.


