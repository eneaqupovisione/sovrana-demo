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
| `scene-collo/` | 20 quadri, 01:10 → 01:11, 1600 px | anello dietro i tasti di «Mi Piace» |
| `scene-viso/` | 36 quadri, 01:11 → 01:12.9, 1600 px | anello dietro i tasti di «24/7» |
| `scene-cavallo/` | 24 quadri, 00:53 → 00:54.9, 1600 px | il cavallo di «Limited»: invertito e in `multiply`, diventa inchiostro sull'acido |
| `img/` | 9 fermi immagine, 1500 px | testate di pagina, schede merch, tasti dei social |

`frames/` si carica sul loader ed è l'unica pilotata dallo scroll. Le altre tre
sono anelli: si scaricano e partono da sole quando la sezione entra in campo,
vanno avanti e tornano indietro (così il gesto non ha stacchi) e si fermano
appena escono. Con `prefers-reduced-motion` restano su un fermo immagine.

Il piano sequenza del collo sono **due gesti diversi** con uno stacco netto al
frame 20 del sorgente: tenerli in un'unica sequenza era un errore, ora sono due
anelli separati dietro due canzoni diverse.

## Effetti

- **scioglimento acido** in hover su titoli e immagini (`feTurbulence` +
  `feDisplacementMap`, un solo filtro pilotato dal puntatore)
- **scarto RGB** sui titoli (`.gx`, ciano + magenta in `screen`)
- **testo che si ricompone** dal rumore quando entra in campo (`data-scr`)
- **nastri** inclinati a tutta larghezza: separano le sezioni. Le insegne
  stanno in `SAY` e ogni nastro sceglie il gruppo con `data-say`; senza
  attributo prende `Enny P` / `Faccio what I want 24/7`
- **cromo liquido** sul marchio, gradiente animato ritagliato sul testo
- **Limited** (`#flip`, prima della lista): per circa un viewport di scroll
  il sito cambia pelle — fondo acido, testo nero, testata invertita. Il
  pannello è `fixed`, non `sticky`: una sticky entra dal basso e si porta
  dietro un viewport di vuoto prima di scattare. La sezione `#flip` è solo un
  distanziatore di 50vh che misura quanto dura il ribaltone. Due lampi a tutto
  schermo coprono lo scambio; senza, si vedrebbe solo un salto di colore. Le
  bande dello strappo stanno sotto i 3 Hz e con `prefers-reduced-motion` il
  lampo non parte affatto
- cursore acido in `difference`, bottoni magnetici, parallasse, grana e righe

Tutto si disattiva con `prefers-reduced-motion`.

## Dati

In cima allo `<script>`: `DATES`, `MERCH`, `RELEASES`, `TICKER`. Sono gli unici
punti da toccare quando arrivano i dati veri. Date, prezzi e link dello shop
sono segnaposto.

## Limited

Ci arriva solo chi ha continuato a scorrere oltre il merch. Dentro c'è quello
che non sta nel menu, in quest'ordine:

1. **un pezzo che sembra trovato** — la stampa numerata del cavallo, 30 copie;
   l'animazione accanto *è* la stampa
2. **una cosa da fare subito** — la lista dei drop, campo e bottone lì, senza
   rimandare a un'altra pagina
3. **materiale grezzo e contatti** — sfondi, testo, press kit, booking: il fan
   e chi lavora nel settore trovano entrambi qualcosa

## Una regola sul testo

Il sito non si riempie di citazioni. Le uniche frasi che compaiono sono le
insegne dei nastri, sono quattro in tutto e si ripetono. Tutto il resto è etichetta di
servizio: «Fuori ora», «Date», «Biglietti», «Booking». Ogni immagine deve avere
un compito — testata, scheda prodotto, tasto — nessuna sta lì per riempire.
