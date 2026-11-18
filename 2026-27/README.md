# Sistemes Digitals — Curs 2026-27

- [Projecte Sistemes Combinacionals: ALU de 3 bits](#projecte-sistemes-combinacionals--alu-de-3-bits)
- [Projecte Sistemes Seqüencials](#projecte-sistemes-seqüencials)

---

## Projecte Sistemes Combinacionals — ALU de 3 bits

<!-- Afegir aquí una captura de solucio.dig -->

📁 [`Projecte - Sistemes Combinacionals/`](Projecte%20-%20Sistemes%20Combinacionals/)

### Descripció
**Unitat Aritmètico-Lògica (ALU)** per a dos operands de 3 bits en **complement a 2 (C2)**. Un codi de control de 2 bits selecciona l'operació. La sortida és un resultat de 3 bits més un bit d'**overflow**.

### Operacions
| c1 c0 | Operació | Resultat |
|-------|----------|----------|
| `00` | Canvi de signe | R = −A (C2) |
| `01` | Suma | R = A + B (C2) |
| `10` | Resta | R = A − B (C2) |
| `11` | Transformació C2 → SM | R = A en Signe i Magnitud |

`overflow` val 1 quan la suma o la resta surten de rang, o quan el resultat de la transformació no es pot representar amb la sortida.

### Entrades
| Senyal | Descripció |
|--------|------------|
| `a2 a1 a0` | Operand A (C2) |
| `b2 b1 b0` | Operand B (C2) |
| `c1 c0` | Selecció de l'operació |

### Sortides
| Senyal | Descripció |
|--------|------------|
| `r2 r1 r0` | Resultat |
| `overflow` | Sobreeiximent (també es mostra en un LED) |

Displays de 7 segments (valor i signe): **A** / **sA**, **B** / **sB**, **R** / **sR**.

### Subcircuits
| Fitxer | Funció |
|--------|--------|
| `HA`, `FA` | Semisumador i sumador complet |
| `CanviSigneA(C2)` | −A en C2 |
| `SumadorC2(A+B)` | Suma en C2 amb detecció d'overflow |
| `RestadorC2(A+(-B))` | Resta com a A + (−B) |
| `TransformarAC2toASM` | Conversió de C2 a SM |
| `MUX2:1`, `MUX4:1`, `MUX16:1`, `MUXV4:1`, `MUXV4:2`, `MUXV16:8`, `MUXVFinal`, `MUXC2SM` | Multiplexors per seleccionar el resultat i la representació |
| `ALU` | Unitat aritmètico-lògica |
| `showDisplay`, `showDisplayC2`, `showDisplaySM` | Decodificadors dels displays |
| **`solucio`** | Circuit de nivell superior |

### Restriccions
- Només portes lògiques. De la llibreria de Digital només es poden fer servir **els displays i els LEDs**.
- Noms de les entrades i sortides **en minúscules**. Només els displays van en majúscules.
- Disseny modular amb subcircuits i tests obligatoris.

---

## Projecte Sistemes Seqüencials

> 🚧 **Pendent.** Aquesta secció es completarà quan es publiqui l'enunciat.

📁 `Projecte - Sistemes Sequencials/` *(encara buida)*

### Descripció
*Pendent*

### Entrades
*Pendent*

### Sortides
*Pendent*

### Disseny
*Pendent* (diagrama d'estats, codificació, tipus de flip-flop)

### Subcircuits
*Pendent*
