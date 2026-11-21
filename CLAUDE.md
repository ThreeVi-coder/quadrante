# Il Quadrante — regole di lavoro

Sito statico, vanilla HTML/CSS/JavaScript, nessuno step di build.
Ospitato su GitHub Pages, repository pubblico. I contenuti stanno in file
dati leggibili e scrivibili a mano, senza toccare codice.

Chi mantiene questo progetto lo fa da solo, con tempo limitato e budget
zero. Il codice in più non è neutro: è roba che un domani va letta,
capita e corretta da una persona sola. Scrivere meno è parte del lavoro,
non una scorciatoia.

## Prima di scrivere codice

- Dammi il piano prima: quali file tocchi, cosa cambi in ognuno, quante
  righe circa in totale.
- Se il piano supera le 60 righe per una cosa che sembrava piccola,
  fermati e dimmelo. Spesso significa che stai risolvendo il problema
  sbagliato.
- Se la cosa si può fare in CSS, non si fa in JavaScript.
- Se esiste già qualcosa che fa l'80% del lavoro in questo progetto,
  si estende quella, non se ne scrive una nuova accanto.

## Sicurezza

Il sito non ha server, database, login né campi in cui un visitatore
possa scrivere. La superficie di attacco è quindi piccola, e queste
regole servono a tenerla tale.

- **Il testo dei file dati va in pagina con `textContent`, non con
  `innerHTML`.** Se davvero serve del testo formattato, si costruiscono
  gli elementi uno per uno con i tag ammessi; non si passa mai contenuto
  grezzo a `innerHTML`.
- **Niente `eval`, niente `new Function`**, e niente HTML costruito
  incollando dati dentro una stringa.
- **Niente che arrivi dall'indirizzo della pagina finisce in pagina così
  com'è.** Se l'ancora o un parametro scelgono quale scheda mostrare,
  quel valore va confrontato con l'elenco delle schede esistenti e
  scartato se non corrisponde.
- **Gli indirizzi presi dai file dati si accettano solo se iniziano per
  `http://` o `https://`.** Un `javascript:` dentro un collegamento o
  un'immagine è codice che parte.
- **Niente chiavi, token o password nel repository.** È pubblico:
  qualunque cosa ci finisce è pubblica per sempre, anche se poi la
  cancelli.
- **Niente script esterni senza chiedermelo.** Se un giorno ne serve
  uno, si scarica il file nel progetto oppure si blocca a una versione
  precisa con l'hash di integrità.
- **Fermati e chiedi** nel momento in cui il progetto ha bisogno di un
  accesso utente, di un modulo che spedisca dati, di un pagamento o di
  un database. Lì le regole sono diverse e non si improvvisano.
- Prima di pubblicare qualcosa di nuovo, gira `/security-review`.

## Economia del codice

- **Niente astrazioni prima della terza ripetizione.** Due volte si
  copia. Tre volte si estrae.
- **Niente gestione di errori per casi che non possono capitare.** I dati
  arrivano da file scritti a mano da me: non vanno validati come se
  venissero da un modulo pubblico. Questo non vale per i tre controlli
  di sicurezza qui sopra, che restano sempre.
- **Niente opzioni di configurazione con un solo chiamante.** Si scrive
  il valore.
- **Niente wrapper intorno a una funzione del browser** che già fa quello
  che serve.
- **Niente retrocompatibilità.** Non c'è nessuno a cui rompere qualcosa.
- **Niente codice per funzionalità future.** Si costruisce quello che
  serve oggi; il futuro lo aggiungiamo quando arriva.
- **Niente commenti che ripetono il codice.** Si commenta solo dove il
  perché non si vede leggendo.
- **Niente dipendenze nuove senza chiedermelo prima**, nemmeno piccole.
  Il sito deve funzionare aperto da un file, senza npm.
- **Niente file nuovi senza chiedermelo prima.** Se una cosa appartiene a
  un file che esiste, va lì dentro.

## Come si modifica

- Si cambia la riga, non si rigenera il file. Se un file esiste, le
  modifiche sono puntuali e il resto resta identico.
- Un compito per volta. Non si sistemano cose non richieste "visto che
  c'ero": se ne noti una, scrivila in fondo alla risposta e lasciala
  stare.
- Mai cancellare o riscrivere contenuti dentro i file dati. Quelli sono
  testo mio.

## Cosa significa finito

Finito è: la cosa chiesta funziona nel browser, il resto del sito non si
è rotto, e non c'è una riga che si possa togliere senza perdere niente.
Non è: pronto per ogni caso futuro, coperto da ogni controllo possibile,
generalizzato.

## Dopo ogni modifica

Due righe, non di più: cosa hai cambiato, e cosa devo controllare io con
gli occhi nel browser.
