# Translation of TETR.IO qp2 rules observance summary By MrZ_26

## Start

This mode doesn't have a global "round", everyone can enter at any time without waiting

## QP2

This mode's theme is climbing `Zenith Tower`, your final score is your `Altitude`.

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

At climb speed 1 the multiplier is ×0.25, every increase in climb speed level adds another ×0.25 (Upon reaching ×2.75 it becomes white with no further difference for higher climb speed, but in reality there's no upper limit).

### Gaining altitude & XP

The methods of gaining altitude and xp are listed below:

| Action | Effect |
| - | - |
| Time | Every second 1m, but when you're 6m~1m below next floor, the speed of altitude gain over time evenly decreases from ×1 to ×0, you have to use other methods to reach the next floor. |
| KO | 15m ("Expert+" becomes 8m) |
| Sending attack | Every line of attack 1m and 1.05xp |
| Cancelling garbage lines | （Non-Expert）0.55xp |
| Clearing lines | （Non-Expert）One line 1.05xp, Two lines or above 2.05xp |

> Note that all altitude gain is impacted by your `rank`, specifically multiply by 4 `*rank/4` when calculating, for example at the start the multiplier is ×0.25, meaning you gain 1m every 4 seconds.

The xp required to reach the next climb speed level is `4*rank`. Once your xp meets the conditions your climb speed increases by one and your xp decreases by the amount that was previously required (if you overshoot the remaining xp is kept).

Once you have promoted to the next climb speed level, for 5 seconds xp will stop naturally decreasing (see xp loss chapter for details) to prevent instantly demoting right after.

There is also a `promotion fatigue` system: Every time you increase a climb speed level, the `no natural xp decrease for 5 seconds` from the previous line becomes a second shorter (until 1 second), meaning repeatedly promoting/demoting causes the effect to be weaker. To reset it back to 5 seconds you have to reach 50% of the next climb speed level (middle of the experience bar).

### Skipping levels

Every time you increase a climb speed level, if the xp afterwards is enough to increase another climb speed level, then you gain an extra `xp/required xp` amount of climb speed level, and **xp is not removed**

Which means this situation can happen:

    One frame - B2B breaks causing huge spike and XP increase
    Next frame - Gain multiple climb speed levels 
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

Below are some useful statistics for convenience:

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

| rank | multiplier | color | shape | hyperspeed notes |
| :-: | :--: | :-: | - | - |
|  1  | 0.25 | none         | a progress bar | |
|  2  | 0.50 | red          | add a triangle below | |
|  3  | 0.75 | orange       | add wings to triangle | |
|  4  | 1.00 | yellow-green | wings increase size | |
|  5  | 1.25 | blue         | wings increase size + add base | |
|  6  | 1.50 | magenta      | wings extend to full size | |
|  7  | 1.75 | light orange | wings become detailed | lowest rank without exiting hyperspeed |
|  8  | 2.00 | turquoise    | add pair of parallelograms to progress bar | hyperspeed trigger at f1/f2 |
|  9  | 2.25 | cyan         | two pairs of parallelograms | hyperspeed trigger at f3/f4 |
| 10  | 2.50 | light purple | three pairs of parallelograms | hyperspeed trigger at f5 |
| 11  | 2.75 | white        | add pair of white triangles | |

### Hyperspeed

When the player's rank reaches 8/8/9/9/10 in the first five floors, hyperspeed is activated.

Once activated there will be a flashy Bejeweled Twist-esque animation, alongside exclusive hyperspeed music.

A large display appears on the top of the screen showing floor splits and your pace compared to your PB Zenith Speedrun time.

Reaching floor 10 with hyperspeed awards a hidden achievement, or when you fall to rank 6 or below hyperspeed disappears.

## Attack Target

You can't manually target someone in this mode, but the state of the player will impact the probability of yourself being attacked: `Targeting factor`

The higher this value the likelier it is to be attacked, **with a starting value of 3**.

From additional inspection, in most cases attacks are locked to players with similar altitude, specific calculations aren't clear

### Gradual time increase (Caps at doubled past 7 minutes)

When time hits 3/5/7 minutes, `Targeting factor`+1

### Temporary decrease if in danger (No impact on messiness)

Only in Non-Expert, check once every 0.25 seconds, if in danger (conditions not understood, probably when your board flashes red, shouldn't be off by a lot) `Targeting factor` temporarily decreases by 1.5, after leaving danger the 1.5 is added back

### Shift to Targeting grace (No impact on messiness)

There is a `Targeting grace` value, when attacked, lines*0.25 amount of `Targeting factor` gets moved to the targeting grace buffer slot (Maximum 3, otherwise doesn't move), then gets moved back later.

When the buffer slot for `Targeting grace` is filled (hits 3), attack magnification decreases by 25% (continuous attacks all send 25% less garbage)

The `Targeting grace` value (linear) will decrease garbage messiness, when filled can cause `change between attacks -45%` and `change during attack -18%` 

If `Targeting grace` has a value, every set amount of time (depending on floor, see table below) 0.25 `Targeting grace` value is moved back to `Targeting factor`, meaning the higher the floor, the more the system allows others to attack with garbage lines rapidly.


### Related tables

`Targeting factor` alongside time/when rapidly filled/change when in danger:

| time range | factor | when full | when in danger |
| ----- | :-: | :-: | :-: |
| 0~2 minutes | 3 | -100% | -50% |
| 3~4 minutes | 4 | -75% | -75% |
| 5~6 minutes | 5 | -66% | -60% |
| past 7 minutes | 6 | -50% | -25% |

`Targeting factor` release time:

| floor | release time (seconds) | highest consistent received APM |
| :---: | :---: | :---: |
| 1 | 4.8 | 12.5 |
| 2 | 3.9 | 15.4 |
| 3 | 2.1 | 28.6 |
| 4 | 1.4 | 42.9 |
| 5 | 1.3 | 46.1 |
| 6 | 0.9 | 66.7 |
| 7 | 0.6 | 100 |
| 8 | 0.4 | 150 |
| 9 | 0.3 | 200 |
| 10 | 0.2 | 300 |

> Notice `highest consistent received APM` above isn't a real statistic, therefore it can't be compared with regular APM, and has low reference value

If `Targeting grace` is in use, every fixed amount of time (via table above), 0.25 `Targeting grace` gets moved back to `Targeting factor`, which means the higher the floor, the more the system allows other players to attack through garbage.


## Attack, All-spin, B2B

Clearing 1, 2, 3 lines respectively send 0, 1, 2 attack (Note: in Non-Expert 0 combo singles send 1 line, making a 1 line : 1 attack ratio possible, can be considerable in specific cases)

Clearing 4 lines sends 4 attack, falls under `Special clears`

This mode uses All-Mini spin rules, spin clears of every tetromino are `Special clears`, they can increase B2B count (With only T being a regular spin if 3-corner rule is passed, if 3-corner rule isn't passed or if it's a non-T tetromino then as long as it's immobile then it counts as Mini, with same attack as regular line clears, clear 1/2/3 send 0/1/2)

All Clears send 3 attack, but also count as +2 B2B (calculated separate from spins) (slightly different from regular TL, TL sends 5 attack but +1 B2B)

B2B starts counting from the second `Special clear`, and adds an extra 1 attack sent

delete: Though there is another surge counter off B2B, when B2B is broken it sends a spike (B2B count -3, or amount of special clears -4)

All attacks keep decimals in calculation, the decimals follow their value probability, for example 1.2 has a 20% chance to become 2, 80% chance to become 1)

### Surge Attack

When B2B is broken a large attack is created, 

## Garbage hole positions

This mode's garbage lines don't follow attack structure, only the total amount of lines

TETR.IO's garbage messiness system is decided by two numbers:

“every line in the same attack has an X% chance to stay on the same column”, “different attacks have a Y% chance to stay on the same column” 

In TL X=100%, Y=0%, which means the garbage lines in an attack are always on the same column, and different attacks are always on different columns

But in qp2 these two numbers aren't as extreme, meaning you'll feel the position of garbage holes aren't that related to the attacks in queue.

`Expert` and `Messier Garbage` mods both increase garbage messiness

`Targeting grace` value decreases garbage messiness, see attack target chapter for more detail

> Note: The variable names in the code are messiness_change and messiness_inner

## Garbage waiting time

When attacked, garbage lines will wait in queue before being activated: starting as transparent yellow, then transparent red, at last opaque red, of which if a piece is placed without clearing lines garbage enters through the board.  

this waiting time is dependent on the floor and if Expert is enabled or not, for specific values see below:

| Floor |  Non-Expert  |   Expert   |
| :-: | :----------: | :---------: |
|  1  | 2.50s (150f) | 1.1s (66f) |
|  2  | 2.25s (135f) | 1.0s (60f) |
|  3  | 2.00s (120f) | 0.9s (54f) |
|  4  | 1.75s (105f) | 0.8s (48f) |
|  5  | 1.50s (90f)  | 0.7s (42f) |
|  6  | 1.25s (75f)  | 0.6s (36f) |
|  7  | 1.00s (60f)  | 0.5s (30f) |
|  8  | 0.75s (45f)  | 0.4s (24f) |
|  9  | 0.50s (30f)  | 0.3s (18f) |
| 10  | 0.25s (15f)  | 0.2s (12f) |

> Note 1: Because garbage has to switch two times to be activated, in reality the waiting time is twice of what's shown above.
> 
> Note 2: The variable name in the code is garbagephase

## Fatigue

To prevent a game from being too long, from 8 minutes every minute adds another negative debuff, with a total of 5 debuffs:


| Time | Negative effect | Description |
| --- | --- | --- |
| 8 minutes | +2 permanent garbage | FATIGUE SETS IN… +2 PERMANENT LINES |
| 9 minutes  | +25% attack received | YOUR BODY GROWS WEAK… receive 25% more garbage |
| 10 minutes | +3 permanent garbage | ALL SENSES BLUR TOGETHER… +3 PERMANENT LINES |
| 11 minutes | +25% attack received | YOUR CONSCIOUSNESS FADES… receive 25% more garbage |
| 12 minutes | +5 permanent garbage | THIS IS THE END. +5 PERMANENT LINES |

## Mods

Mod是在遊戲開始前可選的主動增加遊戲難度的方式，基本上只有壞處沒有好處，但是開啟Mod（或特定的Mod組合）後爬到特定高度可以獲得成就
Mods are ways you can increase the difficulty before starting a run, with basically only downsides and no upsides, but activating mods (or specific mod combinations) and reaching certain altitudes can grant achievements

Mod總共有9個，每個都對應一個特殊效果可以獨立開關，在背景設定中呈現為塔羅牌，下文會在每個Mod的名稱後註明，章節最後也有一個表格用於速查
There are a total of 9 mods, each corresponding with a special effect that can be individually toggled, with the setting having them as Tarot Cards, a description will be written after the mod name below, there will also be a table for convenience at the end of the chapter

### Expert (The Emperor)

Each aspect gets slightly harder:

1. Garbage enters instantaneously, rather than consecutively going up line by line
1. Garbage messiness is increased
1. Removes system of decreasing `targeting factor` when in danger

### No Hold (Temperance)

Disables holding

### Messier Garbage (Wheel of Fortune)

Garbage messiness noticeably increases

### Gravity (The Tower)

Gravity noticeably increases

Lock delay table for the ten floors: 30, 29, 28, 27, 26, 24, 22, 20, 18, 16

### Volatile Garbage (Strength)

Garbage entering from the bottom is multiplied by 2x (The inner system is actually received garbage x2, and cancelling is also x2)

> This mod can speed up progress at the start, but poses too much of a threat in the endgame, whether its final effect is positive or negative is dependent on what type of play

### Double Hole Garbage (The Devil)

Every line of garbage has a chance to have two holes

### Invisible (The Hermit)

Pieces placed becomes invisible

Every 5 seconds the whole board flashes which can be convenient for digging

### All-Spin (The Magician)

(See spin rules at the start) Upgrades non-T tetromino from mini spins into full spins, making them send lines*2 attack similarly to T-Spins

But the cost is when a player clears lines (Accurately it should be the text that appears on the left after hard dropping, non-line-clear spins count too), if the action text is the exact same, then a fully covered garbage line with a reverse tally counter of the floor number+5 appears at the bottom of the board as punishment, when the player does an unpunished line clear all tallies decrease by 1, upon reaching zero the punishment lines turn into a one-hole garbage line with the hole being in the same spot as the number previously was.

> Only mod that can give a more positive effect after the player reaeches a certain skill level

### Duo (The Lovers)

Players with supporter can invite others to play with themselves in this two-player mode

To one of the people, most output values will be halved, for example sent attacks and accumulated climb speed xp etc.

After both players die the game ends, but after one player dies the other player can do revive task(s) to revive their teammate, the tasks are divided into six grades ABCDEF, listed below

| difficulty | code id | value | name | tag type(?) | removed by mod |
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

{Translator note: the difficulty orders aren't exact, for example score 7 can be E D E or D E E too, it doesn't necessarily have to be E E D}

## Mod+

Every mod has a corresponding buffed mod (except for Duos), requiring accumulating 

## Some unsure if useful bonus content


```js
    // Common tables
    FloorDistance - [0, 50, 150, 300, 450, 650, 850, 1100, 1350, 1650, 1 / 0];
    TargetingGrace - [0, 4.8, 3.9, 2.1, 1.4, 1.3, .9, .6, .4, .3, .2];
    GravityBumps = [0, .48, .3, .3, .3, .3, .3, .3, .3, .3, .3];
    LockTimes = [0, 30, 29, 28, 27, 26, 24, 22, 20, 18, 16];
    SpeedrunReq = [7, 8, 8, 9, 9, 10, 0, 0, 0, 0, 0];
    GetSpeedCap(e) {
        const t = this.FloorDistance.find((t => e < t)) - e;
        return Math.max(0, Math.min(1, t / 5 - .2))
    }

    // Release targeting grace
    const cooldownDuration = 60 * se.TargetingGrace[l];
    if (this.S.stats.zenith.targetinggrace > 0 && e >= this.S.lastatktime + cooldownDuration) {
        if (this.S.stats.zenith.targetinggrace >= 3) {
            this.S.setoptions.receivemultiplier += this.S.setoptions.zenith_volatile ? 0.5 : 0.25;
        }
        this.S.stats.zenith.targetingfactor += 0.25;
        this.S.stats.zenith.targetinggrace -= 0.25;
        this.S.lastatktime = e;
    }

    const expertBonus = this.S.setoptions.zenith_expert ? 0.05 : 0.03;
    const messyBonus = this.S.setoptions.zenith_messy ? 0.25 : 0;
    const messinessIncrease = 2.5 * (expertBonus + messyBonus);
    this.S.setoptions.messiness_change = messinessIncrease;
    this.S.setoptions.messiness_inner = expertBonus + messyBonus;
    this.S.setoptions.garbagefavor = (this.S.setoptions.zenith_expert ? 0 : 33) - 3 * l - (this.S.setoptions.zenith_messy ? 25 : 0);
    this.S.setoptions.garbagephase = this.S.setoptions.zenith_expert ? 66 - 6 * l : 165 - 15 * l;
```
