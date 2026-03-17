# Displays & Holos Command Cheatsheet — AstroPixels Plus

All Marcduino commands end with `\r` (carriage return). The `@` prefix is optional and ignored.

---

## 1. Display commands (Front / Rear / All Logics)

### 1.1 Sequence modes per display

| Command | Description |
|---------|-------------|
| `@1T1` | Front Logics → Normal |
| `@1T2` | Front Logics → Flashing Color (06) |
| `@1T3` | Front Logics → Alarm (01) |
| `@1T4` | Front Logics → Failure (02) |
| `@1T5` | Front Logics → Red Alert (11) |
| `@1T6` | Front Logics → Leia (03) |
| `@1T11` | Front Logics → March (04) |
| `@2T1` | Rear Logics → Normal |
| `@2T2` | Rear Logics → Flashing Color (06) |
| `@2T3` | Rear Logics → Alarm (01) |
| `@2T4` | Rear Logics → Failure (02) |
| `@2T5` | Rear Logics → Red Alert (11) |
| `@2T6` | Rear Logics → Leia (03) |
| `@2T11` | Rear Logics → March (04) |
| `@0T1` | **All** Logics → Normal |
| `@0T2` | **All** Logics → Flashing Color (06) |
| `@0T3` | **All** Logics → Alarm (01) |
| `@0T4` | **All** Logics → Failure (02) |
| `@0T5` | **All** Logics → Red Alert (11) |
| `@0T6` | **All** Logics → Leia (03) |
| `@0T11` | **All** Logics → March (04) |

**Designators:** `0` = all, `1` = front, `2` = rear.

---

### 1.2 Text on displays

| Command | Description |
|---------|-------------|
| `@1M<text>` | Text on top front logics, scroll left. e.g. `@1MHello` |
| `@2M<text>` | Text on bottom front logics, scroll left. e.g. `@2MWorld` |
| `@3M<text>` | Text on rear logics, scroll left. e.g. `@3MAstromech` |

---

### 1.3 Display font

| Command | Description |
|---------|-------------|
| `@1P60` | Front logics → Latin font |
| `@2P60` | Front logics (bottom) → Latin font |
| `@3P60` | Rear logics → Latin font |
| `@1P61` | Front logics → Aurabesh font |
| `@2P61` | Front logics (bottom) → Aurabesh font |
| `@3P61` | Rear logics → Aurabesh font |

---

### 1.4 Advanced sequences @APLE (Logic + Effect + Color + Speed + Time)

Format: `@APLE` + integer `LEECSNN`

| Field | Meaning | Values |
|-------|---------|--------|
| **L** | Logic (optional, default 0) | `0` = All, `1` = Front, `2` = Rear |
| **EE** | Effect | See effect table below |
| **C** | Color | `1` Red, `2` Orange, `3` Yellow, `4` Green, `5` Cyan, `6` Blue, `7` Purple, `8` Magenta, `9` Pink, `0` default |
| **S** | Speed/sensitivity (1–9, 5 = normal) | Depends on effect |
| **NN** | Duration in seconds (2 digits) | `00` = continuous for most |

#### Effects (EE)

| EE | Effect |
|----|--------|
| 00 | Reset to Normal |
| 01 | Alarm (alternates color and red) |
| 02 | Failure (color and brightness fade cycle) |
| 03 | Leia (pale green) |
| 04 | March (Imperial March) |
| 05 | Single Color |
| 06 | Flashing Color |
| 07 | Flip Flop Color |
| 08 | Flip Flop Alt |
| 09 | Color Swap |
| 10 | Rainbow |
| 11 | Red Alert |
| 12 | Mic Bright (brightness from mic input) |
| 13 | Mic Rainbow |
| 14 | Lights out |
| 15 | Display Text |
| 16 | Text Scrolling Left |
| 17 | Text Scrolling Right |
| 18 | Text Scrolling Up |
| 19 | Roaming pixel |
| 21 | Vertical scan line |
| 22 | Fire |
| 23 | PSI style color wipe |
| 99 | Random |

#### @APLE examples

| Command | Description |
|---------|-------------|
| `@APLE51000` | Solid red |
| `@APLE52000` | Solid orange |
| `@APLE54008` | Solid green for 8 s |
| `@APLE10500` | Alarm (default) |
| `@APLE20000` | Failure |
| `@APLE30000` | Leia |
| `@APLE40500` | March |
| `@APLE41500` | March red only |
| `@APLE63500` | Yellow flash |
| `@APLE100500` | Rainbow |
| `@APLE111300` | Red Alert |
| `@APLE124200` | Mic Bright green |
| `@APLE135000` | Mic Rainbow cyan |
| `@APLE225000` | Fire |
| `@APLE63315` | Yellow flash faster, 15 s |

