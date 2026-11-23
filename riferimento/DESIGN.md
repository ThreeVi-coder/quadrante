# Il Quadrante — regole visive

Questo file è la legge estetica del progetto. Vale più della prosa nei prompt.
Ogni valore qui dentro è un numero, non un aggettivo. Se una cosa non è scritta qui,
guarda `riferimento/index.html`: è il prototipo approvato, è lì che stanno le risposte.

## La legge

**L'aspetto è retrò, la funzionalità no.**
Materiali e ornamenti da collage dark academia; meccanica, reattività e tempi da
interfaccia moderna. Mai vecchio, mai lento, mai triste, mai piatto.

## Colori

Sei, ognuno con un mestiere. Non se ne aggiungono altri senza motivo.

| token | valore | mestiere |
|---|---|---|
| `--nero` | `#0D0D0D` | la pagina d'ingresso, e dopo solo inchiostro |
| `--carta` | `#EFE5D2` | il fondo del sito |
| `--camello` | `#D6A75F` | superfici e campiture (il quadrante) |
| `--oro` | `#C28D39` | **solo linea**, mai riempimento: filetti, contorni, righe |
| `--bordeaux` | `#710912` | accento raro: lo stato attivo, la cosa che conta ora |
| `--espresso` | `#362822` | il testo (mai nero puro su carta calda) |

Camello su hover schiarisce a `#EFCB91`. Il grigio azzurrato è vietato: è triste.

Ogni sezione porta una variazione di tinta propria, usata con parsimonia
(un segmento di riga, un bordo), mai come fondo pieno:
Personaggi `#710912` · Bestiario `#362822` · Mappe `#1D2B1E` ·
Avventure `#452F29` · Musica `#2A2230` · Negozio `#0D0D0D`

## Tipografia

- Display e corpo: **Cormorant Garamond** (300/400/600), fallback Georgia.
- Interfaccia e etichette: sans di sistema, **maiuscoletto**, `letter-spacing: .3em`,
  dimensioni da `.56rem` a `.68rem`.
- Titoli di sezione: `clamp(1.9rem, 4vw, 3.1rem)`, peso 300, `letter-spacing: .1em`.
- Un titolo molto spaziato va compensato con `text-indent` pari allo spacing,
  altrimenti risulta spostato a destra.

## Movimento

**Asimmetria obbligatoria.** La salita è rapida, il ritorno è lento.

- hover in: **160–190 ms**, `cubic-bezier(.2, 1.5, .45, 1)` — con rimbalzo, meccanico
- ritorno a riposo: **420–480 ms**, `cubic-bezier(.22, .9, .26, 1)`
- entrata/uscita di una scena: **500–900 ms**
- si animano solo `transform`, `opacity`, `filter`, `box-shadow`. Mai `width`,
  `height`, `top`, `left`, `margin`.
- `@media (hover: hover) and (pointer: fine)` attorno a ogni effetto hover.
- `prefers-reduced-motion: reduce` sempre rispettato.
- Target: 60fps. Se un effetto non ci sta, si taglia l'effetto, non il frame rate.

**Niente blur sugli elementi non selezionati**, tranne nel Bestiario, dove è voluto.
Altrove l'isolamento si fa solo con il rilievo: quello sotto il cursore sale,
gli altri restano come sono.

## Dipendenze

Consentite solo queste, da CDN, con versione bloccata. Nessun'altra senza autorizzazione.

- **GSAP 3.13.0** + ScrollTrigger, SplitText, DrawSVG, MorphSVG (gratis, uso commerciale)
- **Lenis 1.3.11** per lo scorrimento morbido

Nessun framework, nessun bundler, nessun build step. Il sito resta HTML + CSS + JS
serviti da GitHub Pages, e i contenuti restano in file leggibili a mano.

## Le scene

### Ingresso
Pagina nera. Tre archi **alti e stretti**, quasi attaccati fra loro: larghi 150 su
un impianto di 1200, apici a 170 (laterali) e 138 (centrale), base a 662.
Linee bianche `#F6EEDF` spessore 1.2 che si incidono una dopo l'altra, 1s ciascuna,
sfalsate di 100ms. Poi il nero dentro ogni arco si stacca e si dissolve
(translateY -8%, scale 1.025, 950ms), scoprendo l'immagine del mondo.
Titolo e sottotitolo **in alto a sinistra**, mai sopra gli archi.
Emblema piccolo in alto al centro, etichetta tecnica in alto a destra,
filo di cornice a 22px dai bordi. In basso una freccia chiara sottile fra due tratti.
Clic in qualsiasi punto = salta all'ultimo fotogramma.
La sfumatura verso la carta in fondo alla pagina è alta **4,5vh**, non di più.

### Discesa
Rotella o clic sulla freccia. Non è uno scatto: è una **transizione continua**
che accompagna giù fino al quadrante. Ingresso e quadrante vivono sulla stessa pagina.

### Quadrante
**Fisso.** Sei settori, ognuno sempre al suo posto, raggio interno 170, esterno 300,
distacco 1,5° per lato. Anello esterno di tacche in oro che ruota lentissimo (260s).
Hover: il settore sotto il cursore esce di 16px lungo il proprio raggio con rimbalzo,
gli altri rientrano di 7px e si spengono leggermente. Scatto secco, non morbido.
Al centro compare **l'immagine** della sezione, non una descrizione: si guarda, non si legge.
Clic = si entra. Nessun pulsante "Entra". Nessun lampo di colore all'uscita.

### Entrata in una sezione
Non è un taglio netto. Il quadrante si dissolve, il titolo della sezione si stacca,
sale in alto a sinistra e si incastra. Sotto, una riga d'oro che si tira da sinistra
a destra, con i primi 120px nella tinta della sezione. Home, impostazioni e profilo
stanno **in alto a destra, sopra la riga**. Il torna-indietro sotto la riga, a sinistra.

### Le sei sezioni, una forma ciascuna
Non devono somigliarsi. È l'errore da non rifare.

- **Personaggi** — galleria di ritratti in cornici ad arco tondo, come quadri appesi.
  Nome e ruolo sotto. Clic apre la pagina del personaggio, impaginata dal suo autore.
- **Bestiario** — elenco verticale, ogni creatura racchiusa fra due graffe che si
  allargano con il blocco. Immagine e testo alternati destra/sinistra.
  Hover: rilievo, e qui sì, le altre sfocano. Clic apre una pagina su carta invecchiata
  con cornice incisa, illustrazione grande, nome e descrizione.
- **Mappe** — composizione centrale: raggiera, telaio, cerchio sovrapposto, nome al centro.
  **La rotella non scorre la pagina: cambia terra.** Una tacca, una mappa.
- **Avventure** — scaffale di dorsi di libri con i titoli in verticale.
  Clic: il volume si estrae davvero e si apre sul suo manifesto, da locandina di film.
- **Musica** — da ripensare. Per ora un elenco di temi sobrio.
- **Negozio** — due o tre vetrine ad **arco gotico a sesto acuto**, disposte **a sbalzo**
  (alta, bassa, alta), filo d'oro doppio, targa sotto con titolo e prezzo.

## Cose che non si fanno

- Titoli sopra le immagini se diventano illeggibili.
- Sfumature di passaggio alte più di 5vh.
- Blur fuori dal Bestiario.
- Effetti senza una funzione (un colore che lampeggia per niente).
- Sei sezioni con lo stesso impianto.
- Grigi freddi.
- Riempimenti in oro.
