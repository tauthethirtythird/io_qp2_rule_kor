# TETR.IO 퀵 플레이 규칙 설명 (원문: MrZ_26, 영어 번역본: Had0j)

## 일러두기

이 한국어 번역본은 영어 번역본을 중역한 것입니다. 또한, 번역의 정확성을 장담할 수 없습니다.
대괄호로 둘러싸인 글씨는 모드를, "Rev."는 리버스 모드를 가리킵니다.
이 글에서 "쉬운 모드"란, [(Rev.) 엑스퍼트]나 리버스 모드를 적용시키지 않은 상태를 편의상 가리키는 말입니다.
"매 프레임마다"는 "1/60초마다"를 뜻합니다.

## 게임의 시작

퀵 플레이 모드는 모두에게 똑같이 적용되는 "라운드"의 개념이 없으며, 누구나 원하는 때에 입장하여 게임을 시작할 수 있습니다.

## 등반

이 모드의 목표는 <b>제니스 탑(Zenith tower)</b>을 등반하는 것으로, 최종 점수는 <b>고도</b>로 결정됩니다.
특정 고도에 다다르게 되면 플레이어는 다음 층으로 올라가게 됩니다.

| 층 | 고도 범위 | 이름 |
| - | - | :-: |
| 1층 | 0m - 50m | 시작의 전당(Hall of Beginnings) |
| 2층 | 50m - 150m | 호텔(The Hotel) |
| 3층 | 150m - 300m | 카지노(The Casino) |
| 4층 | 300m - 450m | 경기장(The Arena) |
| 5층 | 450m - 650m | 박물관(The Museum) |
| 6층 | 650m - 850m | 버려진 사무실들(Abandoned Offices) |
| 7층 | 850m - 1100m | 실험실(The Laboratory) |
| 8층 | 1100m - 1350m | 중심(The Core) |
| 9층 | 1350m - 1650m | 오염(Corruption) |
| 10층 | 1650m+ | 신의 단<sub>壇</sub>(Platform of The Gods) |

## 등반 속도

<b>등반 속도</b>(또는 "등급")는 플레이어의 점수가 오르는 속도를 결정하며, 점수를 증가시키는 모든 행동은 등반 속도로 인한 배율의 영향을 받습니다. 등반 속도가 올라가려면 경험치가 필요합니다.

등반 속도가 1일 때 배율은 ×0.25배이며, 등반 속도가 1씩 오를 때마다 배율도 ×0.25배씩 오릅니다. (배율이 ×2.75배 이상일 때 등반 속도 표시는 하얀색으로 유지되지만, 실제로는 상한이 없기 때문에 얼마든지 배율을 높일 수 있습니다)

### 경험치

| 행동 | 얻는 고도(배율 적용 전) | 얻는 경험치 | 비고 |
| :--: | :--: | :--: | :-- |
| 자연적 증가 | 매초 1m | 자동으로 감소, 자세한 내용은 "경험치 감소" 챕터를 참고 | 다음 층과의 경계에 가까워질 때 고도 증가는 멈추게 됩니다. (다음 층과의 거리가 6-1m 남았을 때 점진적으로 0으로 줄어듦) |
| KO | 15m | | [Rev. 엑스퍼트]에서 8m |
| 공격 보내기 | `줄 수`m | `줄 수+0.05` 경험치 | |
| 가비지 상쇄 | | `줄 수*50%+0.05` 경험치 | [(Rev.) 엑스퍼트]/[Rev. 볼라타일]/<s>[Rev. 듀오]</s>에서는 0줄을 상쇄한 것으로 취급 (역주: 경험치를 아예 얻지 않는단 소리가 아닙니다) |
| 줄 지우기 | | `min(줄 수,2)+0.05` 경험치 | [(Rev.) 엑스퍼트]에서 ***적용되지 않으며***, [Rev. 올스핀]에서 모든 스핀이 아닌 클리어는 1줄로 취급됩니다. |
| 층 건너기 | 3m(배율에 영향을 받지 않음) | | 다음 층까지 2m 이내가 남은 상황에서 줄을 지울 시 발동됩니다. (역주: 솔직히 말해서 영어 번역본에 있었던 내용을 전혀 이해하지 못했으며, 오역일 가능성이 매우 높습니다) |

> "층 건너기"를 제외한 모든 고도 상승은 등급에 영향을 받습니다. 예를 들어 게임을 시작할 때, 등급은 1이고, 배율은 ×0.25배이므로, 매 4초마다 1m씩 올라가게 됩니다.  
> "상쇄 페널티"(자세한 내용은 후술)는 상쇄로 얻는 경험치를 감소시킵니다. Once `cancel penalty` surpasses `consecutive cancels minus experience threshold`, for every extra point the 50% in the formula will decrease by 0.5%, to a lowest of 5%. This threshold is 40 when activating 【Volatile Garbage(+)】, otherwise when 【All-Spin(+)】 is activated it's 10, otherwise it's 25.

When gaining altitude, the newly increased altitude will first be stored into a temporary variable, every frame release 10%, at maximum 10m 

The experience required to promote to the next Climb Speed level is `4*level`, once your experience meets the conditions your Climb Speed level increases by one and your experience decreases by the amount previously required

### 등급 스킵

Whenever you promote a Climb Speed level, if there's still a large amount of remaining experience (occuring when several tens of large B2B attack is released) and is still over the amount to increase another Climb Speed level, then you gain an extra `expreience/required experience` levels, **and these extra experience are not removed**

    Which means this situation can happen:
    One frame - Breaking B2B causes large spike and receive lots of experience
    Next frame - Promote + skip levels 
    Next frame - Can skip another Climb Speed level

### 경험치 감소

