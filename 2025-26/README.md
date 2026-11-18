# Sistemes Digitals — Curs 2025-26

- [Projecte Sistemes Combinacionals: Caixa forta amb doble autenticació](#projecte-sistemes-combinacionals--caixa-forta-amb-doble-autenticació)
- [Projecte Sistemes Seqüencials: Canvi de marxes d'una bicicleta](#projecte-sistemes-seqüencials--canvi-de-marxes-duna-bicicleta)

---

## Projecte Sistemes Combinacionals — Caixa forta amb doble autenticació

<img width="1065" height="927" alt="Esquema del circuit de la caixa forta" src="https://github.com/user-attachments/assets/1e16ae7e-137a-4663-b062-702ac24f31c9" />

📁 [`Projecte - Sistemes Combinacionals/`](Projecte%20-%20Sistemes%20Combinacionals/)

### Descripció
Sistema combinacional de control d'accés per a una **caixa forta amb doble autenticació**, on cal que **dos usuaris** hi cooperin.

### Funcionament
- Cada usuari introdueix un **codi personal**, que es compara amb el valor guardat a una **ROM**.
- Tots dos usuaris introdueixen un **codi compartit**. Ha de coincidir entre ells i amb el **codi que calcula el sistema**.
- El codi compartit és la **suma en Signe i Magnitud (SM)** dels dos codis personals guardats a les ROM.
- El zero en SM té dues representacions (`0000` i `1000`), i es consideren iguals.

### Entrades
| Usuari | Senyal | Descripció |
|--------|--------|------------|
| 1 | `U3..U0` | Codi personal (4 bits, SM) |
| 1 | `C4..C0` | Codi compartit (5 bits, SM) |
| 2 | `V3..V0` | Codi personal (4 bits, SM) |
| 2 | `D4..D0` | Codi compartit (5 bits, SM) |

### Sortides
- Displays de 7 segments **Usuari 1** i **Usuari 2**:
  - `0`: cap codi correcte
  - `1`: codi personal correcte
  - `2`: codi personal i compartit correctes
- `VERIFICAT`: val 1 quan tots dos usuaris han validat tots els codis.
- LED verd d'accés (`LED VERIFICAT`).

### Subcircuits
| Fitxer | Funció |
|--------|--------|
| `Half-Adder`, `Full-Adder` | Semisumador i sumador complet |
| `Half-Substracter`, `Full-Substracter` | Semirestador i restador complet |
| `4Bit-Adder`, `4Bit-Substracter` | Sumador i restador de magnituds de 3 bits (amb acarreig o préstec) |
| `2Bit-Comparator`, `3BitSuperComparator` | Comparadors de magnitud (`IGUAL`, `MAJOR`, `MENOR`) |
| `MUX` | Multiplexor 2:1 |
| `MaxMinSelector` | Ordena dues magnituds (màxim i mínim) |
| `GestionDelSigno` | Signe del resultat de la suma SM |
| `5Bit-AdderSM` | Suma en SM de dos nombres de 4 bits amb resultat de 5 bits |
| `4Bit-ComparatorSM`, `5Bit-ComparatorSM` | Igualtat en SM (`+0 = −0`) |
| `showDisplay` | Decodificador del display (0 / 1 / 2) |
| **`solucio`** | Circuit de nivell superior |

### Restriccions
- Només portes lògiques. De la llibreria de Digital només es poden fer servir **la ROM, els displays i els LEDs**.
- Disseny modular amb subcircuits i tests obligatoris.

---

## Projecte Sistemes Seqüencials — Canvi de marxes d'una bicicleta

<img width="947" height="910" alt="Esquema del circuit del canvi de marxes" src="https://github.com/user-attachments/assets/45b87c01-4b3c-481d-8bd7-43ce517ee1b3" />

📁 [`Projecte - Sistemes Sequencials/`](Projecte%20-%20Sistemes%20Sequencials/)

### Descripció
Sistema seqüencial que controla el canvi de marxes d'una bicicleta amb **2 plats** i **4 pinyons**, implementat amb **flip-flops JK**.

### Modes de funcionament
- **Manual** (`Mode = 0`): els canvis de plat i de pinyó són independents.
- **Automàtic** (`Mode = 1`): en pujar o baixar de plat, també es puja o es baixa una posició de pinyó per suavitzar el canvi.
- El canvi de pinyó funciona igual en tots dos modes.

### Entrades
- `Pup` / `Pdw`: pujar / baixar plat (polsadors)
- `Cup` / `Cdw`: pujar / baixar pinyó (polsadors)
- `Mode`: selecció entre manual i automàtic

### Sortides
- Display de 7 segments amb la posició del **plat** (1–2)
- Display de 7 segments amb la posició del **pinyó** (1–4)
- `PLAT_LIMIT`: LED d'avís quan es vol fer un canvi de plat invàlid
- `PINYO_LIMIT`: LED d'avís quan es vol fer un canvi de pinyó invàlid

### Disseny
- **Màquina de Mealy**: els LEDs de límit depenen de l'estat i del botó que es prem.
- **Estat (3 bits)**: `Q2` és el plat i `Q1 Q0` el pinyó, és a dir, 8 estats.
- **Entrades codificades en 3 bits** (`CodificarEntrades`):

  | X2 X1 X0 | Acció |
  |----------|-------|
  | `000` | cap botó |
  | `001` | Cdw |
  | `010` | Cup |
  | `011` | Pdw manual |
  | `100` | Pup manual |
  | `101` | Pdw automàtic |
  | `110` | Pup automàtic |

- Rellotge amb període d'**1 segon**.

### Subcircuits
| Fitxer | Funció |
|--------|--------|
| `CodificarEntrades` | Codifica els polsadors i el mode en 3 bits |
| `J0`…`J2`, `K0`…`K2` | Entrades dels flip-flops JK |
| `PL`, `CL` | Senyals de límit de plat i de pinyó |
| `SequentialCircuit` | Flip-flops JK i lògica d'estat |
| `PlateDisplay`, `PinyoDisplay` | Decodificadors dels displays |
| **`solucio`** | Circuit de nivell superior |

> Digital no deixa que un test premi un `Button`. Per això el test seqüencial complet (les 56 transicions) és a `SequentialCircuit.dig`.
