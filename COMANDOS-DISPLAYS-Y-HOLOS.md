# Comandos de Displays (Lógicas) y Holos — AstroPixels Plus

Todos los comandos Marcduino terminan con `\r` (retorno de carro). El prefijo `@` es opcional y se ignora.

---

## 1. Comandos de displays (Front / Rear / All Logics)

### 1.1 Modos de secuencia por display

| Comando | Descripción |
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

**Designadores:** `0` = todos, `1` = frontal, `2` = trasero.

---

### 1.2 Texto en displays

| Comando | Descripción |
|---------|-------------|
| `@1M<texto>` | Texto en logics frontales superiores, scroll izquierda. Ej: `@1MHello` |
| `@2M<texto>` | Texto en logics frontales inferiores, scroll izquierda. Ej: `@2MWorld` |
| `@3M<texto>` | Texto en logics traseros, scroll izquierda. Ej: `@3MAstromech` |

---

### 1.3 Fuente del display

| Comando | Descripción |
|---------|-------------|
| `@1P60` | Front logics → fuente Latin |
| `@2P60` | Front logics (inferior) → fuente Latin |
| `@3P60` | Rear logics → fuente Latin |
| `@1P61` | Front logics → fuente Aurabesh |
| `@2P61` | Front logics (inferior) → fuente Aurabesh |
| `@3P61` | Rear logics → fuente Aurabesh |

---

### 1.4 Secuencias avanzadas @APLE (Logic + Effect + Color + Speed + Time)

Formato: `@APLE` + entero `LEECSNN`

| Campo | Significado | Valores |
|-------|-------------|--------|
| **L** | Logic (opcional, por defecto 0) | `0` = All, `1` = Front, `2` = Rear |
| **EE** | Efecto | Ver tabla de efectos abajo |
| **C** | Color | `1` Rojo, `2` Naranja, `3` Amarillo, `4` Verde, `5` Cyan, `6` Azul, `7` Púrpura, `8` Magenta, `9` Rosa, `0` por defecto |
| **S** | Velocidad/sensibilidad (1–9, 5 = normal) | Depende del efecto |
| **NN** | Duración en segundos (2 dígitos) | `00` = continuo en la mayoría |

#### Efectos (EE)

| EE | Efecto |
|----|--------|
| 00 | Reset to Normal |
| 01 | Alarm (alterna color y rojo) |
| 02 | Failure (ciclo de colores y brillo) |
| 03 | Leia (verde pálido) |
| 04 | March (Imperial March) |
| 05 | Single Color |
| 06 | Flashing Color |
| 07 | Flip Flop Color |
| 08 | Flip Flop Alt |
| 09 | Color Swap |
| 10 | Rainbow |
| 11 | Red Alert |
| 12 | Mic Bright (brillo según micrófono) |
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

#### Ejemplos @APLE

| Comando | Descripción |
|---------|-------------|
| `@APLE51000` | Rojo sólido |
| `@APLE52000` | Naranja sólido |
| `@APLE54008` | Verde sólido 8 s |
| `@APLE10500` | Alarm (por defecto) |
| `@APLE20000` | Failure |
| `@APLE30000` | Leia |
| `@APLE40500` | March |
| `@APLE41500` | March solo rojo |
| `@APLE63500` | Flash amarillo |
| `@APLE100500` | Rainbow |
| `@APLE111300` | Red Alert |
| `@APLE124200` | Mic Bright verde |
| `@APLE135000` | Mic Rainbow cyan |
| `@APLE225000` | Fire |
| `@APLE63315` | Flash amarillo más rápido, 15 s |

---

## 2. Comandos de holos

Prefijo Marcduino opcional: `@`. Comandos con `*` también válidos. Todos terminan en `\r`.

### 2.1 Encendido / apagado

| Comando | Descripción |
|---------|-------------|
| `*ON01` | Front holo ON (ciclo color aleatorio) |
| `*OF01` | Front holo OFF |
| `*ON02` | Rear holo ON |
| `*OF02` | Rear holo OFF |
| `*ON03` | Top holo ON |
| `*OF03` | Top holo OFF |
| `*ST00` | Reset todos los holos |
| `*OF04` | Radar Eye OFF |