경험치는 자동적으로 매 프레임마다 `배율*(등급^2+등급)/3600` 씩 감소합니다. 
배율: 엑스퍼트나 듀오가 아닐 때: 3, [(Rev.) 엑스퍼트]나 [Rev. 듀오]에서: 5, 듀오에서: = 3 + 엑스퍼트를 적용한 사람의 수

등반 속도를 승급할 때 5초 동안 `경험치 보호` 효과가 발동되며, 이는 승급 후에 바로 강등되는 것을 막기 위함입니다.
`Promotion fatigue` system: After promoting, the last line's `no loss for 5 seconds` will decrease by 1 second (until 1 second), therefore the effect gets weaker and weaker when repeatedly gaining and losing `levels`  
To recover you need to reach 50% (peak of the slant on the middle of the experience bar) from a promotion action (rather than demotion), afterwards triggering this effect next time will have 5 seconds

편의를 위해 계산된 통계치:

| 등급 | 승급에 필요한 경험치 | 강등까지 걸리는 시간 | 초당 경험치 감소량 | [(Rev.) 엑스퍼트]에서 강등까지 걸리는 시간 | [(Rev.) 엑스퍼트]에서 초당 경험치 감소량 |
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

You can view which Climb Speed you're at under the board, a simple text description of the appearances are shown below:

| `level` | Multiplier | Color | Shape | Hyperspeed notes |
| :-: | :--: | :-: | - | - |
|  1  | 0.25 | none         | a progress bar | |
|  2  | 0.50 | red          | a triangle added below | |
|  3  | 0.75 | orange       | wings added to triangle | |
|  4  | 1.00 | yellow-green | wings increase size | |
|  5  | 1.25 | blue         | wings increase size + add base | |
|  6  | 1.50 | magenta      | wings extend to full size | |
|  7  | 1.75 | light orange | wings become more detailed | lowest `level` without exiting HYPERSPEED |
|  8  | 2.00 | turquoise    | pair of parallelograms added on top | HYPERSPEED trigger at f1/f2 |
|  9  | 2.25 | cyan         | two pairs of parallelograms | HYPERSPEED trigger at f3/f4 |
| 10  | 2.50 | light purple | three pairs of parallelograms | HYPERSPEED trigger at f5 |
| 11+ | 2.75 | white        | pair of white triangles added | |

### HYPERSPEED

When the player's `level` reaches 8/8/9/9/10 in the first five floors, HYPERSPEED is activated.  
Once activated there will be a flashy Bejeweled Twist-esque animation, alongside exclusive HYPERSPEED music.

A large display appears on the top of the screen showing floor splits and your pace compared to your PB Zenith Speedrun time.  
Reaching floor 10 with HYPERSPEED awards a hidden achievement, or when you fall to `level` 6 or below HYPERSPEED disappears.

When activating 【Duo】 or any 【Mod+】 Hyperspeed is disabled

## Attack Target

You can't manually target someone in this mode, but the state of the player will impact the probability of yourself being attacked: `Targeting Factor`  
The higher this value the likelier it is to be attacked, **with a starting value of 3**.

Note that `Targeting Factor` isn't the only factor that affects being attacked by other players, the player's attack target is fully decided by the server, can only say this value is likely one of the main factors

Other factors that could increase the chance of being chosen as another player's target:

- high Climb Speed level
- smaller altitude difference to other players

### Temporary decrease if in danger

