# Projectes Digital
Projectes Finals fets amb [Digital](https://github.com/hneemann/Digital) per l'assignatura de Sistemes Digitals

## Projecte Circuits Combinacionals - Caixa Forta amb Doble Autenticació
<img width="1065" height="927" alt="image" src="https://github.com/user-attachments/assets/1e16ae7e-137a-4663-b062-702ac24f31c9" />

## Descripció
Disseny d’un sistema combinacional de control d’accés per a una **caixa forta amb doble autenticació**, on és necessària la cooperació de **dos usuaris**. El sistema es desenvolupa amb l’eina **Digital** i forma part de l’assignatura *Sistemes Digitals*.

## Funcionament
- Cada usuari introdueix un **codi personal** que es compara amb el valor emmagatzemat a una **ROM**.
- Ambdós usuaris introdueixen un **codi compartit**, que ha de coincidir entre ells i amb el **codi calculat internament** pel sistema.
- El codi compartit és la **suma en Signe i Magnitud (SM)** dels dos codis personals.

## Entrades
- **Usuari 1**
  - `U[3:0]`: codi personal (4 bits, SM)
  - `C[4:0]`: codi compartit (5 bits)
- **Usuari 2**
  - `V[3:0]`: codi personal (4 bits, SM)
  - `D[4:0]`: codi compartit (5 bits)

## Sortides
- Display de 7 segments **Usuari 1**
- Display de 7 segments **Usuari 2**
- `VERIFICAT`: sortida activa (1) quan ambdós usuaris han validat tots els codis
- LED verd d’indicació d’accés

### Valors dels Displays
- `0`: cap codi correcte  
- `1`: codi personal correcte  
- `2`: codi personal i compartit correctes  

## Restriccions
- Implementació **exclusivament amb portes lògiques**
- Ús permès només de **ROM, displays i LEDs** de Digital
- Prohibit usar mòduls predefinits o generació automàtica de circuits
- Disseny **modular** amb subcircuits i tests obligatoris
- Comparació correcta del **zero en SM** (0000 i 1000 equivalents)

---

## Projecte Circuits Sequencials - Canvi de marxes d'una Bicicleta
<img width="947" height="910" alt="image" src="https://github.com/user-attachments/assets/45b87c01-4b3c-481d-8bd7-43ce517ee1b3" />

## Descripció
Disseny d’un sistema seqüencial per controlar el canvi de marxes d’una bicicleta amb **2 plats** i **4 pinyons**, utilitzant **flip-flops JK**. El sistema forma part de l’assignatura *Sistemes Digitals* i s’ha d’implementar amb l’eina **Digital**.

## Modes de funcionament
- **Manual**: els canvis de plat i pinyó es fan de manera independent.
- **Automàtic**: en pujar o baixar de plat, el sistema també modifica el pinyó per suavitzar el canvi.
- El canvi de pinyó és igual en ambdós modes.

## Entrades
- `Pup`: pujar plat  
- `Pdw`: baixar plat  
- `Cup`: pujar pinyó  
- `Cdw`: baixar pinyó  
- `Mode`: selecció Manual / Automàtic  

## Sortides
- Display de 7 segments per indicar el **plat** (1–2)
- Display de 7 segments per indicar el **pinyó** (1–4)
- `PLAT_LIMIT`: LED d’avís per canvi de plat invàlid
- `PINYO_LIMIT`: LED d’avís per canvi de pinyó invàlid

## Restriccions
- Ús del **menor nombre d’estats i bits possibles**
- Exclusivament **flip-flops JK**
- Rellotge amb període d’**1 segon**
- No es permeten entrades simultànies (ús de polsadors)
