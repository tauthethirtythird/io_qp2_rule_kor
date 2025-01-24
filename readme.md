# Translation of TETR.IO qp2 rules observance summary By MrZ_26

## Start

This mode doesn't have a global "round", everyone can enter at any time without waiting

## QP2

This mode's theme is climbing `Zenith Tower`, the final score is your `Altitude`.

After reaching a certain altitude you will enter the next floor, every floor's required altitude is listed below:

| Floor | Altitude Range | Name |
| - | - | - |
| Floor 1 | 0m - 50m | Hall Of Beginnings |
| Floor 2 | 50m - 150m | The Hotel |
| Floor 3 | 150m - 300m | The Casino |
| Floor 4 | 300m - 450m | The Arena |
| Floor 5 | 450m - 650m | The Museum |
| Floor 6 | 650m - 850m | Abandoned Offices |
| Floor 7 | 850m - 1100m | The Laboratory |
| Floor 8 | 1100m - 1350m | The Core |
| Floor 9 | 1350m - 1650m | Corruption |
| Floor 10 | 1650m+ | Platform Of The Gods |

## Climb Speed (Main information source: ThTsOd)

`Climb Speed` (called `rank` in the code) affects how fast you gain altitude, every action that increases altitude is impacted by its' multiplier bonus. Increasing climb speed requires experience (called xp hereafter).

