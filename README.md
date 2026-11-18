# Projectes Digital

Projectes finals de l'assignatura **Sistemes Digitals**, fets amb [Digital](https://github.com/hneemann/Digital).

Cada curs té la seva carpeta amb un README propi que explica cada projecte: l'enunciat resumit, les entrades i sortides, i com està organitzat el circuit.

## Cursos

| Curs | Sistemes Combinacionals | Sistemes Seqüencials |
|------|-------------------------|----------------------|
| [2025-26](2025-26/README.md) | Caixa forta amb doble autenticació | Canvi de marxes d'una bicicleta |
| [2026-27](2026-27/README.md) | ALU de 3 bits (C2 / SM) | *Pendent* |

## Estructura

```
Projectes-Digital/
├── 2025-26/
│   ├── Projecte - Sistemes Combinacionals/
│   └── Projecte - Sistemes Sequencials/
└── 2026-27/
    ├── Projecte - Sistemes Combinacionals/
    └── Projecte - Sistemes Sequencials/   (pendent)
```

A cada projecte hi ha l'enunciat en PDF i tots els fitxers `.dig`. El circuit de nivell superior sempre es diu **`solucio.dig`**.

## Com obrir-los

1. Descarrega [Digital](https://github.com/hneemann/Digital/releases) (cal Java).
2. Obre el fitxer `solucio.dig` del projecte que vulguis. Els subcircuits es carreguen automàticament des de la mateixa carpeta.
3. Per passar els tests, ves a **Simulació → Executar tests** (o `F8`).

Els tests també es poden llançar des de la terminal:

```bash
java -cp Digital.jar CLI test -circ "ruta/al/fitxer.dig"
```

## Normes comunes de les pràctiques

- Implementació **només amb portes lògiques** i subcircuits propis. No es poden fer servir els mòduls de la llibreria de Digital ni generar circuits a partir de taules de veritat.
- Disseny **modular**, amb **tests de Digital** per a cada subcircuit i per al circuit complet.
- Els noms de les entrades i sortides han de coincidir **exactament** amb els de l'enunciat.

## Llicència

[MIT](LICENSE)