Only in `Easy mode`, check once every 0.25 seconds, if in danger (conditions not understood, probably when your board flashes red, shouldn't be off by a lot) `Targeting Factor` temporarily decreases by 1.5, after leaving danger the 1.5 is added back

### Shift to Targeting Grace (No impact on messiness)

There is a `Targeting Grace` value, when attacked, lines*0.25 amount of `Targeting Factor` gets moved to the targeting grace buffer slot (maximum 3, otherwise doesn't move), then gets moved back later.

When the buffer slot for `Targeting Grace` is filled (hits 3), attack magnification decreases by 25% (continuous attacks all send 25% less garbage)

The `Targeting Grace` value (linear) will decrease garbage messiness, when fully filled can cause `change between attacks -45%` and `change during attack -18%` 

If `Targeting Grace` has a value, every set amount of time (depending on floor, see table below) 0.25 `Targeting Grace` value is moved back to `Targeting Factor`, meaning the higher the floor, the more the system allows others to attack with garbage lines rapidly.

### Gradual time increase (Caps at doubled past 7 minutes)

When time hits 3/5/7 minutes, `Targeting Factor` +1

`Targeting Factor` alongside time/when rapidly filled/change when in danger:

| Time range | Factor | when full | when in danger |
| ----- | :-: | :-: | :-: |
| 0~2 minutes | 3 | -100% | -50% |
| 3~4 minutes | 4 | -75% | -75% |
| 5~6 minutes | 5 | -66% | -60% |
| past 7 minutes | 6 | -50% | -25% |

## 공격, 올스핀, 백투백

한 번에 각각 1, 2, 3줄을 지우는 것은 0, 1, 2줄의 공격을 보냅니다.

Limited to `Easy mode`: “0 combo single 一 +1 attack”, making clearing 1 line also have 1 attack efficiency, can be considered under specific circumstances

Clearing 4 lines sends 4 attack, falls under `special clears` (increases B2B count, used in `Surge Attack`, see next chapter for details)

This mode uses `All-Mini+` spin rules, a subtype of `All-Spin`, other than T every other tetromino's Spins also count as `special clears` 
Only T counts for a regular spin if it passes the 3-corner rule, with a base attack of `2*lines`, spins that don't fulfill 3-corner or non-T tetromino's that pass Immobile detection all count as Mini, with a base attack the same as normal clears, being `lines-1`

All Clears send 3 attack, but also count as +2 B2B (calculated separate from spins) (slightly different from regular TL, TL sends 5 attack but +1 B2B)

Consecutive `special clears` starting from the second one start gathering B2B count, and adds +1 attack

Whether to keep decimals or not uses RNG, in calculating process keep decimals, lastly take the decimal part as the chance for whether or not to round up, for example 1.2 has a 20% final chance to become 2, 80% final chance to become 1

### 서지 공격

When B2B is broken a large attack is created, attack is `B2B count -3`, (or the amount of consecutive special clears count -4) (slightly different in TL, however many B2B however many attack, no -3)

> This is a very important system in qp, really needed in certain situations

### 와인드업 공격

If a single attack with 8 or more lines is received, this attack will be split into multiple parts and have a warning hint before being received, to prevent easily topping out after targeting multiplier is increased due to various reasons

Splitting rule: Split the attack into several groups of 4 and the remainder portion, at maximum 4 groups (all extra attack are put in the last segment), for example 14 attack will be split into 4+4+4+2

Warning method: When receiving this type of attack start playing warning animations and sound effects  
The amount of sound effects corresponds to the amount of groups the current round's attack split into (for example 3 sounds corresponds to 4+4+n, or 9~12 attack)  
1 second later the attacks start entering the garbage queue, each split is separated by 0.5s

If 【Volatile Garbage】 is activated, values above related to attack are all multiplied (seems like so, individual circumstances will ±1) ((translation note: I have no idea what the text inside the parentheses mean, sorry if it's unclear.))

## Others related to attack

### 연속적 상쇄

There is a `consecutive cancel` variable, the amount of garbage lines cancelled the amount is added  
All Clears add **+5**
Every 30 seconds without tanking garbage lines **+5**, timer then resets to zero  
When clearing grey tiles (garbage lines) instantly **becomes 0**  
When garbage in queue releases as garbage lines, every line entered through the bottom of the board -3 (lowest is 0)  
When an I-Spin clears lines **-2**
When clearing a Quad **-3**, track the column, if different from both of the previous two times (doesn't repeat tracking, only keep new ones ((translation note: I have no idea what the text inside the parentheses mean, sorry if it's unclear))) then another **-4**  
SZ/JL piece spins clearing lines is the same as I piece clearing Quads, just changed to rotation center column, when both different **-2** (SZ and JL each use the same table)

Once `consecutive cancel` reaches certain values, the original 7-bag order becomes modified, adding extra pieces to every bag:

 - 20: O piece
 - 30: random of L/J
 - 40: random of S/Z
 - 50: random of L/J
 - 50: random of T/I
 - 60: random of S/Z

Will also shorten received garbage amount ((translation note: not sure what this means)), see `received amount calculation` chapter for detail

> This system's addition can basically be attributed to the [메커니컬 하트](https://bilibili.com/opus/997806608970940469) strategy

### Targeting Grace

There is a `Targeting Grace` variable, when attacked increase the same amount of value as received garbage in queue (value through various penalty/protection adjustments, not the original attack amount, excluding 【Volatile Garbage+】's 3x isn't counted), until capping at **18**  
`Targeting Grace`'s value decreases `garbage messiness`, although this system is blocked by these reasons: when time reaches 6 minutes in【Expert+】, 【Messier Garbage(+)】  
If `Targeting Grace`>0, then it will decrease by 1 a bit of time after “last moment of being attacked”, and refresh “last moment of being attacked” as the current moment, release gaps are shown below:

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

### Received amount calculation

When attacked the amount is adjusted based off various factors, before lastly appearing in the garbage queue, specific process listed below:

#### 1. Altitude penalty

Calculate `critical altitude` = `max(min(attacker's altitude,3500), min(altitude-1000,2000))`

If altitude is greater than `critical altitude`, multiply received attack by `100% + 0.4% *(altitude - critical altitude)^2) / (altitude + critical altitude)`

#### 2. Partner penalty

If 【Duo(+)】 is activated and the partner is dead, multiply received attack by `150%`

#### 3. Cancel penalty (looping penalty)

First fetch `penalty coefficient`  
Default 0.001  
With 【All-Spin】 without 【Volatile Garbage】: 0.0003  
With 【Volatile Garbage】 without 【All-Spin】: 0.002

Attacks add `penalty coefficicent * consecutive cancels ^ 2`, although increase amount won't surpass:

- Basic upper limit: Check floor count, first 7 floors is **floor+3**, unlimited after eighth floor  
- If currently in windup: choose lower value compared to 6  
- If 【Volatile】 is enabled multiply by 2

Multiply received attack by `100% + base multiplier*cancel penalty^2`

If `cancel penalty` hits 25 and 【Volatile Garbage】 isn't activated, this attack countdown/2 ((translation note: not sure what this means))

#### 4. Carrying protection

If 【Duo(+)】 is activated and bonus altitude contribution percentage through sending/KOs is less than 20%, multiply sent attack by `55%+contribution%`

#### 5. Targeting Grace protection

If `Targeting Grace` is over 8, multiply sent attack by `100% - 5%*(Targeting Grace-8)`

#### Result

Multiply attack by `attack received multiplier`, then round (use decimals as weighted randomness in qp), spawn in garbage queue

## Garbage messiness

The chance for garbage holes to continue. The higher this value, the more likely each line's hole is different

TETR.IO's garbage messiness system is decided by two numbers:  
“every line in the same attack has an X% chance to reroll the position”, “different attacks have a Y% chance to reroll the position” 

In TL X=0, Y=100%, which means the garbage lines in the same attack are almost always on different columns (unchanged if rerolled on the same position, 10%) 
But in qp2 these two numbers aren't as extreme, meaning you'll feel the position of garbage holes aren't that related to the attacks in queue.

In qp2, by default Y=2.5*X, which means between received garbage attacks there's a higher chance (2.5 times) to be on a different column

The `garbage messiness` in this page is exactly this X, which can be affected by various factors

| Element | Impact value |
| :-: | :-: |
| Floor | `Floor*3%`, in 【Expert(+)】`Floor*5%` |
| 【Expert(+)】 | +Floor*2% |
| 【Messier Garbage(+)】 | +25% (100%) |
| 【All-Spin+】 | +30% |
| 【Expert+】's 11 minute Fatigue `full scatter` effect | =100% (calculations above can surpass 100%, this effect overwrites) |
| `Targeting Grace` (calculated when finally spawns) | every point of `Targeting Grace` decreases Y by 3.75%, X by 1.5% |

> When `Targeting Grace` hits 18 points, Y is decreased by 67.5%, X by 27%  
> Genuinely didn't write in the wrong order, quite weird here, probably need to pull a table to observe garbage messiness changes deduced from various factors  
> After receiving the `full scatter` effect when both values are overwritten as 100%, instead between attacks it's even more likely to be on the same column, very interesting

## 가비지 난이도

Decides the choosing trend for garbage hole positions. This value can be positive or negative: the more it is when positive, garbage hole positions will be chosen harder to dig, same reasoning, the more it is negative the easier to dig

When this value is 0 (TL etc. modes' normal condition), garbage hole positions are evenly randomly chosen. If `Garbage lines aren't continuous` (messiness_nosame, for example custom room options) is activated at the same time, then it will avoid the last column picked  
In qp2, this value's default formula is `33-floor*3`, the further the easier, suspected to be used to cancel overly fast difficulty increase from garbage messiness

When activating 【Expert(+)】, this value -33, which means evenly random at the start  
When activating 【Messier Garbage(+)】, this value -25  
When activating 【Volatile Garbage+】, this value is locked to 50 for the entire run

> The worst condition is Floor 10【Expert】【Messier Garbage】's -55   
> The easiest is 【Volatile Garbage+】's 50

Specific garbage hole position choosing process:
1. Calculate every columns' `dig hardness`
    1. If the column is one of the highest ones and doesn't have empty spaces, the `dig hardness` is 0
    1. Find the column's lowest empty space, find the height of the board's highest spot
    1. `dig hardness = height difference between empty space and highest spot + 5*empty space to highest garbage hole's horizontal distance`
1. Rank the ten columns according to their `dig hardness`, put the highest in the front (randomly sort for same values)
1. Use `Garbage difficulty` to calculate probability spread, formula is `weight[i] = 10 + favor * (1 - i / 4.5)`, consider negative values 0
    1. You can observe the graph in this [Desmos document](https://www.desmos.com/calculator/yfzabziltb)
    1. The X axis is the column numbers (left side column 0 is the easiest to dig, right side column 9 is the hardest to dig), the Y axis is the weight, use the slider at the left side to tune the favor value
1. Decide a column as the garbage hole position via the weight calculation of the previous step

## Garbage gathering
 
There is a `garbage gathering` toggle, enabled when `garbage messiness` <=15% and within the first 5 floors
 
When enabled, garbage hole positions will never be on the two leftmost or rightmost columns, which means it's always on columns 3~8

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

## 피로

한 판이 너무 길어지는 것을 막기 위해서, 시작 8분 후부터 매 분마다 디버프가 걸립니다.

| 시간 |  디버프 | 인게임 텍스트 |
| --- | --- | --- |
|  8:00 | +2 permanent garbage | FATIGUE SETS IN… +2 PERMANENT LINES |
|  9:00 | +25% attack received multiplier | YOUR BODY GROWS WEAK… receive 25% more garbage |
|  10:00 | +3 permanent garbage (total 5) | ALL SENSES BLUR TOGETHER… +3 PERMANENT LINES |
|  11:00 | +25% attack received multiplier | YOUR CONSCIOUSNESS FADES… receive 25% more garbage |
|  12:00 | +5 permanent garbage (total 10) | THIS IS THE END. +5 PERMANENT LINES |

> In [Rev. 엑스퍼트]에서는 피로 효과가 다릅니다. (자세한 내용은 후술)

## 모드

Mods are ways you can increase the difficulty before starting a run, with basically only downsides and no upsides, but activating mods (or specific mod combinations) and reaching certain altitudes can grant achievements

There are a total of 9 mods, each corresponding with a special effect that can be individually toggled, with the setting having them as Tarot Cards, a description will be written after the mod name below, there will also be a table for convenience at the end of the chapter

### Expert Mode (The Emperor)

> A display of power for those willing to bear its burden.

- Harder to receive altitude and experience
- `Garbage messiness` is increased
- `Garbage difficulty` is decreased
- Rising garbage animation is removed, instead spawns instantaneously (same as TL)
- Removes system of decreasing `Targeting Factor` when in danger

### No Hold (Temperance)

> Use each piece as they come and embrace the natural flow of stacking.

- Disables holding

### Messier Garbage (Wheel of Fortune)

> The only constant in life is change.

- `Garbage messiness` increases
- `Garbage difficulty` decreases

### Gravity (The Tower)

> What will you do when it all comes crumbling down?

- Gravity noticeably increases
- Lock delay table for the ten floors (unit frames): 30, 29, 28, 27, 26, 24, 22, 20, 18, 16

### Volatile Garbage (Strength)

> Match great obstacles with greater determination.

- `Attack multiplier` and `cancel multiplier` are both x2

> Can be summarized as received garbage on the board is x2  
> Because it just increases the amount of garbage lines, therefore also indirectly decreases garbage messiness, so this mod can speed up climbing progress at the start, but poses too much of a threat in the endgame so whether its good or not is dependent on the specific type of play

### Double Hole Garbage (The Devil)

> Redefine your limits or succumb to his chains.

- Every line of garbage has a chance to have two holes

### Invisible (The Hermit)

> When the outside world fails you, trust the voice within to light a path.

- Pieces placed become invisible  
- Every 5 seconds the whole board flashes which can be convenient for digging

### All-Spin (The Magician)

> Inspiration is nothing short of magic.

- Non-T tetromino's Spins can be like T providing lines*2 of base attack (see the start for Spin detection rules)
- Whenever clearing lines (accurately it should be when a piece locks and action text appears, non-line-clear Spins can also trigger), if it's the exact same as the action text in the top-left corner, then a special full garbage line instantly appears as punishment, with a reverse tally of `current floor+5` on a random position, when the player does an unpunished line clear -1, upon hitting zero it turns into a regular one-hole garbage line, with the garbage hole on the same position as where the number was

> Only mod that can give a more positive effect after the player reaeches a certain skill level

### Duo (The Lovers)

> Love, and resign yourself to the fate of another.

- Players with supporter can invite others to play with themselves in this two-player mode
- To the perspective of one person, most output values will be halved, for example sent attacks and accumulated experience etc.
- After both players die the game ends, but after one player dies the other player can do revive task(s) to revive their teammate

Tasks that will appear are shown below:

| 난이도 | 코드 내 ID | 미션 값 | 내용 | 분류 | 특정 모드에서 나타나지 않음 |
| - | - | - | - | - | - |
| F | combo              | 3   | 3-콤보 달성하기 | 2 | |
| F | double             | 2   | 더블을 2번 클리어하기 | 2 | |
| F | quad               | 1   | 쿼드를 클리어하기 | 1 | |
| F | lines              | 6   | 6줄을 클리어하기 | 1 | |
| F | osingle            | 1   | O미노로 싱글 클리어하기 | 3 | |
| F | odouble            | 1   | O미노로 더블 클리어하기 | 3 | |
| F | szdouble           | 1   | S 또는 Z미노로 더블 클리어하기 | 3 | |
| F | ljtriple           | 1   | L 또는 J미노로 트리플 클리어하기 | 3 | |
| F | iholdlines         | 3   | Clear 3 lines\nwhile holding an I-Piece | 3 | [노홀드] |
| F | hold               | 8   | 홀드를 8회 사용하기 | 2 | [노홀드] |
| F | rotate             | 20  | 20회 회전하기 | 2 | |
| F | singleconsecutive  | 2   | Clear 2 Singles in a row | 3 | |
| E | spin               | 1   | 아무 스핀 수행하기 | 2 | |
| E | tspinsingle        | 1   | T스핀 싱글 클리어하기 | 2 | |
| E | tspindouble        | 1   | T스핀 더블 클리어하기 | 2 | |
| E | szspin             | 1   | S/Z스핀 클리어하기 | 1 | |
| E | ljspin             | 1   | L/J스핀 클리어하기 | 1 | |
| E | combo              | 5   | 5-콤보 달성하기 | 2 | |
| E | iflat              | 2   | Clear 2 Lines using\nhorizontal I-Pieces | 3 | |
| E | pieces             | 20  | Place 20 pieces | 2 | |
| E | attack             | 6   | 공격 6줄 보내기 | 1 | |
| E | placeoconsecutive  | 2   | 연속으로 2개의 O미노 놓기 | 3 | |
| E | norotateclockwise  | 12  | Place 12 pieces while only\nrotating counterclockwise | 4 | |
| E | singlenocombo      | 6   | Clear 6 Singles without\nstarting a combo | 3 | |
| D | double             | 4   | Clear 4 Doubles | 2 | |
| D | spam               | 3   | Place 3 pieces in a row\nwithout moving or rotating | 4 | |
| D | noclear            | 14  | Place 14 pieces in a row\nwithout clearing any lines | 4 | |
| D | szdouble           | 2   | Clear 2 Doubles\nusing S or Z-Pieces | 3 | |
| D | ljtriple           | 2   | Clear 2 Triples\nusing L or J-Pieces | 3 | |
| D | ispinclear         | 1   | Clear an I-Spin | 1 | |
| D | upperhalfquad      | 1   | Clear a Quad in the\nupper half of the board | 4 | |
| D | rotate             | 80  | 80회 회전하기 | 2 | |
| D | quadcombo          | 1   | Clear a Quad\nwhile on a 2+-Combo | 4 | |
| D | szsingle           | 2   | Clear 2 Singles in a row\nusing S or Z-Pieces | 4 | |
| D | combonohold        | 3   | Perform a 3-Combo\nwithout using Hold | 3 | |
| D | noclearspin        | 3   | Perform 3 Spins\nthat don't clear any lines | 4 | |
| D | szljspin           | 2   | | Perform 2\nS/Z/L/J-Spins | 3 | |
| C | tspintriple        | 1   | Clear a T-Spin Triple | 2 | |
| C | nohold             | 25  | Place 25 pieces in a row\nwithout using Hold | 4 | 【No Hold】 |
| C | triple             | 3   | Clear 3 Triples | 2 | |
| C | b2b                | 4   | Reach B2B x4 | 1 | |
| C | quadbuckets        | 2   | Clear a Quad in\n2 different columns | 3 | |
| C | holdconsecutive    | 12  | Use Hold on\n12 pieces in a row | 3 | 【No Hold】 |
| C | softdrop           | 10  | Place 10 pieces without\nreleasing Soft Drop | 4 | |
| C | top3rows           | 3   | Have part of your stack in\nthe top 3 rows for 3 seconds | 4 | |
| C | linesnoti          | 10  | Clear 10 Lines without\nclearing with T or I-pieces | 4 | |
| C | szspintriple       | 1   | Clear an S/Z-Spin Triple | 2 | |
| C | odoubleconsecutive | 2   | 2개의 O미노를 사용해 더블 연속으로 클리어하기 | 4 | [노홀드] |
| C | tspinminiclear     | 4   | Clear 4 T-Spin Minis | 2 | |
| C | attack             | 14  | 공격 14줄 보내기 | 1 | |
| C | doublespiece       | 3   | Clear 3 Doubles\nwith the same type of piece | 4 | |
| C | ljgarbage          | 1   | Clear Garbage\nusing a L/J-Spin | 3 | |
| C | szgarbage          | 1   | Clear Garbage\nusing a S/Z-Spin | 3 | |
| C | columnopiece       | 3   | Place 3 O-Pieces\nin column 1 | 3 | |
| C | spinclear          | 2   | Clear 2 Spins\nin one combo | 3 | |
| C | iclearspam         | 1   | Clear a Single with an I-Piece\nwithout moving or rotating | 4 | |
| C | holddas            | 6   | Place 6 Pieces\nwithout releasing DAS | 3 | |
| B | oclear             | 6   | Clear 6 Lines\nusing O-Pieces | 3 | |
| B | spinbuckets        | 3   | Clear Spin-Clears\nwith 3 different pieces | 3 | |
| B | quad               | 4   | 쿼드 4번 클리어하기 | 1 | |
| B | spam               | 5   | Place 5 pieces in a row\nwithout moving or rotating | 4 | |
| B | ljspintriple       | 1   | Clear an L/J-Spin Triple | 2 | |
| B | quadconsecutive    | 2   | Clear 2 Quads in a row | 2 | |
| B | singlesonly        | 8   | Clear 8 Singles without doing\nother clears or using Hold | 4 | |
| B | nogarbage          | 4   | Have no Garbage Lines on\nyour board for 4 seconds | 4 | 【Duo+】 |
| B | rotate             | 300 | 300회 회전하기 | 2 | |
| B | nocancel           | 8   | Don't cancel any\ngarbage for 8 seconds | 3 | |
| B | tspindoubleup      | 1   | Clear a T-Spin Double\nwith the Piece pointing up | 4 | |
| B | oclearspam         | 1   | Clear a Double with an O-Piece\nwithout moving or rotating | 4 | |
| B | tnorotate          | 3   | Place 3 T-Pieces\nwithout rotating any | 3 | |
| B | tspincombo         | 1   | Clear a T-Spin Double\nwhile on a 2+-Combo | 3 | |
| A | combo              | 7   | Perform a 7-Combo | 2 | |
| A | ispindouble        | 1   | Clear an I-Spin Double | 2 | |
| A | szspinconsecutive  | 2   | Clear two S/Z-Spin\nDoubles consecutively | 3 | |
| A | ljspinconsecutive  | 2   | Clear two L/J-Spin\nDoubles consecutively | 3 | |
| A | colorclear         | 1   | Perform a Color Clear | 2 | |
| A | lines              | 40  | 40줄 클리어하기 | 1 | |
| A | combospin          | 4   | Clear 4 Spins\nin one Combo | 3 | |
| A | tspindtcolumn      | 1   | Clear a T-Spin Double/Triple\ncentered in column 1 or 10 | 3 | |
| X (Special) | ospinconsecutive | 2 | Clear two O-Spin Mini\nDoubles consecutively | 3 | |

There is a `accumulated revive difficulty` variable, when reviving increase (First five floors +1, floors six to nine +2, floor 10 +3)

When needing to revive calculate revive difficulty score = `floor+accumulated revive difficulty`, and then select a group based off the score, lastly choose tasks from the list above and randomize order:
 
1. F
2. F F
3. F F F
4. F F E
5. F E E
6. E E E
7. E E D
8. E D D
9. D D D
10. D D C
11. D C C
12. C C C
13. C C B
14. C B B
15. B B B
16. B B A
17. A B A (상한, ABA 순서로 항상 고정되어 있음)

## 리버스 모드

모든 모드는 그에 대응하는 업그레이드 버전이 있으며, 이는 그 모드를 적용한 챠로 총합 3만 미터를 등반하면 해금됩니다. (한 번에 여러 모드를 적용하여 동시에 쌓을 수 있습니다)
[Rev. 듀오]는 특별합니다. (자세한 내용은 후술)

    If you want to unlock all buffed mods as quick as possible it's recommended to activate multiple at the same time, below is a reference strategy (if you can smoothly get a few f10 with all of the mods individually)  
    `【Gravity】+【Messier Garbage】+【Double Hole Garbage】+【All-Spin】` activate these four and rely on All-Spin's fierce output, try not to let garbage lines enter, finish 30,000 meters. If you can use brainless Blitz mode looping and aren't afraid of `【Invisible】` you can bring it too, otherwise it 
    later needs to be cleared by itself  
    Afterwards activate `【Invisible】+【Volatile Garbage】` and `【No Hold】+【Volatile Garbage】`, notice try to tank more garbage then use Quad to dig to climb faster (because cancelling garbage lines has a worse result), at the same time try to calculate total efficiency with and without `Expert` 
    (altitude/time, multiply by 2 with Expert) to decide whether or not to accumulate for Expert Mode incidentally, if possible then bring it, otherwise later on it needs to be cleared by itself  
    Last is `【Expert】+【Volatile Garbage】`, being individually played because this mod will substantially decrease climbing efficiency, and put last because it could already have some progress made at the start 

All buffed mods can only be played solo, and cannot be stacked on other mods

Introduction to effects that will appear later:

1. `Garbage line protection`: (Only appears in certain mods)    
Every line of `Non-permanent garbage lines` (includes lines with clearable ***grey*** blocks) will cause `Targeting Factor` to decrease by 0.5, at maximum decrease by 2.5 (due to the starting value being 3, so for these modes you rarely get attacked in the opening), check every 0.25 seconds

### Rev. 엑스퍼트 (The Tyrant)

> Fear, oppression, and limitless ambition. (두려움, 짓누름, 그리고 한없는 야망)

엑스퍼트 모드의 모든 디버프에 더해,  
- KO로 인한 고도 획득(배율 적용 전): 15m -> 8m
- 고도가 등반 속도에 따라 자연적으로 증가하지 않음
- `Targeting Grace` releases faster (see `Targeting Grace` related chapters for detail)
- Adds a descent system, altitude decreases over time, although it gets blocked by each floor's borderline so you can't fall to the previous floor
- When you stay on the same floor for over 60 seconds, every second permanently gain 0.5% multiplier to be attacked (for example after accumulating the effect for 200 seconds all incoming garbage is doubled)
- Fatigue system becomes even more harsh

|     층     | 고도 감소 속도 | 그에 대응되는 등급과 SPM |
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
> `level` and spm are only for reference, in reality cancelling doesn't count for spm so it can't be achieved, after the fifth-sixth floor you have to rely on 3-digit surge APM to continue climbing  ((translation note: SPM = Sent Per Minute))  
> During gameplay descent looks like it has acceleration, but it's only a visual effect, in reality it's still even

| 시간 | 디버프 | 인게임 텍스트 |
| --- | --- | --- |
|  6:00 | garbage becomes messier (disables `Targeting Grace` effect) | YOUR POWER SLIPS… garbage received becomes messier |
|  7:00 | +25% attack received multiplier | WHISPERS OF DISCONTENT SPREAD… receive 25% more garbage |
|  8:00 | +3 permanent garbage | PROTESTERS LINE THE STREETS… +3 PERMANENT LINES |
|  9:00 | +25% attack received multiplier | YOUR CLOSEST ALLIES DEFECT… receive 25% more garbage |
|  10:00 | +5 permanent garbage (total 8) | PARANOIA CLOUDS YOUR JUDGEMENT… +5 PERMANENT LINES |
|  11:00 | garbage becomes noticeably messier (receive `full scatter` effect) | THE REVOLUTION HAS BEGUN… garbage received becomes much messier |
|  12:00 | +12 permanent garbage (total 20) | THE END OF AN ERA. +12 PERMANENT LINES |

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

- Received attack multiplier becomes 3x (notice: `cancelling multiplier` isn't changed)
- 14 high playfield
- Garbage hole positions have two warnings
- `Garbage difficulty` is locked to a very high value, and `garbage gathering` is permanently enabled

### Double Hole Garbage+ (Damnation)

> Neither the freedom of life or peace of death.

- The starting board state becomes 12-row checkerboard garbage lines
- Garbage lines become messy garbage lines with 3~4 random grey blocks  
- Cannot attack (including cancelling). Unless during: clearing garbage lines, or with the “BLIGHTED” effect
 - BLIGHTED: Received after clearing garbage lines, when enabled the next line clear's attack *1.75, if doesn't clear garbage lines buff disappears and +1 attack
 - Board has 4 fixed garbage lines, when cleared spontaneously appears again
 - Activates `garbage line protection` (er... isn't there always 4 lines)
((translation note: garbage cap is reduced to 2 as well))

### Invisible+ (The Exile)

> Never underestimate blind faith.

- Pieces placed are invisible (but the board doesn't flash anymore)
- Only the top three garbage lines are visible  
- Receive 3 lines of garbage at the start by the system

### All-Spin+ (The Warlock)

> Into realms beyond heaven and earth.

- Even more strict consecutive same clear penalty: only track Spin's lines cleared count (including 0) or Void actions, as long as two consecutive attacks are the same then 20 penalty lines are added leading to instant death  
- After reaching B2B x 4, any Spin (including ones that don't clear lines) +2 attack, and B2B counter can be increased without clearing lines  
- All non-Spin clears are called “Void”, no attack ((translation note: Void acts as a Single but doesn't penalize if a Spin Single is done previously))
- Receive 10 lines of garbage at the start by the system  
- `Garbage messiness` is increased
- Activates `Garbage line protection`

## Special Mods

### Duo+ (Bleeding Hearts)

> Even as we bleed, we keep holding on...  

Exclusive to 2025 Valentine's Day event, free to play for everyone for a week (includes regular version), unlocking not required

- When attacking (sending/cancelling both count) there is a Backfire, prioritizing the partner, if already dead then it will attack yourself (parameter is Zen mode's unclear 0.5x, without warning or waiting instantaneously enter the board)
- When one of the players dies the altitude will be temporary locked, until being revived  
- Climb Speed level is locked to a highest of 4 (normally unlimited)  
- Special fatigue process
- ((translation note: apparently Climb Speed level is capped at 5 (blue) as well, not sure if this is correct though))

|  Time  | Effect | Description |
| ----- | --- | --- |
|  1:00 | `Garbage messiness`= 5% | THE RELATIONSHIP STAGNATES…  garbage becomes a bit messier |
|  1:30 | `Garbage messiness`= 15% | INSECURITIES GROW STRONGER…  garbage becomes messier |
|  2:00 | `Garbage messiness`= 30% | {PARTNER} FEELS NEGLECTED…  garbage becomes much messier |
|  2:30 | `Garbage messiness`= 20% | {SELF} SUCCESSFULLY APOLOGIZES…?  garbage becomes a bit cleaner |
|  3:00 | `Garbage messiness`= 0% | THINGS ARE BACK TO HOW THEY SHOULD BE…!  garbage becomes much cleaner |
|  3:30 | `Garbage messiness`= 10% | THE WEIGHT OF WORDS UNSPOKEN…  garbage becomes messier |
|  4:00 | `Garbage messiness`= 25% | "WHY CAN'T YOU JUST LISTEN TO ME?"  garbage becomes much messier |
|  4:30 | Revive difficulty +3 levels | "THIS IS ALL YOUR FAULT."  revive difficulty increased |
|  5:00 | `Garbage messiness`= 10% | {PARTNER} MAKES THE SAME PROMISE AGAIN…  garbage becomes cleaner |
|  5:30 | +4 permanent garbage lines | "THIS TIME WILL BE DIFFERENT."  +4 PERMANENT GARBAGE |
|  6:00 | `Garbage messiness`= 30% | SOME HABITS CAN'T BE BROKEN…  garbage becomes much messier |
|  6:30 | `Garbage messiness`= 40% | ALL TRUST HAS WITHERED AWAY…  garbage becomes messier |
|  7:00 | `Garbage messiness`= 50% | {SELF} SETS AN ULTIMATUM…  garbage becomes messier |
|  7:30 | `Garbage messiness`= 60% | {PARTNER} CONTEMPLATES THEIR WASTED EFFORT…  garbage becomes messier |
|  8:00 | +25% attack received multiplier | ONE LAST PAINFUL ARGUMENT…  receive 25% more garbage |
| `8:30`| “Disable reviving” | GOODBYE.  you can no longer revive |
| `9:30`| `Garbage messiness`= 20% | "I MISS YOU"  garbage becomes much cleaner |
| 10:00 | `Garbage messiness`= 10% | WHAT IF…?  garbage becomes a bit cleaner |
| 10:30 | +12 permanent garbage lines (total of 16) | …  +12 PERMANENT LINES |

> In this mode `garbage messiness` is only decided by Fatigue, original systems are completely ignored  
> After receiving “disable reviving” buff, revival tasks are locked to the impossible X rank task

### PENTR.IO (The Fool)

> A journey of one thousand six hundred fifty meters starts with a single step.

 Exclusive to 2025 April Fools event, free to play for a week
 
 - Pentominoes  
 - ASC-DX rotation system (same idea as ASC, but range expanded from ±2 to ±3)  
 - Garbo's personally drawn monochromatic sketch background
 - If【Duo】is also enabled, revive tasks will become a “Clear 4*revive difficulty lines”
 - When activating every mod (except for【Duo】), mod combination name is “WHY”

 ASC-DX's kick table (clockwise and 0←→2's 180°, counterclockwise and 1←→3's 180° is mirror symmetrical):
 ```
 35 34 33 __ __ __ __
 28 27 26 25 __ __ __
 22 20 19 18 31 __ __
 _9 _7 _1 _0 16 24 __
 10 _8 _3 _2 17 29 36
 13 11 _5 _4 21 30 37
 15 14 12 _6 23 32 38
 ```
 
 ### Rev. 펜트리오 (A Fool's Errand)
 
 > You'll never escape who you are.
 
 2025 April Fools event similarly to【PENTR.IO】, requires climbing 2500m with【PENTR.IO】to unlock
 
 -【PENTR.IO】's base but changed to hexominoes
   
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

In all Fatigue systems `+X% received attack` will be correspondingly increased to 2 (3) times due to 【Volatile Garbage(+)】, same as multiplication

## Special thanks

Thanks to ThTsOd for providing formatted code and partial interpreting

Thanks to friends in the group chat for testing, indicating problems and helping fixing

## Some unsure if useful technological bonus information

If you want to search for variables, here are some integer names below:

1. `level` rank
1. `experience` climb_pts
1. `Promotion fatigue` promotion_fatigue, rank_locked_until
1. `Targeting factor` targetingfactor
1. `Targeting grace` targetinggrace
1. `Mods` zenith_[modname]
1. `Reverse mods` [modname]_reverse
1. `Change between attacks` messiness_change
1. `Change during attack` messiness_inner
1. `Garbage difficulty` garbagefavor
1. `Garbage gathering` messiness_center
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
    SpeedrunReq = [7, 8, 8, 9, 9, 10, 0, 0, 0, 0, 0]; // [0] stores minimum level before exiting
    TargetingGrace = [0, 4.8, 3.9, 2.1, 1.4, 1.3, .9, .6, .4, .3, .2]; // Targeting Grace's “release interval”, this variable's name isn't written completely, same with the one below
    TargetingGraceRevEx = [0, 1, .9, .8, .7, .6, .5, .4, .3, .2, .1];
    RevNoHoldHoleSideChangeChance = [.1, .1, .15, .2, .25, .3, .35, .4, .45, .5, .55];
    ReviveLevelIncrease = [1, 1, 1, 1, 1, 1, 2, 2, 2, 2, 3];
    CancelingFatigueBumpCap = [4, 4, 5, 6, 7, 8, 9, 10, 1 / 0, 1 / 0, 1 / 0];
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
            let leakSpeed = ...; // Solo:Normal3 Expert5  Duo:3+players with Expert
            this.S.zenith.climb_pts -= leakSpeed * (rank ** 2 + rank) / 3600 // climb_pts is current experience
        }

        const nextRankXP = 4 * rank;
        const storedXP = 4 * (rank - 1);
        if (this.S.zenith.climb_pts < 0)
            // Demotion
            if (rank <= 1)
                // Won't fall to under level 0
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
            // Climb Speed gaining altitude over time
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

        // Garbage difficulty
        this.S.setoptions.garbagefavor = MOD_volatileRev ? 50 : (MOD_expert ? 0 : 33) - 3 * floor - (MOD_messy ? 25 : 0);

        // Garbage waiting time
        this.S.setoptions.garbagephase = MOD_expert ? 66 - 6 * floor : 165 - 15 * floor;
        if (MOD_anyRev && !MOD_expert)
            this.S.setoptions.garbagephase = (MOD_messyRev || MOD_volatileRev || MOD_doubleholeRev) ? 75 : [75, 75, 75, 75, 75, 75, 75, 60, 45, 30, 15][floor];

        // Garbage line protection, open/close Targeting Factor based off of garbage line count
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
    function getHolePosition() { // Calculations related to garbage hole position, mainly to deal with Garbage difficulty (used Copilot to organize source code, can't confirm fully correct)
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

                // For every column, first find the lowest empty tile, track this column's “dig hardness”
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

                // Rank every column based off the dig hardness from high to low
                scores.sort((e, t) => t[1] - e[1]);

                // Calculate every column's weight based off favor amount, which means decide whether to incline towards high or low dig hardness
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
            // This block is affected by 【Duo+】 and is obsolete
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