---

## 2. Holo commands

Optional Marcduino prefix: `@`. Commands with `*` also valid. All end with `\r`.

### 2.1 On / off

| Command | Description |
|---------|-------------|
| `*ON01` | Front holo ON (random color cycle) |
| `*OF01` | Front holo OFF |
| `*ON02` | Rear holo ON |
| `*OF02` | Rear holo OFF |
| `*ON03` | Top holo ON |
| `*OF03` | Top holo OFF |
| `*ST00` | Reset all holos |
| `*OF04` | Radar Eye OFF |

### 2.2 Marcduino-style holos (same as *ON/*OF)

| Command | Description |
|---------|-------------|
| `@6T1` | Front holo ON |
| `@6D` | Front holo OFF |
| `@7T1` | Top holo ON |
| `@7D` | Top holo OFF |
| `@8T1` | Rear holo ON |
| `@8D` | Rear holo OFF |

### 2.3 Effect modes (pulse, rainbow, random, Radar Eye)

| Command | Description |
|---------|-------------|
| `*HPS301` | Front holo pulse |
| `*HPS302` | Rear holo pulse |
| `*HPS303` | Top holo pulse |
| `*HPS601` | Front holo rainbow |
| `*HPS602` | Rear holo rainbow |
| `*HPS603` | Top holo rainbow |
| `*RD01` | Front holo random move |
| `*RD02` | Rear holo random move |
| `*RD03` | Top holo random move |
| `*HRS3` | Radar Eye pulse |
| `*HRSR` | Radar Eye pulse red |
| `*HRS6` | Radar Eye rainbow |
| `*HRS4` | Radar Eye random color cycle |

### 2.4 Holo position (Front = 01, Rear = 02, Top = 03)

| Command | Position | Front | Rear | Top |
|---------|----------|-------|------|-----|
| `*HP001` / `*HP002` / `*HP003` | Down | ✓ | ✓ | ✓ |
| `*HP101` / `*HP102` / `*HP103` | Center | ✓ | ✓ | ✓ |
| `*HP201` / `*HP202` / `*HP203` | Up | ✓ | ✓ | ✓ |
| `*HP301` / `*HP302` / `*HP303` | Left | ✓ | ✓ | ✓ |
| `*HP401` / `*HP402` / `*HP403` | Upper left | ✓ | ✓ | ✓ |
| `*HP501` / `*HP502` / `*HP503` | Lower left | ✓ | ✓ | ✓ |
| `*HP601` / `*HP602` / `*HP603` | Right | ✓ | ✓ | ✓ |
| `*HP701` / `*HP702` / `*HP703` | Upper right | ✓ | ✓ | ✓ |
| `*HP801` / `*HP802` / `*HP803` | Lower right | ✓ | ✓ | ✓ |

### 2.5 Movements (wag = left/right, nod = up/down)

| Command | Description |
|---------|-------------|
| `*HW01` | Front holo wag (5 times) |
| `*HW02` | Rear holo wag (5 times) |
| `*HW03` | Top holo wag (5 times) |
| `*HN01` | Front holo nod (5 times) |
| `*HN02` | Rear holo nod (5 times) |
| `*HN03` | Top holo nod (5 times) |

### 2.6 Direct HP commands (internal protocol)

Send raw HP commands to the firmware:

| Command | Description |
|---------|-------------|
| `@HP<rest>` | Sends `HP` + rest of command to holos |
| `*HP<rest>` | Same as `@HP`; `*` prefix also allowed |

Example (from Shadow docs): `*HPA000|0\r` equals `@HPA000|0`.

---

## 3. Low-level commands — HP protocol (holos)

These are the commands the firmware actually interprets. Send over serial as **`HP`** + rest (optional prefix `@` or `*`). Terminator: `\r`.

### 3.1 General format

```
HP + D + T + NN [+ options] [+ |value]
```

| Part | Meaning | Values |
|------|----------|--------|
| **D** | Designator (which holo(s)) | See table below |
| **T** | Type | `0` = LED, `1` = Servo |
| **NN** | Function (2 digits) | 00, 01, 02, … 99 |
| **options** | Optional param(s) | C, S, R, P (see below) |
| **\|value** | Duration in seconds (or repeat count for wag/nod) | e.g. `|20` = 20 s |

**Designators (D):**

