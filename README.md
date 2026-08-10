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
| `scene-occhi/` | 15 quadri, 00:33 → 00:33.7, 1600 px | anello dietro i tasti di «24/7» |
| `scene-soldi/` | 24 quadri, 01:35.9 → 01:37.1, 1600 px | anello dietro i tasti di «Money Maker» |
| `scene-addio/` | 15 quadri, 02:13.4 → 02:14.1, 1600 px | il bacio: l'ultima cosa che si vede, dietro la lista |
| `sc-musica/` | 00:09.4 → 00:10.6 | testata Musica: denti e lingua, la faccia della voce |
| `sc-eventi/` | 00:57.7 → 00:58.9 | testata Eventi: artigli sul viso, guarda in camera |
| `sc-merch/` | 00:38.5 → 00:39.5 | testata Merch: labbra e artigli d'argento, roba che si indossa |
| `sc-social/` | 01:27.0 → 01:27.9 | testata Social: occhiali e mosso, la faccia moltiplicata |
| `sc-contatti/` | 01:57.0 → 01:58.2 | testata Contatti: primo piano verso l'obiettivo |
| `sc-chi/` | 01:00.8 → 01:01.7 | testata Chi è: lei sul cavallo cromato |
| `sc-ritratto/` | 02:31.4 → 02:32.3 | il ritratto in Chi è: figura intera |
| `sc-menu/` | 00:03.2 → 00:04.4 | dietro il menu a tutto schermo |
| `scene-cavallo/` | 24 quadri, 00:53 → 00:54.9, 1600 px | il cavallo di «Limited» (lei sopra, 00:51.7 → 00:52.9): invertito e in `multiply`, diventa inchiostro sull'acido |
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
- **raggi X** (`data-xray`): un dettaglio si apre in una lastra al passaggio del
  puntatore — etichetta, scheda del singolo, specifiche della stampa,
  spedizioni. Il click porta comunque alla pagina intera: la lastra è
  un'anteprima, non un vicolo cieco. Al tocco non compare e resta il link.
  Aggiungerne uno = una voce in `XRAY` e un `data-xray` sull'ancora
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

## Il finale del palco

Quando la stretta si porta via il nome, al suo posto non compare una frase:
compare l'uscita. Occhiello, titolo del singolo, «Ascolta ora» verso la
piattaforma e «Tutte le piattaforme» verso la pagina Musica. È l'unico punto
del palco in cui si può cliccare, e resta in campo per l'ultimo quarto della
scena — `pointer-events` si accende solo quando è abbastanza visibile da
essere colpito apposta.

## Telefono

Non e' il sito rimpicciolito, e' un secondo montaggio:

- **l'inquadratura si calcola.** Ogni sequenza dichiara dov'e' il soggetto nel
  girato (`fx`, `fy`) e dove lo si vuole nel riquadro (`px`). Su schermo largo
  c'e' margine per stringere e spostare, perche' il testo sta di lato; su
  schermo stretto il ritaglio mangia gia' i fianchi, quindi il soggetto torna
  al centro e lo zoom sparisce. Nessun valore scritto due volte.
- **il cavallo di «Limited» (lei sopra, 00:51.7 → 00:52.9)** su schermo stretto passa a `contain` e scende in
  fondo, intero. Si puo' fare perche' il nero fuori dall'immagine, dopo
  `invert`, diventa bianco e il `multiply` lo restituisce acido: invisibile.
  Il testo sale in alto e il velo si apre verso il basso.
- **quello che su desktop fa il passaggio del puntatore, sul telefono lo fa lo
  scorrimento**: di ogni gruppo si accende un elemento solo, quello piu' vicino
  al centro dello schermo. Le stesse regole CSS, con `.hot` accanto a `:hover`.
  Le lastre a raggi X invece **non** si aprono da sole: si aprivano passando
  per il centro e finivano addosso a chi scorreva. Al tocco le apre un tocco,
  diventano toccabili loro stesse (dentro c'è il link alla pagina intera) e
  basta muoversi per chiuderle.
- **i tasti d'ascolto** si stringono a 70% (max 300 px): a tutta larghezza
  coprivano l'inquadratura
- **il merch** passa a due colonne: un oggetto per riga erano dieci schermate.

## Le testate

Le sei pagine interne avevano una foto ferma dietro il titolo. Ora hanno un
anello, con lo stesso trattamento duotone di prima. La scelta segue il formato:
la testata è una fascia bassa e larga, quindi ci vanno i **primi piani** — un
campo lungo lì dentro viene tagliato alla vita. I campi lunghi stanno invece
nei riquadri alti: il ritratto di «Chi è» e il menu a tutto schermo.

Il menu è `position:fixed` a tutto schermo: senza `data-loop-when="on"` il suo
anello girerebbe anche da chiuso.

## Una regola sul testo

Il sito non si riempie di citazioni. Le uniche frasi che compaiono sono le
insegne dei nastri, sono quattro in tutto e si ripetono. Tutto il resto è etichetta di
servizio: «Fuori ora», «Date», «Biglietti», «Booking». Ogni immagine deve avere
un compito — testata, scheda prodotto, tasto — nessuna sta lì per riempire.