### 2.2 Holos en estilo Marcduino (mismo efecto que *ON/*OF)

| Comando | Descripción |
|---------|-------------|
| `@6T1` | Front holo ON |
| `@6D` | Front holo OFF |
| `@7T1` | Top holo ON |
| `@7D` | Top holo OFF |
| `@8T1` | Rear holo ON |
| `@8D` | Rear holo OFF |

### 2.3 Modos de efecto (pulse, rainbow, random, Radar Eye)

| Comando | Descripción |
|---------|-------------|
| `*HPS301` | Front holo pulse |
| `*HPS302` | Rear holo pulse |
| `*HPS303` | Top holo pulse |
| `*HPS601` | Front holo rainbow |
| `*HPS602` | Rear holo rainbow |
| `*HPS603` | Top holo rainbow |
| `*RD01` | Front holo movimiento aleatorio |
| `*RD02` | Rear holo movimiento aleatorio |
| `*RD03` | Top holo movimiento aleatorio |
| `*HRS3` | Radar Eye pulse |
| `*HRSR` | Radar Eye pulse rojo |
| `*HRS6` | Radar Eye rainbow |
| `*HRS4` | Radar Eye ciclo color aleatorio |

### 2.4 Posición del holo (Front = 01, Rear = 02, Top = 03)

| Comando | Posición | Front | Rear | Top |
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

### 2.5 Movimientos (wag = izquierda/derecha, nod = arriba/abajo)

| Comando | Descripción |
|---------|-------------|
| `*HW01` | Front holo wag (5 veces) |
| `*HW02` | Rear holo wag (5 veces) |
| `*HW03` | Top holo wag (5 veces) |
| `*HN01` | Front holo nod (5 veces) |
| `*HN02` | Rear holo nod (5 veces) |
| `*HN03` | Top holo nod (5 veces) |

### 2.6 Comandos HP directos (protocolo interno)

Permiten enviar órdenes HP crudas al firmware:

| Comando | Descripción |
|---------|-------------|
| `@HP<resto>` | Envía `HP` + resto del comando al sistema de holos |
| `*HP<resto>` | Igual que `@HP`; el prefijo `*` también está permitido |

Ejemplo (desde documentación Shadow): `*HPA000|0\r` equivale a `@HPA000|0`.

---

## 3. Comandos de bajo nivel — Protocolo HP (holos)

Estos son los comandos que el firmware interpreta realmente. Se envían por serial como **`HP`** + resto (con prefijo opcional `@` o `*`). Terminador: `\r`.

### 3.1 Formato general

```
HP + D + T + NN [+ opciones] [+ |valor]
```

| Parte | Significado | Valores |
|-------|-------------|--------|
| **D** | Designador (qué holo(s)) | Ver tabla abajo |
| **T** | Tipo | `0` = LED, `1` = Servo |
| **NN** | Función (2 dígitos) | 00, 01, 02, … 99 |
| **opciones** | Parámetro(s) opcional(es) | C, S, R, P (ver abajo) |
| **\|valor** | Duración en segundos (o repeticiones en wag/nod) | Ej: `\|20` = 20 s |

**Designadores (D):**

| Código | Holo(s) afectado(s) |
|--------|----------------------|
| `F` | Front |
| `R` | Rear |
| `T` | Top |
| `D` | Radar Eye |
| `O` | Other |
| `A` | All (los 3: Front, Rear, Top) |
| `X` | Front y Rear |
| `Y` | Front y Top |
| `Z` | Rear y Top |
| `S` | Secuencias (S1, S2, …) |

**Opciones según comando:**

- **C** = Color (1 dígito): `0` Random, `1` Red, `2` Yellow, `3` Green, `4` Cyan, `5` Blue, `6` Magenta, `7` Orange, `8` Purple, `9` White  
- **S** = Velocidad/sensibilidad (0–9), p. ej. en Dim Pulse  
- **R** = Estado random al limpiar: `1` secuencias por defecto, `2` secuencias aleatorias  
- **P** = Posición (servo): `0` Down, `1` Center, `2` Up, `3` Left, `4` Upper Left, `5` Lower Left, `6` Right, `7` Upper Right, `8` Lower Right  

