# Translation of TETR.IO qp2 rules observance summary By MrZ_26

This page's `【XX】` is the format for mods, for specifics see the Mods chapter

## Start

This mode doesn't have a global "round", everyone can enter at any time without waiting

## QP2

This mode's theme is climbing `Zenith Tower`, the final score is your `Altitude`.

Upon reaching a certain altitude you will proceed to the next floor

| Floor | Altitude Range | Name |
| - | - | :-: |
| Floor 1 | 0m - 50m | Hall of Beginnings |
| Floor 2 | 50m - 150m | The Hotel |
| Floor 3 | 150m - 300m | The Casino |
| Floor 4 | 300m - 450m | The Arena |
| Floor 5 | 450m - 650m | The Museum |
| Floor 6 | 650m - 850m | Abandoned Offices |
| Floor 7 | 850m - 1100m | The Laboratory |
| Floor 8 | 1100m - 1350m | The Core |
| Floor 9 | 1350m - 1650m | Corruption |
| Floor 10 | 1650m+ | Platform of The Gods |

## Climb Speed

`Climb Speed` (called `rank` in the code) affects how fast you gain altitude, every action that increases altitude is impacted by its' multiplier bonus. Increasing climb speed requires experience (called `xp` hereafter).

At climb speed 1 the multiplier is ×0.25, every increase in climb speed level adds another ×0.25 (Upon reaching ×2.75 it becomes white with no further difference, but in reality there's no upper limit).

### Gaining altitude & XP, and promoting

| Action | Altitude | xp | Specialty |
| :--: | :--: | :--: | :--: |
| Natural increase | Every second 1m | `xp loss`, see below | Will get `stuck`, slowly becomes 0 when 6m~1m away from next floor |
| KO | `15m` | | `8m` in【Expert+】|
| Sending attack | `lines`m | `lines+0.05`xp | |
| Cancelling garbage | | `lines/2+0.05`xp | In【Expert(+)】or【Volatile+】considered as 0 lines |
| Clearing lines | | `min(lines,2)+0.05`xp | None in【Expert(+)】|
| Past 3 actions above when `stuck` | 3m | | In reality occurs when 2m away from the next floor |

> Altitude gain above excluding the +3m when stuck are all affected by your `rank`, for example at the start `rank` is 1, multiplier is ×0.25, every 4 seconds gain 1m

When gaining altitude, the newly increased altitude will first be stored into a temporary variable, every frame release 10%, at maximum 10m 

The `xp` required to reach the next climb speed level is `4*rank`. once your `xp` meets the conditions your climb speed increases by one and your `xp` decreases by the amount that was previously required.  
Once you have promoted to the next climb speed level, for 5 seconds `xp` will stop naturally decreasing (see `xp` loss chapter for details) to prevent having very little xp after promotion thus instantly demoting right after.

There is also a `promotion fatigue` system: Every time you increase a climb speed level, the `no natural xp decrease for 5 seconds` from the previous section becomes a second shorter (until 1 second), meaning repeatedly promoting/demoting causes the effect to be weaker. To reset it back to 5 seconds you have to reach 50% of the next climb speed level (middle of the experience progress bar).

### Skipping levels

Every time you increase a climb speed level, if the xp afterwards is enough to increase another climb speed level, then you gain an extra `xp/required xp` amount of climb speed level, **and xp is not removed**  

Whenever you promote a climb speed level, if there's still a large amount of remaining `xp` (occuring when several tens of large B2B attack is released) and is still over the amount to increase another climb speed level, thetn you gain an extra `xp/required xp` ranks, **and these extra xp are not removed**

    Which means this situation can happen:
    One frame - B2B breaks causing huge spike and `xp` increase
    Next frame - Promote + skip levels 
    Next frame - Can skip another climb speed level

### xp loss

Climb speed xp gradually diminishes over time, decreasing by `mul*(rank^2+rank)/3600` every frame.  
mul is related to【Expert(+)】, when disabled = 3, when enabled = 5, when in Duos = 3 + players with Expert

When xp is under 0 you lose a climb speed level, afterwards your xp becomes the maximum xp of the previous climb speed level.

Below are some calculated statistics for convenience:

| `rank` | xp required to promote | seconds to demotion | xp loss per second | 【Expert(+)】seconds to demotion | 【Expert(+)】xp loss per second |
| :--: | :-: | :---: | :--: | :---: | :----: |
|  1   | 4   | 40.00 |  0.1 | 24.00 |  0.17 |
|  2   | 8   | 26.67 |  0.3 | 16.00 |  0.50 |
|  3   | 12  | 20.00 |  0.6 | 12.00 |  1.00 |
|  4   | 16  | 16.00 |  1.0 |  9.60 |  1.67 |
|  5   | 20  | 13.33 |  1.5 |  8.00 |  2.50 |
|  6   | 24  | 11.43 |  2.1 |  6.86 |  3.50 |
|  7   | 28  | 10.00 |  2.8 |  6.00 |  4.67 |
|  8   | 32  | 8.89  |  3.6 |  5.33 |  6.00 |
|  9   | 36  | 8.00  |  4.5 |  4.80 |  7.50 |
|  10  | 40  | 7.27  |  5.5 |  4.36 |  9.17 |
|  11  | 44  | 6.67  |  6.6 |  4.00 | 11.00 |
|  12  | 48  | 6.15  |  7.8 |  3.69 | 13.00 |
|  13  | 52  | 5.71  |  9.1 |  3.43 | 15.17 |
|  14  | 56  | 5.33  | 10.5 |  3.20 | 17.50 |
|  15  | 60  | 5.00  | 12.0 |  3.00 | 20.00 |
|  16  | 64  | 4.71  | 13.6 |  2.82 | 22.67 |
|  17  | 68  | 4.44  | 15.3 |  2.67 | 25.50 |
|  18  | 72  | 4.21  | 17.1 |  2.53 | 28.50 |
|  19  | 76  | 4.00  | 19.0 |  2.40 | 31.67 |
|  20  | 80  | 3.81  | 21.0 |  2.29 | 35.00 |
|  21  | 84  | 3.64  | 23.1 |  2.18 | 38.50 |
|  22  | 88  | 3.48  | 25.3 |  2.09 | 42.17 |
|  23  | 92  | 3.33  | 27.6 |  2.00 | 46.00 |
|  24  | 96  | 3.20  | 30.0 |  1.92 | 50.00 |
|  25  | 100 | 3.08  | 32.5 |  1.85 | 54.17 |
|  26  | 104 | 2.96  | 35.1 |  1.78 | 58.50 |

### Appearance

You can view which climb speed you're at under the board, a simple text description of the appearances are shown below:

| `rank` | Multiplier | Color | Shape | Hyperspeed notes |
| :-: | :--: | :-: | - | - |
|  1  | 0.25 | none         | a progress bar | |
|  2  | 0.50 | red          | a triangle added below | |
|  3  | 0.75 | orange       | wings added to triangle | |
|  4  | 1.00 | yellow-green | wings increase size | |
|  5  | 1.25 | blue         | wings increase size + add base | |
|  6  | 1.50 | magenta      | wings extend to full size | |
|  7  | 1.75 | light orange | wings become more detailed | lowest `rank` without exiting hyperspeed |
|  8  | 2.00 | turquoise    | pair of parallelograms added on top | hyperspeed trigger at f1/f2 |
|  9  | 2.25 | cyan         | two pairs of parallelograms | hyperspeed trigger at f3/f4 |
| 10  | 2.50 | light purple | three pairs of parallelograms | hyperspeed trigger at f5 |
| 11  | 2.75 | white        | pair of white triangles added | |

### Hyperspeed

When the player's `rank` reaches 8/8/9/9/10 in the first five floors, hyperspeed is activated.  
Once activated there will be a flashy Bejeweled Twist-esque animation, alongside exclusive hyperspeed music.

A large display appears on the top of the screen showing floor splits and your pace compared to your PB Zenith Speedrun time.  
Reaching floor 10 with hyperspeed awards a hidden achievement, or when you fall to `rank` 6 or below hyperspeed disappears.

When activating 【Duos】 or any 【Mod+】 Hyperspeed is disabled

## Attack Target

You can't manually target someone in this mode, but the state of the player will impact the probability of yourself being attacked: `Targeting factor`  
The higher this value the likelier it is to be attacked, **with a starting value of 3**.

From additional observation, in most cases attacks are locked to players with similar altitude, specific calculations aren't clear

### Temporary decrease if in danger

Only in `Easy mode`, check once every 0.25 seconds, if in danger (conditions not understood, probably when your board flashes red, shouldn't be off by a lot) `Targeting factor` temporarily decreases by 1.5, after leaving danger the 1.5 is added back

### Shift to Targeting grace (No impact on messiness)

There is a `Targeting grace` value, when attacked, lines*0.25 amount of `Targeting factor` gets moved to the targeting grace buffer slot (maximum 3, otherwise doesn't move), then gets moved back later.

When the buffer slot for `Targeting grace` is filled (hits 3), attack magnification decreases by 25% (continuous attacks all send 25% less garbage)

The `Targeting grace` value (linear) will decrease garbage messiness, when fully filled can cause `change between attacks -45%` and `change during attack -18%` 

If `Targeting grace` has a value, every set amount of time (depending on floor, see table below) 0.25 `Targeting grace` value is moved back to `Targeting factor`, meaning the higher the floor, the more the system allows others to attack with garbage lines rapidly.

### Gradual time increase (Caps at doubled past 7 minutes)

When time hits 3/5/7 minutes, `Targeting factor` +1

`Targeting factor` alongside time/when rapidly filled/change when in danger:

| Time range | Factor | when full | when in danger |
| ----- | :-: | :-: | :-: |
| 0~2 minutes | 3 | -100% | -50% |
| 3~4 minutes | 4 | -75% | -75% |
| 5~6 minutes | 5 | -66% | -60% |
| past 7 minutes | 6 | -50% | -25% |

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

## Attack, All-Spin, B2B

Clearing 1, 2, 3 lines respectively send 0, 1, 2 attack

Limited to `easy modes`: “0 combo single 一 +1 attack”, making clearing 1 line also have 1 attack efficiency, can be considered under specific circumstances

Clearing 4 lines sends 4 attack, falls under `special clears` (increases B2B count, used in `Surge attack`, see next chapter for details)

This mode uses `All-Mini+` spin rules, a subtype of `All-Spin`, other than T every other tetromino's Spins also count as `special clears` 
Only T counts for a regular spin if it passes the 3-corner rule, with a base attack of `2*lines`, spins that don't fulfill 3-corner or non-T tetromino's that pass Immobile detection all count as Mini, with a base attack the same as normal clears, being `lines-1`

All Clears send 3 attack, but also count as +2 B2B (calculated separate from spins) (slightly different from regular TL, TL sends 5 attack but +1 B2B)

Consecutive `special clears` starting from the second one start gathering B2B count, and adds +1 attack

Whether to keep decimals or not uses RNG, in calculating process keep decimals, lastly take the decimal part as the chance for whether or not to round up, for example 1.2 has a 20% final chance to become 2, 80% final chance to become 1

### Surge Attack

When B2B is broken a large attack is created, attack is `B2B count -3`, (or the amount of consecutive special clears count -4) (slightly different in TL, however many B2B however many attack, no -3)

> This is a very important system in qp, really needed in certain situations

### Windup Attack

If a single attack with 8 or more lines is received, this attack will be split into multiple parts and have a warning hint before being received, to prevent easily topping out after targeting multiplier is increased due to various reasons

Splitting rule: Split the attack into several groups of 4 and the remainder portion, at maximum 4 groups (all extra attack are put in the last segment), for example 14 attack will be split into 4+4+4+2

Warning method: When receiving this type of attack start playing warning animations and sound effects  
The amount of sound effects corresponds to the amount of groups the current round's attack split into (for example 3 sounds corresponds to 4+4+n, or 9~12 attack)  
1 second later the attacks start entering the garbage queue, each split is separated by 0.5s

If 【Volatile】 is activated, values above related to attack are all multiplied (seems like so, individual circumstances will ±1) ((translation note: I have no idea what inside the parentheses means, sorry if it's unclear))

## Garbage messiness

The chance for garbage holes to continue. The higher this value, the more likely each line's hole is different

TETR.IO's garbage messiness system is decided by two numbers:  
“every line in the same attack has an X% chance to not stay on the same column”, “different attacks have a Y% chance to not stay on the same column” 

In TL X=0, Y=100%, which means the garbage lines in the same attack are always on the same column, and different attacks are always on different columns  
But in qp2 these two numbers aren't as extreme, meaning you'll feel the position of garbage holes aren't that related to the attacks in queue.

In qp2 the situation is Y=2.5*X, which means between received garbage attacks there's a higher chance (2.5 times) to be on a different column

The `garbage messiness` in this page is exactly this X, which can be affected by various factors

| Element | Impact value |
| :-: | :-: |
| Floor | `Floor*3%`, in 【Expert(+)】`Floor*5%` |
| 【Expert(+)】 | +Floor*2% |
| 【Messy(+)】 | +25% (100%) |
| 【All-Spin+】 | +30% |
| 【Expert+】's 6 minute Fatigue `Full scatter` effect | =100% (calculations above can surpass 100%, this effect overwrites) |
| `Targeting grace` (calculated when finally spawns) | every point of `Targeting grace` decreases Y by 3.75%, X by 1.5% |

> When `Targeting grace` hits 18 points, Y is decreased by 67.5%, X by 27%  
> Genuinely didn't write in the wrong order, quite weird here, probably need to pull a table to observe garbage messiness changes deduced from various factors  
> After receiving the `Full scatter` effect when both values are overwritten as 100%, instead between attacks it's even more likely to be on the same column, very interesting

## Garbage favor

Decides the choosing trend for garbage hole positions. This value can be positive or negative: the more it is when positive, garbage hole positions will be chosen easier to dig, same reasoning, the more it is negative the harder to dig

When this value is 0 (TL etc. modes' normal condition), garbage hole positions are evenly randomly chosen. If `Garbage lines aren't continuous` (messiness_nosame, for example custom room options) is activated at the same time, then it will avoid the last column picked  
In qp2, this value's formula is `33-floor*3`

When activating 【Expert(+)】, this value -33, which means evenly random at the start  
When activating 【Messier Garbage(+)】, this value -25  
When activating 【Volatile+】, this value is locked to 50 for the entire run

> The worst condition is Floor 10【Expert】【Messier Garbage】's -55  
> The easiest is 【Volatile+】's 50

Specific garbage hole position choosing process:
1. Calculate every columns' `dig easiness`
    1. If the column is one of the highest ones and doesn't have empty spaces, the `dig easiness` is 0
    1. Find the column's lowest empty space, find the height of the board's highest spot
    1. `dig easiness = height difference between empty space and highest spot + 5*empty space to highest garbage hole's horizontal distance`
1. Rank the ten columns according to their `dig easiness`, put the highest in the front (randomly sort for same values)
1. Use `Garbage favor` to calculate probability spread, formula is `weight[i] = 10 + favor * (1 - i / 4.5)`, consider negative values 0
    1. You can observe the graph in this [Desmos document](https://www.desmos.com/calculator/yfzabziltb)
    1. The X axis is the column numbers (left side column 0 is the easiest to dig, right side column 9 is the hardest to dig), the Y axis is the weight, use the slider at the left side to tune the favor value
1. Decide a column as the garbage hole position via the weight calculation of the previous step

## Garbage waiting time

When attacked garbage lines will wait in queue for a certain amount of time before entering a triggerable state, during this state placing pieces that don't clear lines causes garbage to enter through the board: transparent yellow → transparent red → opaque red (triggerable)  
Waiting time is decided by the floor or certain mods, for specific values see below:

| Floor |  Regular (Non-Expert)   |  【Expert(+)】   | 【Messier+/Volatile+/Double Hole+】 | Other【Mod+】 |
| :-: | :----------: | :---------: | :-------------: | :-----: |
|  1  |  5.0s (300f)  | 2.2s (132f) |   **2.5s**    |**2.5s**|
|  2  |  4.5s (270f)  | 2.0s (120f) |   **2.5s**    |**2.5s**|
|  3  |  4.0s (240f)  | 1.8s (108f) |   **2.5s**    |**2.5s**|
|  4  |  3.5s (210f)  | 1.6s  (96f) |   **2.5s**    |**2.5s**|
|  5  |  3.0s (180f)  | 1.4s  (84f) |   **2.5s**    |**2.5s**|
|**6**|**2.5s (150f)**| 1.2s  (72f) |   **2.5s**    |**2.5s**|
|  7  |  2.0s (120f)  | 1.0s  (60f) |   **2.5s**    | `2.0s` |
|  8  |  1.5s  (90f)  | 0.8s  (48f) |   **2.5s**    | `1.5s` |
|  9  |  1.0s  (60f)  | 0.6s  (36f) |   **2.5s**    | `1.0s` |
| 10  |  0.5s  (30f)  | 0.4s  (24f) |   **2.5s**    | `0.5s` |

> Note: Because garbage has to switch twice to enter a triggerable state, the statistics in the source code are half of the table above

## Fatigue

To prevent a game from being too long, starting from 8 minutes every minute adds a negative effect

| Time | Negative effect | Description |
| --- | --- | --- |
| 8 minutes | +2 permanent garbage | FATIGUE SETS IN… +2 PERMANENT LINES |
| 9 minutes  | +25% attack received | YOUR BODY GROWS WEAK… receive 25% more garbage |
| 10 minutes | +3 permanent garbage (total 5) | ALL SENSES BLUR TOGETHER… +3 PERMANENT LINES |
| 11 minutes | +25% attack received | YOUR CONSCIOUSNESS FADES… receive 25% more garbage |
| 12 minutes | +5 permanent garbage (total 10) | THIS IS THE END. +5 PERMANENT LINES |

> In 【Expert+】 fatigue effects are different, see later below for specifics

## Mods

In this page `Easy mode` means not activating 【Expert(+)】 and not activating 【Mod+】

Mods are ways you can increase the difficulty before starting a run, with basically only downsides and no upsides, but activating mods (or specific mod combinations) and reaching certain altitudes can grant achievements

There are a total of 9 mods, each corresponding with a special effect that can be individually toggled, with the setting having them as Tarot Cards, a description will be written after the mod name below, there will also be a table for convenience at the end of the chapter

((translation note: in the original readme "Garbage" in "Messier Garbage, Volatile Garbage, Double Hole Garbage" are omitted but to reflect more accurately to that of in-game I'll keep them for now))

### Expert (The Emperor)

- Harder to receive altitude and experience
- `Garbage messiness` is increased
- `Garbage favor` is decreased
- Rising garbage animation is removed, instead spawns instantaneously (same as TL)
- Removes system of decreasing `Targeting factor` when in danger

### No Hold (Temperance)

- Disables holding

### Messier Garbage (Wheel of Fortune)

- `Garbage messiness` increases
- `Garbage favor` decreases

### Gravity (The Tower)

- Gravity noticeably increases
- Lock delay table for the ten floors (unit frames): 30, 29, 28, 27, 26, 24, 22, 20, 18, 16

### Volatile Garbage (Strength)

- Attack multiplier and cancel multiplier are both x2

> Can be summarized as received garbage on the board is x2  
> Because it just increases the amount of garbage lines, therefore also indirectly decreases garbage messiness, so this mod can speed up climbing progress at the start, but poses too much of a threat in the endgame so whether its good or not is dependent on the specific type of play

### Double Hole Garbage (The Devil)

- Every line of garbage has a chance to have two holes

### Invisible (The Hermit)

- Pieces placed become invisible  
- Every 5 seconds the whole board flashes which can be convenient for digging

### All-Spin (The Magician)

- Non-T tetromino's Spins can be like T providing lines*2 of base attack (see the start for Spin detection rules)
- Whenever clearing lines (accurately it should be when a piece locks and action text appears, non-line-clear Spins can also trigger), if it's the exact same as the action text in the top-left corner, then a special full garbage line instantly appears as punishment, with a reverse tally of `current floor+5` on a random position, when the player does an unpunished line clear -1, upon hitting zero it turns into a regular one-hole garbage line, with the garbage hole on the same position as where the number was

> Only mod that can give a more positive effect after the player reaeches a certain skill level

### Duo (The Lovers)

- Players with supporter can invite others to play with themselves in this two-player mode
- To the perspective of one person, most output values will be halved, for example sent attacks and accumulated `xp` etc.
- After both players die the game ends, but after one player dies the other player can do revive task(s) to revive their teammate

  The tasks are divided into six grades ABCDEF, listed in full below:

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

Every mod has a corresponding buffed mod (except for 【Duos】), needing 30,000 meters climbed with the mod to unlock (activating multiple mods can accumulate for them at the same time)

    If you want to unlock all buffed mods as quick as possible it's recommended to activate multiple at the same time, below is a reference strategy (if you can smoothly get a few f10 with all of the mods individually)  
    `【Gravity】+【Messy】+【Double Hole】+【AllSpin】` activate these four and rely on allspin's fierce output, try not to let garbage lines enter, finish 30,000 meters. If you can use brainless Blitz mode looping and aren't afraid of `【Invisible】` you can bring it too, otherwise it 
    later needs to be cleared by itself  
    Afterwards activate `【Invisible】+【Volatile】` and `【No Hold】+【Volatile】`, notice try to tank more garbage then use Quad to dig to climb faster (because cancelling garbage lines has a worse result), at the same time try to calculate total efficiency with and without `Expert` 
    (altitude/time, multiply by 2 with Expert) to decide whether or not to accumulate for Expert incidentally, if possible then bring it, otherwise later on it needs to be cleared by itself  
    Last is `【Expert】+【Volatile】`, being individually played because this mod will substantially decrease climbing efficiency, and put last because it could already have some progress made at the start 

All buffed mods can only be played solo, and cannot be stacked on other mods

Introduction to effects that will appear later:

1. `Garbage line protection`: (Only appears in 【All-Spin+】【Double Hole Garbage+】【Messier Garbage+】)    
Every line of `Non-permanent garbage lines` (includes lines with clearable ***grey*** blocks) will cause `Targeting factor` to decrease by 0.5, at maximum decrease by 2.5 (due to the starting value being 3, so for these modes you rarely get attacked in the opening), check every 0.25 seconds

### Expert+ (The Tyrant)

> Fear, oppression, and limitless ambition.

On top of all limits of the original basis,  
- KO base attack is decreased from 15m to 8m
- Climb speed no longer gains altitude over time, sending attack and KOs are required to receive height
- `Targeting grace` releases faster (see `Targeting grace` related chapters for detail)
- Adds a descent system, altitude decreases over time, although it gets blocked by each floor's borderline so you can't fall to the previous floor
- When you stay on the same floor for over 60 seconds, every second permanently gain 0.5% multiplier to be attacked (for example after accumulating the effect for 200 seconds all incoming garbage is doubled)
- Fatigue system becomes even more harsh

|     Floor     |  Descent speed | Corresponding rank and spm |
| :--------: | :-----: | :---------: |
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

| Time | Negative effect | Text description |
| --- | --- | --- |
| 6 minutes | garbage becomes messier (disables `Targeting grace` effect) | YOUR POWER SLIPS… garbage received becomes messier |
| 7 minutes | +25% attack received | WHISPERS OF DISCONTENT SPREAD… receive 25% more garbage |
| 8 minutes | +3 permanent garbage | PROTESTERS LINE THE STREETS… +3 PERMANENT LINES |
| 9 minutes | +25% attack received | YOUR CLOSEST ALLIES DEFECT… receive 25% more garbage |
| 10 minutes | +5 permanent garbage (total 8) | PARANOIA CLOUDS YOUR JUDGEMENT… +5 PERMANENT LINES |
| 11 minutes | garbage becomes noticeably messier (receive `full scatter` effect) | THE REVOLUTION HAS BEGUN… garbage received becomes much messier |
| 12 minutes | +12 permanent garbage (total 20) | THE END OF AN ERA. +12 PERMANENT LINES |

### No Hold+ (Asceticism)

> A detachment from even that which is moderate.

- Holding is disabled
- 1 piece preview
- No piece shadow
- Completely random piece generation
- Spins all count as Mini (base attack of `lines-1`)
- Garbage holes all become 2-wide style

### Messier Garbage+ (Loaded Dice)

> In a rigged game, your mind is the only fair advantage.

- `Garbage messiness` is increased 
- Line clear delay increases from 0 to 1.15 seconds
- The starting board state becomes a fixed pattern of six circles:
- Activates `Garbage line protection`

```
Starting pattern：
..........
.XXX..XXX.
.X.X..X.X.
.XXX..XXX.
..........
.XXX..XXX.
.X.X..X.X.
.XXX..XXX.
..........
.XXX..XXX.
.X.X..X.X.
.XXX..XXX.
..........
```

### Gravity (Freefall)

> The ground you stood on never existed in the first place.

- 20G from the start (lock delay table for the ten floors: 24, 22, 20, 18, 16, 15, 14, 13, 12, 11)

### Volatile Garbage+ (Last Stand)

> Strength isn't necessary for those with nothing to lose.

- Received attack multiplier becomes 3x (notice: cancelling multiplier isn't changed)
- 14 high playfield
- Garbage hole positions have two warnings
- `Garbage favor` is locked to a very high value

### Double Hole Garbage+ (Damnation)

> No more second chances.

- The starting board state becomes 12-row checkerboard garbage lines
- Garbage lines become messy garbage lines with 3~4 random grey blocks  
- Can't cancel garbage lines (though you also don't receive much)  
- Activates `Garbage line protection`  
((translation note: garbage cap is reduced to 2 as well, and apparently incoming garbage is x0.5))

### Invisible+ (The Exile)

> Never underestimate blind faith.

- Pieces placed are invisible (but the board doesn't flash anymore)
- Only the top three garbage lines are visible  
- Receive 3 lines of garbage at the start by the system

### All-Spin+ (The Warlock)

> Into realms beyond heaven and earth.

- Repeating the same line clear is punished, and the penalty is changed to 20 lines of full garbage (instant death) ((translation note: it's technically survivable but really hard))
- At the same time non-spin line clears are all viewed as Single (clearing 2 lines then clearing 4 lines, counts as two Singles, death)  
- Receive 10 lines of garbage at the start by the system  
- `Garbage messiness` is increased
- Activates `Garbage line protection`

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

In all fatigue systems `+X% received attack` will be correspondingly increased to 2 (3) times due to 【Volatile(+)】, same as multiplication

## Special thanks

Thanks to ThTsOd for providing formatted code and partial interpreting

Thanks to friends in the group chat for testing, indicating problems and helping fixing

## Some unsure if useful technological bonus information

If you want to search for variables, here are some integer names below:

1. `Targeting factor` targetingfactor
1. `Targeting grace` targetinggrace
1. `Mods` zenith_[modname]
1. `Reverse mods` [modname]_reverse
1. `Change between attacks` messiness_change
1. `Change during attack` messiness_inner
1. `Garbage favor` garbagefavor
1. `garbage waiting time` garbagephase

```js
    /*
        Source code is from 2025.01.19 version, estimated to be the js after ts edited so it's definitely confusing, the code below is reference code modified from the source
        Deleted some unnecessary content, added various descriptions
        “MOD_” is a simplification for reading convenience, in the original code it's “this.S.setoptions.zenith_”,
        or “"xxxxxx_reversed" === this.S.setoptions.zenith_mods[0]”

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
        const height0 = this.S.stats.zenith.altitude; // Tracked for 'stuck' altitude

        // Experience loss
        if (frame >= this.S.zenith.rank_locked_until) {
            let leakSpeed = ...; // Solo:Normal3 Expert5  Duos:3+players with Expert
            this.S.zenith.climb_pts -= leakSpeed * (rank ** 2 + rank) / 3600 // climb_pts is current xp
        }

        const nextRankXP = 4 * rank;
        const storedXP = 4 * (rank - 1);
        if (this.S.zenith.climb_pts < 0)
            // Demotion
            if (rank <= 1)
                // Won't fall to under rank 0
                this.S.zenith.climb_pts = 0;
            else {
                // Recover calculation of total xp ((?))
                this.S.zenith.climb_pts += storedXP;
                this.S.zenith.last_rank_change_was_promote = false;
                rank--;
            }
        else if (this.S.zenith.climb_pts >= nextRankXP) {
            // Clear xp and promote one rank
            this.S.zenith.climb_pts -= nextRankXP; 
            this.S.zenith.last_rank_change_was_promote = true;
            this.S.zenith.rank_locked_until = frame + Math.max(60, 60 * (5 - this.S.zenith.promotion_fatigue));
            this.S.zenith.promotion_fatigue++;
            rank++;
        }

        // no natural xp loss for 5 seconds effect
        if (this.S.zenith.last_rank_change_was_promote && this.S.zenith.climb_pts >= 2 * (rank - 1))
            this.S.zenith.promotion_fatigue = 0;

        // Skipping ranks! if there's still a large remainder after promotion
        this.S.stats.zenith.rank = rank + this.S.zenith.climb_pts / (4 * rank);

        // Some statistics
        this.S.stats.zenith.peakrank = Math.max(this.S.stats.zenith.rank, this.S.stats.zenith.peakrank);
        this.S.stats.zenith.avgrankpts += this.S.stats.zenith.rank;

        const o = this.S.stats.zenith.altitude;
        const floor = me.GetFloorLevel(o);

        if (MOD_expertRev) {
            // 【Expert+】's descent
            this.S.stats.zenith.altitude = Math.max(me.FloorDistance[floor - 1], o - .05 * (floor ** 2 + floor + 10) / 60);
        } else {
            // Climb speed gaining altitude over time
            this.S.stats.zenith.altitude += .25 * rank / 60 * me.GetSpeedCap(o);
        }

        // Smooth altitude change
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

        // Disallow “climb speed gaining altitude over time” route for reaching next floor
        if (this.S.setoptions.zenith_tutorial && this.S.stats.zenith.altitude >= 50 && this.S.zenith.tutorial.stage > 0 && this.S.zenith.tutorial.stage < 5) {
            this.S.stats.zenith.altitude = Math.min(49.99, height0);
            this.S.zenith.bonusremaining = 0;
        }

        // 【Gravity(+)】
        floor !== this.S.stats.zenith.floor && (
            MOD_gravity ? (this.S.g += me.GravityBumps[floor], this.S.setoptions.locktime = me.GLockDelay[floor]) : MOD_gravityRev && (this.S.g = 20, this.S.setoptions.locktime = me.GRLockDelay[floor]), this.S.zenith.lastfloorchange = frame, 1 === floor ? this.S.glock = 240 : this.S.stats.zenith.splits[floor - 2] = Math.round(this.self.lm.GetGameTime())
        )
        this.S.stats.zenith.floor = floor;

        // 【Expert+】's overtime punishment
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

        // Targeting factor increase at 3/5/7 minutes
        if (frame===10800 || frame===18000 || frame===25200)
            this.S.stats.zenith.targetingfactor++;

        // Release targeting grace
        let r = 60 * (MOD_expertRev ? TargetingGrace : TargetingGraceRevEx)[floor];
        if (this.S.stats.zenith.targetinggrace > 0 && frame >= this.S.lastatktime + r) {
            this.S.stats.zenith.targetinggrace--;
            this.S.lastatktime = frame;
        }

        // Set new garbage messiness
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

        // Garbage favor
        this.S.setoptions.garbagefavor = MOD_volatileRev ? 50 : (MOD_expert ? 0 : 33) - 3 * floor - (MOD_messy ? 25 : 0);

        // Garbage waiting time
        this.S.setoptions.garbagephase = MOD_expert ? 66 - 6 * floor : 165 - 15 * floor;
        if (MOD_anyRev && !MOD_expert)
            this.S.setoptions.garbagephase = (MOD_messyRev || MOD_volatileRev || MOD_doubleholeRev) ? 75 : [75, 75, 75, 75, 75, 75, 75, 60, 45, 30, 15][floor];

        // Progressively close off garbage line protection when clearing garbage lines
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

    // Some methods
    function getHolePosition() { // Calculations related to garbage hole position, mainly to deal with garbage favor (used copilot to organize source code, can't confirm fully correct)
        let pos = 0;

        if (MOD_volatileRev) t.zenith.garbageahead.shift();

        if (t.setoptions.garbagefavor !== 0) {
            pos = function() {
                const scores = [];

                // If highest column has an open hole and includes grey tiles (garbage lines), tracks first hole's position counting from the left as holePosAtTopLine
                // Doesn't feel right......? Did I interpret wrong or is the source code genuinely wrong, I guess the design expectation is to find the highest garbage hole position?
                let garbageHolePosAtTop = -1;
                for (let y = field.height - 1; y >= 0; y--) {
                    let holePos = -1;
                    let isGarbage = false;
                    for (let x = 0; x < field.width; x++) {
                        if (holePos === -1 && null === t.board[y][x]) {
                            holePos = x;
                        }
                        if ("gb" === t.board[y][x]) {
                            isGarbage = true;
                        }
                    }
                    if (holePos !== -1) {
                        if (isGarbage) garbageHolePosAtTop = holePos;
                        break;
                    }
                }

                // For every column, first find the lowest empty tile, track this column's “dig easiness”
                e: for (let x = 0; x < field.width; x++) {
                    for (let y = 0; y < field.height; y++) {
                        if (null !== t.board[y][x]) {
                            const r = garbageHolePosAtTop === -1 ? 0 : Math.abs(x - garbageHolePosAtTop);
                            scores.push([x, (field.height - y) + 5 * r + .1 * t.rngex.nextFloat()]);
                            continue e;
                        }
                    }
                    scores.push([x, .1 * t.rngex.nextFloat()]);
                }

                // Rank every column based off the dig easiness from high to low
                scores.sort((e, t) => t[1] - e[1]);

                // Calculate every column's weight based off favor amount, which means decide whether to incline towards high or low dig easiness
                // favor为0时每一列的权重都是10，也就是等概率，图像画出来是一条直线（虽然0的时候其实会跳过这些步骤，不用这么麻烦），正数的时候就会把这条直线绕中点(4.5，10)顺时针旋转，也就是增加前五项好挖的列的权重，减少后五项不好挖的列的权重（负权重计为0）
                // ((translation work in progress))
                let scoreSum = 0;
                for (let i = 0; i < scores.length; i++) {
                    let score = Math.max(0, 10 + t.setoptions.garbagefavor + i * ((20 - 2 * (10 + t.setoptions.garbagefavor)) / 9));
                    if (t.setoptions.messiness_nosame && t.lastcolumn === scores[i][0]) score = 0;
                    if (MOD_volatileRev && (scores[i][0] < 2 || scores[i][0] >= e.bm.ColumnWidth() - 2)) score = 0;
                    scoreSum += score;
                    scores[i][2] = scoreSum;
                }

                // 以上一步计算的score为权重进行最终的随机选择（scoreSum是辅助变量，可以不管）
                // Use calculated score from previous step as weight and conduct the final random choice (scoreSum is an assisting variable, can be ignored)
                // ((translation work in progress))
                const r = t.rngex.nextFloat() * scoreSum;
                for (let i = 0; i < scores.length; i++) {
                    if (scores[i][2] !== 0 && r <= scores[i][2]) {
                        t.lastcolumn = scores[i][0];
                        return t.lastcolumn;
                    }
                }

                // 如果意外情况没返回，默认返回0（应该是最左列？）
                // ((translation work in progress))
              
                return 0;
            }();
        } else {
            if (t.setoptions.messiness_nosame && t.lastcolumn !== null) {
                pos = Math.floor(t.rngex.nextFloat() * (e.bm.ColumnWidth() - 1));
                if (pos >= t.lastcolumn) pos++;
            } else {
                pos = Math.floor(t.rngex.nextFloat() * e.bm.ColumnWidth());
            }
            t.lastcolumn = pos;

            if (MOD_volatileRev) {
                t.zenith.garbageahead.push(pos);
                t.lastcolumn = t.zenith.garbageahead[0];
                return t.lastcolumn;
            } else {
                return pos;
            }
        }
    }

    // Some events
    AwardKill() { // KOs
        this.GiveBonus(.25 * Math.floor(this.S.stats.zenith.rank) * (MOD_expertRev ? 8 : 15))
    }
    AwardLines(amount, giveHeight = true, giveXP = true) { // Non-Expert clearing lines(false,true) / Cancelling lines(false,true) / Sending attack(true,true)
        // Add altitude（impacted by mod etc.，see climb speed chapter table）
        let dh = .25 * Math.floor(this.S.stats.zenith.rank) * amount * (giveHeight ? 1 : 0);

        // When stuck +3m
        const heightToNextFloor = me.FloorDistance.find((e => this.S.stats.zenith.altitude < e)) - this.S.stats.zenith.altitude - dh - this.S.zenith.bonusremaining;
        if (heightToNextFloor >= 0 && heightToNextFloor <= 2) dh += 3;

        this.GiveBonus(dh);

        // Receive xp from clearing lines
        this.GiveClimbPts((amount + .05) * (giveXP ? 1 : 0));
    }
    AwardHasBeenAttacked(amount) { // Being attacked
        const spaceRemain = Math.min(18 - this.S.stats.zenith.targetinggrace, amount);
        if (spaceRemain > 0) this.S.stats.zenith.targetinggrace += spaceRemain;
    }
    GiveBonus(amount) { // Receive altitude (various routes)
        if (this.S.setoptions.zenith_tutorial && this.S.zenith.tutorial.stage > 0 && this.S.zenith.tutorial.stage < 5)
            amount *= me.GetSpeedCap(this.S.stats.zenith.altitude);
        this.S.zenith.bonusremaining += amount;
        if (this._bonusExpires < this.self.esm.frame) this._bonusCount = 0;
        this._bonusCount += amount;
        this._bonusExpires = this.self.esm.frame + 60;
        this.S.zenith.bonusfromally += amount;
    }
```