At climb speed 1 the multiplier is ×0.25, every increase in climb speed level adds another ×0.25 (Upon reaching ×2.75 it becomes white with no further difference, but in reality there's no upper limit).

### Gaining altitude & XP, and promoting

The routes of gaining altitude and xp are listed below:

| Action | Effect |
| - | - |
| Time | Every second 1m, but when you're 6m~1m below next floor, the speed of altitude gain over time evenly decreases from ×1 to ×0 |
| KO | 15m ("Expert+" weakens to 8m) |
| Sending attack | `lines`m and `lines+0.05`xp |
| Cancelling garbage lines (Non-Expert) | `lines/2+0.05`xp |
| Clearing lines (Non-Expert) | `min(lines,2)+0.05`xp |

> Note that all altitude gain is impacted by your `rank`, technically the multiplier is `rank/4`, for example at the start `rank` is 1, multiplier is ×0.25, every 4 seconds gain 1m

> When your distance to the next floor is under 2m, clearing lines can instantly +3m to proceed to the next floor, this rule only applies at
 when gaining altitude, the newly increased altitude will first be stored into a temporary variable, every frame release 10%, at maximum 10m 

The xp required to reach the next climb speed level is `4*rank`. once your xp meets the conditions your climb speed increases by one and your xp decreases by the amount that was previously required.  
Once you have promoted to the next climb speed level, for 5 seconds xp will stop naturally decreasing (see xp loss chapter for details) to prevent instantly demoting right after.

There is also a `promotion fatigue` system: Every time you increase a climb speed level, the `no natural xp decrease for 5 seconds` from the previous section becomes a second shorter (until 1 second), meaning repeatedly promoting/demoting causes the effect to be weaker. To reset it back to 5 seconds you have to reach 50% of the next climb speed level (middle of the experience bar).

### Skipping levels

Every time you increase a climb speed level, if the xp afterwards is enough to increase another climb speed level, then you gain an extra `xp/required xp` amount of climb speed level, **and xp is not removed**  
每次升级的瞬间，若还有大量剩余xp（发生在爆了大几十B2B产生巨量攻击时）仍然超过升级所需xp，则额外升 `xp/所需xp` 级，**且不扣除这些多余的xp**  
The moment you promote a climb speed level, if there's still a large amount of remaining xp (occuring when several tens of large B2B attack is released) and is still over the amount to increase another climb speed level, thetn you gain an extra `xp/required xp` ranks, **and these extra xp are not removed**

Which means this situation can happen:

    One frame - B2B breaks causing huge spike and XP increase
    Next frame - Promote + skip levels 
    Next frame - Can skip another climb speed level

### xp loss

Climb speed xp gradually diminishes over time, decreasing by `e*(rank^2+rank)/3600` xp every frame.  
e changes depending on if Expert is enabled, see below for a table:

| Mode | value of e |
| - | - |
| Regular | 3 |
| Expert | 5 |
| Duo | 3+amount of players with Expert |

When xp is under 0 you lose a climb speed level, afterwards your xp becomes the maximum xp of the previous climb speed level.  
Below are some calculated statistics for convenience:

| rank | xp required to promote | seconds to demotion | xp loss per second |
| :--: | :-: | :---: | :--: |
|  1   | 4   | 40.00 | 0.1 |
|  2   | 8   | 26.67 | 0.3 |
|  3   | 12  | 20.00 | 0.6 |
|  4   | 16  | 16.00 | 1.0 |
|  5   | 20  | 13.33 | 1.5 |
|  6   | 24  | 11.43 | 2.1 |
|  7   | 28  | 10.00 | 2.8 |
|  8   | 32  | 8.89  | 3.6 |
|  9   | 36  | 8.00  | 4.5 |
|  10  | 40  | 7.27  | 5.5 |
|  11  | 44  | 6.67  | 6.6 |
|  12  | 48  | 6.15  | 7.8 |
|  13  | 52  | 5.71  | 9.1 |
|  14  | 56  | 5.33  | 10.5 |
|  15  | 60  | 5.00  | 12.0 |
|  16  | 64  | 4.71  | 13.6 |
|  17  | 68  | 4.44  | 15.3 |
|  18  | 72  | 4.21  | 17.1 |
|  19  | 76  | 4.00  | 19.0 |
|  20  | 80  | 3.81  | 21.0 |
|  21  | 84  | 3.64  | 23.1 |
|  22  | 88  | 3.48  | 25.3 |
|  23  | 92  | 3.33  | 27.6 |
|  24  | 96  | 3.20  | 30.0 |
|  25  | 100 | 3.08  | 32.5 |
|  26  | 104 | 2.96  | 35.1 |
| rank | xp required to promote | seconds to demotion | xp loss per second |
| Expert 1   |   4 | 24.00 |  0.167 |
| Expert 2   |   8 | 16.00 |  0.500 |
| Expert 3   |  12 | 12.00 |  1.000 |
| Expert 4   |  16 |  9.60 |  1.667 |
| Expert 5   |  20 |  8.00 |  2.500 |
| Expert 6   |  24 |  6.86 |  3.500 |
| Expert 7   |  28 |  6.00 |  4.667 |
| Expert 8   |  32 |  5.33 |  6.000 |
| Expert 9   |  36 |  4.80 |  7.500 |
| Expert 10  |  40 |  4.36 |  9.167 |
| Expert 11  |  44 |  4.00 | 11.000 |
| Expert 12  |  48 |  3.69 | 13.000 |
| Expert 13  |  52 |  3.43 | 15.167 |
| Expert 14  |  56 |  3.20 | 17.500 |
| Expert 15  |  60 |  3.00 | 20.000 |
| Expert 16  |  64 |  2.82 | 22.667 |
| Expert 17  |  68 |  2.67 | 25.500 |
| Expert 18  |  72 |  2.53 | 28.500 |
| Expert 19  |  76 |  2.40 | 31.667 |
| Expert 20  |  80 |  2.29 | 35.000 |
| Expert 21  |  84 |  2.18 | 38.500 |
| Expert 22  |  88 |  2.09 | 42.167 |
| Expert 23  |  92 |  2.00 | 46.000 |
| Expert 24  |  96 |  1.92 | 50.000 |
| Expert 25  | 100 |  1.85 | 54.167 |
| Expert 26  | 104 |  1.78 | 58.500 |

### Appearance

You can view which climb speed you're at under the board, a simple text description of the appearances are shown below:

| rank | Multiplier | Color | Shape | Hyperspeed notes |
| :-: | :--: | :-: | - | - |
|  1  | 0.25 | none         | a progress bar | |
|  2  | 0.50 | red          | a triangle added below | |
|  3  | 0.75 | orange       | wings added to triangle | |
|  4  | 1.00 | yellow-green | wings increase size | |
|  5  | 1.25 | blue         | wings increase size + add base | |
|  6  | 1.50 | magenta      | wings extend to full size | |
|  7  | 1.75 | light orange | wings become more detailed | lowest rank without exiting hyperspeed |
|  8  | 2.00 | turquoise    | pair of parallelograms added on top | hyperspeed trigger at f1/f2 |
|  9  | 2.25 | cyan         | two pairs of parallelograms | hyperspeed trigger at f3/f4 |
| 10  | 2.50 | light purple | three pairs of parallelograms | hyperspeed trigger at f5 |
| 11  | 2.75 | white        | pair of white triangles added | |

### Hyperspeed

When the player's rank reaches 8/8/9/9/10 in the first five floors, hyperspeed is activated.  
Once activated there will be a flashy Bejeweled Twist-esque animation, alongside exclusive hyperspeed music.

A large display appears on the top of the screen showing floor splits and your pace compared to your PB Zenith Speedrun time.  
Reaching floor 10 with hyperspeed awards a hidden achievement, or when you fall to rank 6 or below hyperspeed disappears.

## Attack Target

You can't manually target someone in this mode, but the state of the player will impact the probability of yourself being attacked: `Targeting factor`  
The higher this value the likelier it is to be attacked, **with a starting value of 3**.

From additional observation, in most cases attacks are locked to players with similar altitude, specific calculations aren't clear

### Temporary decrease if in danger

Only in `easy modes`, check once every 0.25 seconds, if in danger (conditions not understood, probably when your board flashes red, shouldn't be off by a lot) `Targeting factor` temporarily decreases by 1.5, after leaving danger the 1.5 is added back

### Shift to Targeting grace (No impact on messiness)

There is a `Targeting grace` value, when attacked, lines*0.25 amount of `Targeting factor` gets moved to the targeting grace buffer slot (maximum 3, otherwise doesn't move), then gets moved back later.

When the buffer slot for `Targeting grace` is filled (hits 3), attack magnification decreases by 25% (continuous attacks all send 25% less garbage)

The `Targeting grace` value (linear) will decrease garbage messiness, when fully filled can cause `change between attacks -45%` and `change during attack -18%` 

If `Targeting grace` has a value, every set amount of time (depending on floor, see table below) 0.25 `Targeting grace` value is moved back to `Targeting factor`, meaning the higher the floor, the more the system allows others to attack with garbage lines rapidly.

### Gradual time increase (Caps at doubled past 7 minutes)

When time hits 3/5/7 minutes, `Targeting factor` +1

## Targeting grace

There is a `Targeting grace` variable, when attacked, increase the same amount of value as lines received (【Volatile+】's 3x isn't calculated), until caps at **18**
`Targeting grace`'s value decreases `garbage messiness`, although this system is blocked by these reasons: when time reaches 6 minutes in【Expert+】, 【Messier Garbage(+)】
If `Targeting grace`>0, then it will decrease by 1 a bit of time after “last moment of being attacked”, and refresh “last moment of being attacked” as the current moment, release gaps are shown below:

| Floor | Release every (seconds) | During【Expert+】|
| :-: | :-: | :-: |
| 1  | 4.8 | 1.0 |
| 2  | 3.9 | 0.9 |
| 3  | 2.1 | 0.8 |
| 4  | 1.4 | 0.7 |
| 5  | 1.3 | 0.6 |
| 6  | 0.9 | 0.5 |
| 7  | 0.6 | 0.4 |
| 8  | 0.4 | 0.3 |
| 9  | 0.3 | 0.2 |
| 10 | 0.2 | 0.1 |

`Targeting factor` alongside time/when rapidly filled/change when in danger:

| Time range | Factor | when full | when in danger |
| ----- | :-: | :-: | :-: |
| 0~2 minutes | 3 | -100% | -50% |
| 3~4 minutes | 4 | -75% | -75% |
| 5~6 minutes | 5 | -66% | -60% |
| past 7 minutes | 6 | -50% | -25% |

If `Targeting grace` is in use, every fixed amount of time (via table above), 0.25 `Targeting grace` gets moved back to `Targeting factor`, which means the higher the floor, the more the system allows other players to attack through garbage.

## Attack, All-Spin, B2B

Clearing 1, 2, 3 lines respectively send 0, 1, 2 attack

Limited to `easy modes`: “0 combo single 一 +1 attack”, making clearing 1 line also have 1 attack efficiency, can be considered under specific circumstances

Clearing 4 lines sends 4 attack, falls under `special clears` (increases B2B count, used in `Surge attack`, see next chapter for details)

This mode uses All-Mini+ spin rules, a subtype of `All-Spin`, other than T every other tetromino's Spins also count as `special clears` ((translation note: original says All-Mini but there's an update so it should be All-Mini+))  
Only T counts for a regular spin if it passes the 3-corner rule, with a base attack of `2*lines`, spins that don't fulfill 3-corner or non-T tetromino's that pass Immobile detection all count as Mini, with a base attack the same as normal clears, being `lines-1`

All Clears send 3 attack, but also count as +2 B2B (calculated separate from spins) (slightly different from regular TL, TL sends 5 attack but +1 B2B)

Consecutive `special clears` starting from the second one start gathering B2B count, and adds +1 attack

All attacks keep decimals in calculation, the decimals follow their value probability, for example 1.2 has a 20% chance to become 2, 80% chance to become 1 (Not sure if this rule is still in use)

### Surge Attack

When B2B is broken a large attack is created, attack is `B2B count -3`, (or the amount of consecutive special clears count -4) (slightly different in TL, however many B2B however many attack, no -3)

> This is a very important system in qp, really needed in certain situations

### Windup Attack

If a single attack with 8 or more lines is received (excluding Surge Attack), this attack will be split into multiple parts and have a warning hint before being received

> This trigger scenario is very likely inaccurate, needs research

Split method: Split the attack into several groups of 4 and the remaining portion (during【Volatile】changes to 8)

Warning method: 1 second before receiving this attack ! and !! etc. animations with sound are played, the warning corresponds to the amount of parts the attack is split into (for example Windup 4 corresponds to 4+4+4+n, aka 13~16 attack)  
1 second later the attacks start entering the garbage queue, each split is separated by 0.5s

## Garbage messiness

TETR.IO's garbage messiness system is decided by two numbers:  
“every line in the same attack has an X% chance to not stay on the same column”, “different attacks have a Y% chance to not stay on the same column” 

In TL X=0, Y=100%, which means the garbage lines in the same attack are always on the same column, and different attacks are always on different columns  
But in qp2 these two numbers aren't as extreme, meaning you'll feel the position of garbage holes aren't that related to the attacks in queue.

In qp2 the situation is Y=2.5*X, which means between received garbage attacks there's a higher chance (2.5 times) to be on a different column

The so called X in this page is `Garbage messiness`, which can be affected by various factors, specific changes shown below: 

| Element | Impact value |
| :-: | :-: |
| Floor | `Floor*3%`, in 【Expert(+)】`Floor*5%` |
| 【Expert(+)】 | +Floor*2% |
| 【Messy(+)】 | +25% (100%) |
| 【All-Spin+】 | +30% |
| 【Expert+】's 6 minute Fatigue `Full scatter` effect | =100% (calculations above can surpass 100%, this effect overwrites) |
| `Targeting grace` (calculated when finally spawns) | every point of `Targeting grace` decreases Y by 3.75%, X by 1.5% |

> When `Targeting grace` hits 18 points, Y is decreased by 67.5%, X by 27%  
> 真的没写反，这里挺奇怪的，可能需要拉个表格观察一下各种因素导致的混乱度变化  
> Genuinely didn't write out of order, quite strange here, ((translation work in progress sorry))  
> 吃了`全散`效果后两个值都被设为100%时反而在间断处更容易在同一列，很神奇  
> After receiving the `Full scatter` effect when both values are overwritten to 100%, ((work in progress))

## Garbage waiting time

When attacked, garbage lines will wait in queue before being activated: starting as transparent yellow, then transparent red, at last opaque red, of which if a piece is placed without clearing lines garbage enters through the board  
This waiting time is dependent on the floor and if Expert is enabled or not, for specific values see below:

| Floor |  Regular (Non-Expert)   |  【Expert(+)】   | 【Messy+】【Volatile+】【Double Hole+】 | Other【Mods+】 |
| :-: | :----------: | :---------: | :----: | :-----: |
|  1  | 2.50s (150f) | 1.1s (66f) | Same as regular Floor 6 | Same as regular Floor 6 |
|  2  | 2.25s (135f) | 1.0s (60f) | Same as regular Floor 6 | Same as regular Floor 6 |
|  3  | 2.00s (120f) | 0.9s (54f) | Same as regular Floor 6 | Same as regular Floor 6 |
|  4  | 1.75s (105f) | 0.8s (48f) | Same as regular Floor 6 | Same as regular Floor 6 |
|  5  | 1.50s (90f)  | 0.7s (42f) | Same as regular Floor 6 | Same as regular Floor 6 |
|  6  | 1.25s (75f)  | 0.6s (36f) | Same as regular Floor 6 | Same as regular Floor 6 |
|  7  | 1.00s (60f)  | 0.5s (30f) | Same as regular Floor 6 | Same as regular Floor `7` |
|  8  | 0.75s (45f)  | 0.4s (24f) | Same as regular Floor 6 | Same as regular Floor `8` |
|  9  | 0.50s (30f)  | 0.3s (18f) | Same as regular Floor 6 | Same as regular Floor `9` |
| 10  | 0.25s (15f)  | 0.2s (12f) | Same as regular Floor 6 | Same as regular Floor `10` |

> Note: Because garbage has to switch two times to be activated, in reality the waiting time is twice of what's shown above.  

## Fatigue

To prevent a game from being too long, starting from 8 minutes every minute adds another negative debuff, with a total of 5 debuffs:

| Time | Negative effect | Description |
| --- | --- | --- |
| 8 minutes | +2 permanent garbage | FATIGUE SETS IN… +2 PERMANENT LINES |
| 9 minutes  | +25% attack received | YOUR BODY GROWS WEAK… receive 25% more garbage |
| 10 minutes | +3 permanent garbage (total 5) | ALL SENSES BLUR TOGETHER… +3 PERMANENT LINES |
| 11 minutes | +25% attack received | YOUR CONSCIOUSNESS FADES… receive 25% more garbage |
| 12 minutes | +5 permanent garbage (total 10) | THIS IS THE END. +5 PERMANENT LINES |

> In【Expert+】fatigue effects are different, see later below for specifics

## Mods

This page defines not activating Expert Mod or any Mod+ as `Easy modes`  
All mods in this page are noted with【XX】format

Mods are ways you can increase the difficulty before starting a run, with basically only downsides and no upsides, but activating mods (or specific mod combinations) and reaching certain altitudes can grant achievements

There are a total of 9 mods, each corresponding with a special effect that can be individually toggled, with the setting having them as Tarot Cards, a description will be written after the mod name below, there will also be a table for convenience at the end of the chapter

((translation note: in the original readme "Garbage" in the names of "Messier Garbage, Volatile Garbage, Double Hole Garbage" are omitted but to reflect more accurately to that of in-game I'll temporarily keep them))
### Expert (The Emperor)

Each aspect gets slightly harder:

1. `Garbage messiness` is increased
1. Rising garbage animation is removed, instead spawns instantaneously (same as TL)
1. Removes system of decreasing `targeting factor` when in danger

### No Hold (Temperance)

Disables holding

### Messier Garbage (Wheel of Fortune)

`Garbage messiness` increases

### Gravity (The Tower)

Gravity noticeably increases  
Lock delay table for the ten floors (unit frames): 30, 29, 28, 27, 26, 24, 22, 20, 18, 16

### Volatile Garbage (Strength)

Garbage entering from the bottom is multiplied by 2x (The inner system is actually received garbage x2, and cancelling is also x2)

> This mod can speed up progress at the start, but poses too much of a threat in the endgame, whether its final effect is positive or negative is dependent on what type of play

### Double Hole Garbage (The Devil)

Every line of garbage has a chance to have two holes

### Invisible (The Hermit)

Pieces placed become invisible  
Every 5 seconds the whole board flashes which can be convenient for digging

### All-Spin (The Magician)

(See spin rules at the start) Upgrades non-T tetromino from mini spins into full spins, making them send lines*2 attack similarly to T-Spins

But the cost is when a player clears lines (Accurately it should be the text that appears on the left after hard dropping, non-line-clear spins count too), if the action text is the exact same, then a fully covered garbage line with a reverse tally counter of the floor number+5 appears at the bottom of the board as punishment, when the player does an unpunished line clear all tallies decrease by 1, upon reaching zero the punishment lines turn into a one-hole garbage line with the hole being in the same spot as the number previously was.

> Only mod that can give a more positive effect after the player reaeches a certain skill level

### Duo (The Lovers)

Players with supporter can invite others to play with themselves in this two-player mode  
To the perspective of one person, most output values will be halved, for example sent attacks and accumulated climb speed xp etc.

After both players die the game ends, but after one player dies the other player can do revive task(s) to revive their teammate, the tasks are divided into six grades ABCDEF, listed below

| Difficulty | code ID | value | name | tag type(?) | removed by mod |
| - | - | - | - | - | - |
| F | combo             | 3   | Perform a 3-Combo | 2 | |
| F | double            | 2   | Clear 2 Doubles | 2 | |
| F | quad              | 1   | Clear a Quad | 1 | |
| F | lines             | 6   | Clear 6 Lines | 1 | |
| F | odouble           | 1   | Clear a Double \n using an O-Piece | 3 | |
| F | garbageclear      | 4   | Clear 4 Garbage Lines | 2 | |
| F | szdouble          | 1   | Clear a Double \n using an S or Z-Piece | 3 | |
| F | ljtriple          | 1   | Clear a Triple \n using an L or J-Piece | 3 | |
| E | tspinmini         | 1   | Perform a T-Spin Mini | 1 | |
| E | tspinsingle       | 1   | Clear a T-Spin Single | 2 | |
| E | tspindouble       | 1   | Clear a T-Spin Double | 2 | |
| E | szspin            | 1   | Clear an S/Z-Spin | 1 | |
| E | ljspin            | 1   | Clear an L/J-Spin | 1 | |
| E | combo             | 5   | Perform a 5-Combo | 2 | |
| E | iflat             | 2   | Clear 2 Lines using \n horizontal I-Pieces | 3 | |
| E | tank              | 4   | Tank 4 Garbage Lines | 2 | |
| E | cancel            | 4   | Cancel 4 Garbage Lines | 2 | |
| D | double            | 4   | Clear 4 Doubles | 2 | |
| D | spam              | 3   | Place 3 pieces in a row \n without moving or rotating | 4 | |
| D | noclear           | 14  | Place 14 pieces in a row \n without clearing any lines | 4 | |
| D | send              | 6   | Send 6 Lines | 1 | |
| D | pieces            | 20  | Place 20 pieces | 2 | |
| D | szdouble          | 2   | Clear 2 Doubles \n using S or Z-Pieces | 3 | |
| D | ljtriple          | 2   | Clear 2 Triples \n using L or J-Pieces | 3 | |
| D | ispinclear        | 1   | Clear an I-Spin | 1 | |
| D | upperhalfquad     | 1   | Clear a Quad in the \n upper half of the board | 4 | |
| C | tspintriple       | 1   | Clear a T-Spin Triple | 2 | |
| C | nohold            | 25  | Place 25 pieces \n without using Hold | 3 | nohold |
| C | triple            | 3   | Clear 3 Triples | 2 | |
| C | b2b               | 4   | Reach B2B x4 | 1 | |
| C | quadbuckets       | 2   | Clear a Quad in \n 2 different columns | 3 | |
| C | holdconsecutive   | 12  | Use Hold on \n 15 pieces in a row | 3 | nohold |
| C | softdrop          | 10  | Place 10 pieces without \n releasing Soft Drop | 4 | |
| C | top3rows          | 3   | Have part of your stack in \n the top 3 rows for 3 seconds | 4 | |
| C | linesnoti         | 10  | Clear 10 Lines without \n clearing with T or I-pieces | 4 | |
| C | szspintriple      | 1   | Clear an S/Z-Spin Triple | 2 | |
| C | odoubleconsecutive| 2   | Clear 2 Doubles consecutively \n using two O-Pieces | 4 | |
| C | tspinminiclear    | 4   | Clear 4 T-Spin Minis | 2 | |
| B | oclear            | 6   | Clear 6 Lines \n using O-Pieces | 3 | |
| B | spinbuckets       | 3   | Clear Spin-Clears \n with 3 different pieces | 3 | |
| B | quad              | 4   | Clear 4 Quads | 1 | |
| B | spam              | 5   | Place 5 pieces in a row \n without moving or rotating | 4 | |
| B | send              | 18  | Send 18 Lines | 1 | |
| B | ljspintriple      | 1   | Clear an L/J-Spin Triple | 2 | |
| B | quadconsecutive   | 2   | Clear 2 Quads in a row | 2 | |
| B | singlesonly       | 8   | Clear 8 Singles without doing \n other clears or using Hold | 4 | |
| B | nogarbage         | 4   | Have no Garbage Lines on \n your board for 4 seconds | 4 | |
| B | rotate            | 100 | Rotate 100 times | 2 | |
| B | nocancel          | 8   | Don't cancel any \n garbage for 8 seconds | 3 | |
| A | combo             | 7   | Perform a 7-Combo | 2 | |
| A | ispindouble       | 1   | Clear an I-Spin Double | 2 | |
| A | szspinconsecutive | 2   | Clear two S/Z-Spin \n Doubles consecutively | 3 | |
| A | ljspinconsecutive | 2   | Clear two L/J-Spin \n Doubles consecutively | 3 | |
| A | colorclear        | 1   | Perform a Color Clear | 2 | |
| A | lines             | 40  | Clear 40 Lines | 1 | |

Grades F\~A correspond to a difficulty score of 1\~6, upon revival the difficulty of the tasks=`floor+revives*2` (try to split into three whole numbers), a detailed table is listed below:
1. F
1. F F
1. F F F
1. F F E
1. F E E
1. E E E
1. E E D
1. E D D
1. D D D
1. D D C
1. D C C
1. C C C
1. C C B
1. C B B
1. B B B
1. B B A
1. B A A
1. A A A (Upper bound)

((translation note: the difficulty orders aren't exact, for example score 7 can be E D E or D E E too, it doesn't necessarily have to be E E D))

## Mod+

Every mod has a corresponding buffed mod (except for Duos), needing 30,000 meters climbed with the mod to unlock (activating multiple mods can accumulate for them at the same time)

    If you want to unlock all buffed mods as quick as possible it's recommended to activate multiple at the same time, below is a reference strategy (if you can smoothly get a few f10 with all of the mods individually)  
    `【Gravity】+【Messy】+【Double Hole】+【AllSpin】` activate these four and rely on allspin's fierce output, try not to let garbage lines enter, finish 30,000 meters. If you can use brainless Blitz mode looping and aren't afraid of `【Invisible】` you can bring it too, otherwise it 
    later needs to be cleared by itself  
    Afterwards activate `【Invisible】+【Volatile】` and `【No Hold】+【Volatile】`, notice try to tank more garbage then use Quad to dig to climb faster (because cancelling garbage lines has a worse result), at the same time try to calculate total efficiency with and without `Expert` 
    (altitude/time, multiply by 2 with Expert) to decide whether or not to accumulate for Expert incidentally, if possible then bring it, otherwise later on it needs to be cleared by itself  
    Last is `【Expert】+【Volatile】`, being individually played because this mod will substantially decrease climbing efficiency, and put last because it could already have some progress made at the start 

Introduction to effects that will appear later:

1. `Starting protection`: Only in Mods with garbage lines at the start, when cleaning the last 5 garbage lines on the board, every line will increase `Targeting factor` by 0.5, total of 2.5 (Mods with this condition are estimated to have this starting value lowered, and then uses this type of method to progressively return to normal)
   
All buffed mods can only be played solo, and cannot be stacked on other mods

### Expert+ (The Tyrant)

> Fear, oppression, and limitless ambition.

On top of the original many limits,

Climb speed no longer gains altitude over time, sending attack and KOs are required to receive height

Descent: Altitude decreases over time, although it gets blocked by each floor's borderline and therefore can't go down to the previous floor

| Floor | Descent speed | Corresponding rank and spm |
| :-: | :---: | :---------: |
|  1 (0m)    | 0.6 m/s | 3 & 48spm |
|  2 (50m)   | 0.8 m/s | 4 & 48spm |
|  3 (150m)  | 1.1 m/s | 4 & 66spm |
|  4 (300m)  | 1.5 m/s | 5 & 72spm |
|  5 (450m)  | 2.0 m/s | 5 & 96spm |
|  6 (650m)  | 2.6 m/s | 6 & 104spm |
|  7 (850m)  | 3.3 m/s | 6 & 132spm |
|  8 (1100m) | 4.1 m/s | 6 & 164spm |
|  9 (1350m) | 5.0 m/s | 7 & 171spm |
| 10 (1650m) | 6.0 m/s | 7 & 206spm |

> Descent speed formula is `(floor^2+floor+10)/20`  
> rank and spm are only for reference, in reality cancelling doesn't count for spm so it can't be achieved, after the fifth-sixth floor you have to rely on 3-digit surge APM to continue climbing  ((translation note: SPM = sent per minute))
> During gameplay descent looks like it has acceleration, but it's only a visual effect, in reality it's still even

Fatigue system becomes even more harsh:

| Time | Negative effect | Text description |
| --- | --- | --- |
| 6 minutes | garbage becomes messier (disables `Targeting grace` effect) | YOUR POWER SLIPS… garbage received becomes messier |
| 7 minutes | +25% attack received | WHISPERS OF DISCONTENT SPREAD… receive 25% more garbage |
| 8 minutes | +3 permanent garbage | PROTESTERS LINE THE STREETS… +3 PERMANENT LINES |
| 9 minutes | +25% attack received | YOUR CLOSEST ALLIES DEFECT… receive 25% more garbage |
| 10 minutes | +5 permanent garbage (total 8) | PARANOIA CLOUDS YOUR JUDGEMENT… +5 PERMANENT LINES |
| 11 minutes | garbage becomes noticeably messier (receive `full scatter` effect) | THE REVOLUTION HAS BEGUN… garbage received becomes much messier |
| 12 minutes | +12 permanent garbage (total 20) | THE END OF AN ERA. +12 PERMANENT LINES |

After staying in the same floor for over 60 seconds, every second you permanently gain 0.5% multiplier of being attacked (for example 200 seconds after the effect starts all incoming attacks are doubled)

`Targeting grace` releases faster (see `Targeting grace` related chapter for specifics)

Base KO bonus altitude decreases from 15m to 8m

### No Hold+ (Asceticism)

> A detachment from even that which is moderate.

On top the original basis of no hold,  
1 piece preview  
No piece shadow  
Completely random generation (eyeballed, should be right though)  
Spins all count as Mini (base attack of `lines-1`)  
Garbage hole styles become 2-wide

### Messier Garbage+ (Loaded Dice)

> In a rigged game, your mind is the only fair advantage.

`Garbage messiness` increased 
Line clear delay increases from 0 to 1 second ((translation note: it seems like it's actually 1.15s))  
The starting board state becomes a fixed pattern of six circles:

    ..........
    .XXX..XXX.
    .X.X..X.X.
    .XXX..XXX.
    ..........
    Three layers, doesn't touch the walls, looks like Mahjong's six dots

has `Starting protection`

### Gravity (Freefall)

> The ground you stood on never existed in the first place.

20G from the start  
Lock delay table for the ten floors: 24, 22, 20, 18, 16, 15, 14, 13, 12, 11

### Volatile Garbage+ (Last Stand)

> Strength isn't necessary for those with nothing to lose.

Received attack multiplier becomes 3x (notice: cancelling multiplier isn't changed)
14 high playfield  
Garbage hole positions have two warnings  
garbagefavor's value is locked to 50 (detailed calculations aren't known, garbage being extra clean is probably due to this)

### Double Hole Garbage+ (Damnation)

> No more second chances.

The starting board state becomes 12-row checkerboard garbage lines    
Garbage lines become messy garbage lines with 3~4 grey blocks randomly  
Can't cancel garbage lines (though you also don't receive much)  
has `Starting protection`  
((translation note: garbage cap is reduced to 2 as well, and apparently incoming garbage isx0.5))

### Invisible+ (The Exile)

> Never underestimate blind faith.

On top the original basis of invisibility,   
The board doesn't flash anymore  
Only the top three garbage lines are visible  
Receive 3 lines of garbage at the start by the system

### All-Spin+ (The Warlock)

> Into realms beyond heaven and earth.

On top the original basis of consecutive clear penalties,    
Penalties become 20 lines of filled garbage (instant death) ((translation note: it is technically survivable but really hard because the piece spawns at rows 22-23))  
At the same time non-spin line clears are all viewed as Single (clearing 2 lines then clearing 4 lines, counts as two Singles, death)  
Receive 10 lines of garbage at the start by the system  
`Garbage messiness` increased
has `Starting protection`

## Tarot Card basic summary

| Upright name | Effect summary | Reversed name | Effect summary (includes upright effects) |
| ---: | :---: | ---: | :---: |
| The Emperor | less room for error + harder to climb | The Tyrant | extremely hard to climb + descent + super fatigue |
| Temperance | no holding | Asceticism | 1 preview + random + 2 holes |
| Wheel of Fortune | messier garbage | Loaded Dice | 1.15s lock delay + pattern start |
| The Tower | higher gravity + decreased lock delay | Freefall | 20G low lock delay |
| Strength | double garbage + double cancel | Last Stand | 3x garbage + normal cancel + low board |
| The Devil | double hole garbage | Damnation | debris garbage lines + checkerboard start |
| The Hermit | invisible + 5 second flash | The Exile | no more flashing + can't see all garbage |
| The Magician | no mini + penalize repeats | The Warlock | sudden death + non-spins count as Single + cheese start |
| The Lovers | two players | | |

## Extra notes

In all fatigue systems `+X% received attack` will be correspondingly increased to 2 (3) times due to 【Volatile(+)】, which is similar to multiplication  
((work in progress))

## Some unsure if useful technological bonus information

If you want to search for variables, here are some integer names below:

1. `Targeting factor` targetingfactor
1. `Targeting grace` targetinggrace
1. `Mods` zenith_[modname]
1. `Reverse mods` [modname]_reverse
1. `Change between attacks` messiness_change
1. `Change during attack` messiness_inner
1. `garbage lines' ???` garbagefavor
1. `garbage waiting time` garbagephase

```js
    /*
        Source code is from 2025.01.19 veresion, estimated to be the js after ts edited so it's definitely confusing, the code below is reference code modified from the source
        Deleted some unnecessary (嗯嗯嗯 欸嘿) content, added various descriptions
        “MOD_” is a simplification for convenience when reading, in the original code it's “this.S.setoptions.zenith_”,
        or “"xxxxxx_reversed" === this.S.setoptions.zenith_mods[0]”
    */

    // Some common tables
    FloorDistance = [0, 50, 150, 300, 450, 650, 850, 1100, 1350, 1650, 1 / 0];
    GravityBumps = [0, .48, .3, .3, .3, .3, .3, .3, .3, .3, .3];
    GravLockDelay = [0, 30, 29, 28, 27, 26, 24, 22, 20, 18, 16];
    GravRevLockDelay = [0, 24, 22, 20, 18, 16, 15, 14, 13, 12, 11];
    SpeedrunReq = [7, 8, 8, 9, 9, 10, 0, 0, 0, 0, 0]; // First element is the minimum rank to not exit
    TargetingGrace = [0, 4.8, 3.9, 2.1, 1.4, 1.3, .9, .6, .4, .3, .2];
    TargetingGraceRevEx = [0, 1, .9, .8, .7, .6, .5, .4, .3, .2, .1];
    RevNoHoldHoleSideChangeChance = [.1, .1, .15, .2, .25, .3, .35, .4, .45, .5, .55];
    GetSpeedCap(frame) {
        const t = this.FloorDistance.find((t => frame < t)) - frame;
        return Math.max(0, Math.min(1, t / 5 - .2))
    }

    // Main loop
    Loop() {
        const frame = this.self.esm.frame;
        let rank = Math.floor(this.S.stats.zenith.rank);
        const height0 = this.S.stats.zenith.altitude; // 记录用于卡楼层的高度 ((wip))

        // xp loss
        if (frame >= this.S.zenith.rank_locked_until) {
            let leakSpeed = ...; // Solo: Normal3 Expert5  Duos:3+players with expert
            this.S.zenith.climb_pts -= leakSpeed * (rank ** 2 + rank) / 3600 // climb_pts is current xp
        }

        const nextRankXP = 4 * rank;
        const storedXP = 4 * (rank - 1);
        if (this.S.zenith.climb_pts < 0)
            // Demotion
            if (rank <= 1)
                // won't fall to under rank 0
                this.S.zenith.climb_pts = 0;
            else {
                // 恢复计算总xp ((wip))
                this.S.zenith.climb_pts += storedXP;
                this.S.zenith.last_rank_change_was_promote = false;
                rank--;
            }
        else if (this.S.zenith.climb_pts >= nextRankXP) 
            // 清空xp升1级
            this.S.zenith.climb_pts -= nextRankXP; 
            this.S.zenith.last_rank_change_was_promote = true;
            this.S.zenith.rank_locked_until = frame + Math.max(60, 60 * (5 - this.S.zenith.promotion_fatigue));
            this.S.zenith.promotion_fatigue++;
            rank++;
        }

        // xp在5秒内不自然流失效果 ((wip))
        if (this.S.zenith.last_rank_change_was_promote && this.S.zenith.climb_pts >= 2 * (rank - 1))
            this.S.zenith.promotion_fatigue = 0;

        // 跳级！如果升级后还有大量剩余的话 ((wip))
        this.S.stats.zenith.rank = rank + this.S.zenith.climb_pts / (4 * rank);

        // Some statistics
        this.S.stats.zenith.peakrank = Math.max(this.S.stats.zenith.rank, this.S.stats.zenith.peakrank);
        this.S.stats.zenith.avgrankpts += this.S.stats.zenith.rank;

        const o = this.S.stats.zenith.altitude;
        const floor = me.GetFloorLevel(o);

        if (MOD_expertRev) {
            // 【Expert+】's downfalling
            this.S.stats.zenith.altitude = Math.max(me.FloorDistance[floor - 1], o - .05 * (floor ** 2 + floor + 10) / 60);
        } else {
            // Climb Speed gaining altitude over time
            this.S.stats.zenith.altitude += .25 * rank / 60 * me.GetSpeedCap(o);
        }

        // Linear altitude change
        if (this.S.zenith.bonusremaining > 0)
            if (this.S.zenith.bonusremaining <= .05) {
                this.S.stats.zenith.altitude += this.S.zenith.bonusremaining;
                this.S.zenith.bonusremaining = 0;
            }
            else {
                const delta = Math.min(10, .1 * this.S.zenith.bonusremaining);
                this.S.stats.zenith.altitude += delta;
                this.S.zenith.bonusremaining -= delta;
            }

        // 不让用“推进器随时间爬升”途径上楼 ((wip))
        this.S.setoptions.zenith_tutorial && this.S.stats.zenith.altitude >= 50 &&
        this.S.zenith.tutorial.stage > 0 && this.S.zenith.tutorial.stage < 5 && (
            this.S.stats.zenith.altitude = Math.min(49.99, height0);
            this.S.zenith.bonusremaining = 0;
        )

        // 【Gravity(+)】
        floor !== this.S.stats.zenith.floor && (
            MOD_gravity ? (this.S.g += me.GravityBumps[floor], this.S.setoptions.locktime = me.GLockDelay[floor]) : MOD_gravityRev && (this.S.g = 20, this.S.setoptions.locktime = me.GRLockDelay[floor]), this.S.zenith.lastfloorchange = frame, 1 === floor ? this.S.glock = 240 : this.S.stats.zenith.splits[floor - 2] = Math.round(this.self.lm.GetGameTime())
        )
        this.S.stats.zenith.floor = floor

        // 【Expert+】's overtime penalty
        if (MOD_expertRev && frame - this.S.zenith.lastfloorchange > 3600)
            this.S.setoptions.receivemultiplier += .005 / 60;

        // Don't know what this is
        if (this.S.TEMP_zenith_apm_cycle) {
            if (this.S.TEMP_zenith_apm_cycle += this.S.TEMP_zenith_apm / 3600 / 2.5 * (.75 + .5 * this.S.rngex.nextFloat()), this.S.TEMP_zenith_apm_cycle >= 1) {
                this.S.TEMP_zenith_apm_cycle--;
                this.self.atm.FightLines(this.S.rngex.nextFloat() >= .5 ? 4 : 1);
            }
        }

        // Some systems' instant death, estimated to be used for【All-Spin+】
        if (this.self.atm.GetPendingGarbageCount() >= this.S.TEMP_zenith_instakill_at)
            this.self.gom.GameOver("garbagesmash");

        // Targeting factor increase on 3/5/7 minutes
        if (frame===10800 || frame===18000 || frame===25200)
            this.S.stats.zenith.targetingfactor++;

        // Release targeting grace
        let r = 60 * (MOD_expertRev ? TargetingGrace : TargetingGraceRevEx)[floor];
        if (this.S.stats.zenith.targetinggrace > 0 && frame >= this.S.lastatktime + r) {
            this.S.stats.zenith.targetinggrace--;
            this.S.lastatktime = frame;
        }

        // 刷新混乱度
        const messy = (MOD_expert ? .05 : .03) * floor;
        if (MOD_messy) messy += .25;
        if (MOD_messyRev) messy += 1;
        if (MOD_allspinRev) messy += .3;
        this.S.setoptions.messiness_inner = messy;
        this.S.setoptions.messiness_change = 2.5 * messy;
        if (this.S.zenith.maxmessy) {
            this.S.setoptions.messiness_change = 1;
            this.S.setoptions.messiness_inner = 1;
        }

        // Garbage favor??? Temporarily don't know how this is specifically used
        this.S.setoptions.garbagefavor = MOD_volatileRev ? 50 : (MOD_expert ? 0 : 33) - 3 * floor - (MOD_messy ? 25 : 0);

        // Garbage waiting time
        this.S.setoptions.garbagephase = MOD_expert ? 66 - 6 * floor : 165 - 15 * floor;
        if (MOD_anyRev && !MOD_expert)
            this.S.setoptions.garbagephase = (MOD_messyRev || MOD_volatileRev || MOD_doubleholeRev) ? 75 : [75, 75, 75, 75, 75, 75, 75, 60, 45, 30, 15][floor];

        // 随着消除垃圾行逐渐关闭开局保护 ((wip))
        if (frame % 15 == 0 && (MOD_messyRev || MOD_doubleholeRev || MOD_allspinRev)) {
            const line = this.self.bm.CountGarbageLinesNoPerma();
            if (line !== this.S.zenith.garbagerowcount) {
                const t = Math.max(0, 2.5 - .5 * this.S.zenith.garbagerowcount);
                const n = Math.max(0, 2.5 - .5 * line);
                this.S.stats.zenith.targetingfactor += n - t;
                this.S.zenith.garbagerowcount = line;
            }
        }
    }
```