---

### 3.2 Efectos LED que puedes usar (holos)

Formato: **HP** + designador (**F** Front, **R** Rear, **T** Top, **D** Radar Eye, **A** All) + **0** + **NN** + opciones.  
**`*HPR0013`** = Rear holo, efecto **01** (Leia). Hace el efecto Leia (azul/blanco); el **último dígito (3) se ignora** en 01.

**Colores (C):** `0` Random, `1` Red, `2` Yellow, `3` Green, `4` Cyan, `5` Blue, `6` Magenta, `7` Orange, `8` Purple, `9` White.

| Código | Efecto | Parámetros | ¿Se usan? | Ejemplo |
|--------|--------|------------|-----------|---------|
| **00** | Apagado | — | — | `HPR0000`, `HPF0000` |
| **01** | Leia (azul/blanco, holograma) | 1 dígito opcional | **Se ignora** | `*HPR0013\r`, `*HPF001\r` |
| **02** | Color Projector (Leia con color) | **C** | Sí | `HPF0023` verde, `HPR0025` azul |
| **03** | Dim Pulse (pulso suave) | **C**, **S** (0–9) | Sí | `HPF00335` |
| **04** | Cycle | **C** | Sí | `HPF0040` = random (`*ON01`) |
| **05** | Color sólido | **C** | Sí | `HPR0051` rojo |
| **06** | Rainbow | — | — | `HPF006`, `HPA006` |
| **07** | Short Circuit | **C** | Sí | `HPF0075` azul |
| 096–099 | Limpiar / auto LED | según comando | Sí | Ver tabla abajo |

**Parseo:** Tras `HP`+designador+**0** van **2 dígitos** = función; el siguiente opcional = parámetro. En **01** ese parámetro **no se usa**.

---

**Referencia completa (comandos LED):**

| Comando bajo nivel | Descripción |
|--------------------|-------------|
| `HPF00` / `HPR00` / `HPT00` / `HPD00` / `HPA00` | Apagado |
| `HPF001` / `HPR001` / `HPF0013` / `HPR0013` / … | Leia. Dígito extra **ignorado**. |
| `HPF002C` / `HPR002C` / … | Color Projector: **C**. |
| `HPF003CS` / `HPR003CS` / … | Dim Pulse: **C**, **S** (0–9). |
| `HPF004C` / `HPR004C` / … | Cycle: **C**. |
| `HPF005C` / `HPR005C` / … | Color sólido **C**. |
| `HPF006` / `HPR006` / … | Rainbow. |
| `HPF007C` / `HPR007C` / … | Short Circuit: **C**. |
| `HPF096` / `HPR096` / … | Limpiar LED, desactivar auto LED y “Off Color”. |
| `HPF0971` / `HPR0971` / … | Limpiar, activar auto LED, secuencias por defecto, sin “Off Color”. |
| `HPF0972` / … | Limpiar, activar auto LED, secuencias aleatorias, sin “Off Color”. |
| `HPF098` / … | Limpiar, desactivar auto LED, activar “Off Color”. |
| `HPF0991` / … | Limpiar, auto LED, secuencias por defecto, con “Off Color”. |
| `HPF0992` / … | Limpiar, auto LED, secuencias aleatorias, con “Off Color”. |

**Cómo se parsea el final:** los dígitos después de `HP` + designador + tipo son **siempre**:
- **2 dígitos** = función (NN): 00, 01, 02…
- **Opcional** 1.º dígito = opción (C/S/R/P según el comando)

Ejemplo `HPF0013`: se lee como **HP** + **F** + **0** + **01** + **3** → Front, LED, función **01** (Leia), opción **3**. El «13» no es “opción 13”: el **1** forma la función **01**, el **3** es la opción (y en Leia esa opción no se usa).

**Ejemplos:**

- `*HPR0013\r` → Rear, Leia (azul/blanco). El último dígito se ignora.  
- `*HPF001\r` → Front, Leia (mismo efecto que 0013).  
- `HPR0000\r` → Rear, off.  
- `HPF0040\r` → Front, Cycle con color 0 (Random) — es lo que hace `*ON01`.  
- `HPF0000\r` → Front, off — equivale a `*OF01`.  
- `HPA007|25\r` → Rainbow en los 3 holos durante 25 s.

