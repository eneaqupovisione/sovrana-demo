# ENNY P — sito

Sito in pagina unica (nessuna dipendenza, nessun build). Tutto sta in
`index.html`: stili, template delle pagine, router a `#/`, animazioni.

Online: https://eneaqupovisione.github.io/sovrana-demo/

## Lingua visiva

Il girato di «24/7» dà il nero, il petrolio e l'argento. Al sito aggiungiamo
due colori che nel video non esistono e che non si toccano mai nello stesso
punto: **l'oro** (veste) e il **verde acido** (attacca).

Tre caratteri, tre registri:

- **Archivo** in larghezza estesa — i titoli, il peso del nome
- **Bodoni Moda** — il registro editoriale, le citazioni
- **Space Mono** — l'HUD della macchina, le etichette

## Immagini e sequenze

Tutto estratto dal video ufficiale «24/7».

| cartella | contenuto | uso |
|---|---|---|
| `frames/` | 34 quadri, 00:00.8 → 00:02.2, 2560 px | il palco: la mano che stringe e si porta via il marchio |
| `scene-collo/` | 35 quadri, 01:10 → 01:12.8, 1920 px | sfondo in movimento dietro i tasti d'ascolto |
| `scene-cavallo/` | 24 quadri, 00:53 → 00:54.9, 1600 px | anello in loop: il cavallo cromato |
| `img/` | 9 fermi immagine, 1500 px | testate di pagina, schede merch, tasti dei social |

`frames/` si carica sul loader; le altre due sequenze solo quando la sezione
sta per entrare in campo. Il loop del cavallo gira solo mentre è visibile.

## Effetti

- **scioglimento acido** in hover su titoli e immagini (`feTurbulence` +
  `feDisplacementMap`, un solo filtro pilotato dal puntatore)
- **scarto RGB** sui titoli (`.gx`, ciano + magenta in `screen`)
- **testo che si ricompone** dal rumore quando entra in campo (`data-scr`)
- **nastri** inclinati a tutta larghezza: separano le sezioni e portano
  sempre le stesse due insegne — `Enny P` e `Faccio what I want 24/7`
- **cromo liquido** sul marchio, gradiente animato ritagliato sul testo
- cursore acido in `difference`, bottoni magnetici, parallasse, grana e righe

Tutto si disattiva con `prefers-reduced-motion`.

## Dati

In cima allo `<script>`: `DATES`, `MERCH`, `RELEASES`, `TICKER`. Sono gli unici
punti da toccare quando arrivano i dati veri. Date, prezzi e link dello shop
sono segnaposto.

## Una regola sul testo

Il sito non si riempie di citazioni. Le uniche due frasi che compaiono sono le
insegne dei nastri, e sono sempre quelle. Tutto il resto è etichetta di
servizio: «Fuori ora», «Date», «Biglietti», «Booking». Ogni immagine deve avere
un compito — testata, scheda prodotto, tasto — nessuna sta lì per riempire.