| Code | Holo(s) affected |
|------|-------------------|
| `F` | Front |
| `R` | Rear |
| `T` | Top |
| `D` | Radar Eye |
| `O` | Other |
| `A` | All (Front, Rear, Top) |
| `X` | Front and Rear |
| `Y` | Front and Top |
| `Z` | Rear and Top |
| `S` | Sequences (S1, S2, …) |

**Options by command:**

- **C** = Color (1 digit): `0` Random, `1` Red, `2` Yellow, `3` Green, `4` Cyan, `5` Blue, `6` Magenta, `7` Orange, `8` Purple, `9` White  
- **S** = Speed/sensitivity (0–9), e.g. for Dim Pulse  
- **R** = Random state when clearing: `1` default sequences, `2` random sequences  
- **P** = Position (servo): `0` Down, `1` Center, `2` Up, `3` Left, `4` Upper Left, `5` Lower Left, `6` Right, `7` Upper Right, `8` Lower Right  

---

### 3.2 LED effects you can use (holos)

Format: **HP** + designator (**F** Front, **R** Rear, **T** Top, **D** Radar Eye, **A** All) + **0** + **NN** + options.  
**`*HPR0013`** = Rear holo, effect **01** (Leia). Does what you want (Leia blue/white); the **last digit (3) is ignored** for effect 01.

**Colors (C):** `0` Random, `1` Red, `2` Yellow, `3` Green, `4` Cyan, `5` Blue, `6` Magenta, `7` Orange, `8` Purple, `9` White.

| Code | Effect | Params | Used? | Example |
|------|--------|--------|-------|---------|
| **00** | Off | — | — | `HPR0000`, `HPF0000` |
| **01** | Leia (blue/white, hologram) | 1 digit optional | **Ignored** | `*HPR0013\r`, `*HPF001\r` |
| **02** | Color Projector (Leia with color) | **C** | Yes | `HPF0023` green, `HPR0025` blue |
| **03** | Dim Pulse | **C**, **S** (0–9) | Yes | `HPF00335` |
| **04** | Cycle | **C** | Yes | `HPF0040` = random (`*ON01`) |
| **05** | Solid color | **C** | Yes | `HPR0051` red |
| **06** | Rainbow | — | — | `HPF006`, `HPA006` |
| **07** | Short Circuit | **C** | Yes | `HPF0075` blue |
| 096–099 | Clear / auto LED state | by command | Yes | See full table below |

**Parsing:** After `HP`+designator+**0** come **2 digits** = function; optional next = param. For **01** that param is **not used**.

---

**Full reference (LED commands):**

| Low-level command | Description |
|-------------------|-------------|
| `HPF00` / `HPR00` / `HPT00` / `HPD00` / `HPA00` | Off |
| `HPF001` / `HPR001` / `HPF0013` / `HPR0013` / … | Leia. Extra digit **ignored**. |
| `HPF002C` / `HPR002C` / … | Color Projector: **C**. |
| `HPF003CS` / `HPR003CS` / … | Dim Pulse: **C**, **S** (0–9). |
| `HPF004C` / `HPR004C` / … | Cycle: **C**. |
| `HPF005C` / `HPR005C` / … | Solid color **C**. |
| `HPF006` / `HPR006` / … | Rainbow. |
| `HPF007C` / `HPR007C` / … | Short Circuit: **C**. |
| `HPF096` / `HPR096` / … | Clear LED, disable auto LED and “Off Color”. |
| `HPF0971` / `HPR0971` / … | Clear, enable auto LED, default sequences, no “Off Color”. |
| `HPF0972` / … | Clear, enable auto LED, random sequences, no “Off Color”. |
| `HPF098` / … | Clear, disable auto LED, enable “Off Color”. |
| `HPF0991` / … | Clear, auto LED, default sequences, with “Off Color”. |
| `HPF0992` / … | Clear, auto LED, random sequences, with “Off Color”. |

**Examples:**

- The “3” is ignored.  

- `*HPR0013\r` → Rear, Leia (blue/white). Last digit ignored.  
- `*HPF001\r` → Front, Leia (same as 0013).  
- `HPR0000\r` → Rear, off.  
- `HPF0023\r` → Front, Color Projector green.  
- `HPF0040\r` → Front, Cycle random (`*ON01`).  
- `HPF0000\r` → Front, off (`*OF01`).  
- `HPA006|25\r` → Rainbow on all 3 holos for 25 s.

**Note:** For hologram-style in **green** (or other color), use **HPF0023** (Color Projector color 3 = Green), not 001.  