**Nota:** Para un efecto tipo holograma pero en **verde** (u otro color), usa **HPF0023** (Color Projector con color 3 = Green), no 001.  

---

### 3.4 Comandos Servo (T = 1): HP**D**1**NN**[P]

| Comando bajo nivel | Descripción |
|--------------------|-------------|
| `HPF101P` / `HPR101P` / `HPT101P` / … | Ir a posición **P** (0–8). Ver tabla de posiciones arriba. |
| `HPF102` / `HPR102` / … | RC Control Left/Right (si está soportado). |
| `HPF103` / … | RC Control Up/Down (si está soportado). |
| `HPF104` / `HPR104` / `HPT104` / … | Posición aleatoria. |
| `HPF105[|n]` / `HPR105[|n]` / … | Wag (izq/der). Opcional `|n` = número de veces (ej. `\|5`). |
| `HPF106[|n]` / `HPR106[|n]` / … | Nod (arriba/abajo). Opcional `|n` = número de veces. |
| `HPF198` / … | Desactivar Auto HP Twitch. |
| `HPF199` / … | Activar Auto HP Twitch. |

**Posiciones P (para 101):**  
`0` Down, `1` Center, `2` Up, `3` Left, `4` Upper Left, `5` Lower Left, `6` Right, `7` Upper Right, `8` Lower Right.

**Ejemplos:**

- `HPF1010` → Front, posición Down.  
- `HPF1011` → Front, Center.  
- `HPR1013` → Rear, Left.  
- `HPF104` → Front, posición aleatoria.  
- `HPF105|5` → Front, wag 5 veces.  
- `HPA0000` → Reset todos (equivale a `*ST00`).  

---

### 3.5 Secuencias globales (S): HP**S**N

| Comando bajo nivel | Descripción |
|--------------------|-------------|
| `HPS1` | Leia mode (Front en Down + Leia LED, resto desactivados). |
| `HPS4` | Limpiar LEDs, desactivar Auto HP Twitch y Auto LED, sin “Off Color”. |
| `HPS5` | Limpiar, activar Auto HP Twitch y Auto LED (secuencias por defecto), sin “Off Color”. |
| `HPS7` | Limpiar, desactivar Auto HP Twitch y Auto LED, con “Off Color”. |
| `HPS8` | Limpiar, activar Auto HP Twitch y Auto LED (por defecto), con “Off Color”. |
| `HPS9` | Limpiar, activar Auto HP Twitch y Auto LED (aleatorio), con/sin “Off Color”. |

---

### 3.6 Equivalencia alto nivel → bajo nivel (holos)

| Comando Marcduino (* / @) | Comando bajo nivel equivalente |
|---------------------------|--------------------------------|
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
| … (posiciones) | `HPx1PP` con P = 0..8 |
| `*HW01` | `HPF105|5` |
| `*HN01` | `HPF106|5` |

Para enviar directamente desde serial: **`*HP`** + resto o **`@HP`** + resto (ej: `*HPR0013\r`, `*HPF0000\r`, `*HPF1011\r`).

---

## 4. Resumen rápido

- **Displays:** `@0T` / `@1T` / `@2T` (modo), `@1M` / `@2M` / `@3M` (texto), `@1P` / `@2P` / `@3P` (fuente), `@APLE...` (secuencias avanzadas).
- **Holos (alto nivel):** `*ON0n` / `*OF0n` (on/off), `*ST00` (reset), `*HPS30n` (pulse), `*HPS60n` (rainbow), `*RD0n` (random move), `*HPxyz` (posición), `*HW0n` (wag), `*HN0n` (nod), `*HRS*` (Radar Eye).
- **Holos (bajo nivel):** enviar `*HP` o `@HP` + designador (F/R/T/D/A/…) + tipo (0=LED, 1=Servo) + NN + opciones + opcional `|segundos`. Ejemplos: `*HPR0013\r`, `*HPF0000\r`, `*HPF1011\r`, `*HPA007|25\r`.