---

### 3.3 Servo commands (T = 1): HP**D**1**NN**[P]

| Low-level command | Description |
|-------------------|-------------|
| `HPF101P` / `HPR101P` / `HPT101P` / … | Go to position **P** (0–8). See position table above. |
| `HPF102` / `HPR102` / … | RC Control Left/Right (if supported). |
| `HPF103` / … | RC Control Up/Down (if supported). |
| `HPF104` / `HPR104` / `HPT104` / … | Random position. |
| `HPF105[|n]` / `HPR105[|n]` / … | Wag (left/right). Optional `|n` = repeat count (e.g. `|5`). |
| `HPF106[|n]` / `HPR106[|n]` / … | Nod (up/down). Optional `|n` = repeat count. |
| `HPF198` / … | Disable Auto HP Twitch. |
| `HPF199` / … | Enable Auto HP Twitch. |

**Positions P (for 101):**  
`0` Down, `1` Center, `2` Up, `3` Left, `4` Upper Left, `5` Lower Left, `6` Right, `7` Upper Right, `8` Lower Right.

**Examples:**

- `HPF1010` → Front, Down.  
- `HPF1011` → Front, Center.  
- `HPR1013` → Rear, Left.  
- `HPF104` → Front, random position.  
- `HPF105|5` → Front, wag 5 times.  
- `HPA0000` → Reset all (same as `*ST00`).  

---

### 3.4 Global sequences (S): HP**S**N

| Low-level command | Description |
|-------------------|-------------|
| `HPS1` | Leia mode (Front in Down + Leia LED, others disabled). |
| `HPS4` | Clear LEDs, disable Auto HP Twitch and Auto LED, no “Off Color”. |
| `HPS5` | Clear, enable Auto HP Twitch and Auto LED (default sequences), no “Off Color”. |
| `HPS7` | Clear, disable Auto HP Twitch and Auto LED, with “Off Color”. |
| `HPS8` | Clear, enable Auto HP Twitch and Auto LED (default), with “Off Color”. |
| `HPS9` | Clear, enable Auto HP Twitch and Auto LED (random), with/without “Off Color”. |

---

### 3.5 High-level → low-level mapping (holos)

| Marcduino command (* / @) | Equivalent low-level command |
|---------------------------|------------------------------|
| `*ON01` | `HPF0040` (Front, cycle random) |
| `*OF01` | `HPF0000` |
| `*ON02` | `HPR0040` |
| `*OF02` | `HPR0000` |
| `*ON03` | `HPT0040` |
| `*OF03` | `HPT0000` |
| `*ST00` | `HPA0000` |
| `*OF04` | `HPD0000` (Radar Eye) |
| `*HPS301` | `HPF0030` (Front, Dim Pulse random) |
| `*HPS302` | `HPR0030` |
| `*HPS303` | `HPT0030` |
| `*HPS601` | `HPF006` |
| `*HPS602` | `HPR006` |
| `*HPS603` | `HPT006` |
| `*RD01` | `HPF104` |
| `*RD02` | `HPR104` |
| `*RD03` | `HPT104` |
| `*HP001` (Front down) | `HPF1010` |
| `*HP101` (Front center) | `HPF1011` |
| … (positions) | `HPx1PP` with P = 0..8 |
| `*HW01` | `HPF105|5` |
| `*HN01` | `HPF106|5` |

To send directly over serial: **`*HP`** + rest or **`@HP`** + rest (e.g. `*HPR0013\r`, `*HPF0000\r`, `*HPF1011\r`).

---

## 4. Quick reference

- **Displays:** `@0T` / `@1T` / `@2T` (mode), `@1M` / `@2M` / `@3M` (text), `@1P` / `@2P` / `@3P` (font), `@APLE...` (advanced sequences).
- **Holos (high-level):** `*ON0n` / `*OF0n` (on/off), `*ST00` (reset), `*HPS30n` (pulse), `*HPS60n` (rainbow), `*RD0n` (random move), `*HPxyz` (position), `*HW0n` (wag), `*HN0n` (nod), `*HRS*` (Radar Eye).
- **Holos (low-level):** send `*HP` or `@HP` + designator (F/R/T/D/A/…) + type (0=LED, 1=Servo) + NN + options + optional `|seconds`. Parsing: e.g. `HPF0013` = F + 0 + **01** (function) + **3** (option); the "13" is not "option 13". Examples: `*HPR0013\r`, `*HPF0000\r`, `*HPF1011\r`, `*HPA007|25\r`.
