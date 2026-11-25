## Sessione 1

**Cosa ho chiesto:**

Ho fornito i file HTML, CSS e JSON iniziali del sito e ho chiesto supporto passo dopo passo per completare le consegne:
  1. completamento di *dati/sedi.json* (3 sedi) e *dati/eventi.json* (6 eventi collegati tramite sede_id);
  2. generazione dinamica delle schede in *programma.html* tramite *fetch*;
  3. integrazione in *info.html* della sezione «Meteo a Torino adesso» tramite l'API di Open-Meteo;
  5. correzione dell'allineamento e dei margini laterali in *programma.html*.

**Cosa ho usato, modificato o scartato:**

*Usato:* le strutture JSON per `sedi.json` ed `eventi.json`, la scheda dati e il diagramma Mermaid per `SCHEMA.md`, e gli script `fetch` per `programma.html` e `info.html`.

*Modificato/Scartato:* invece di sovrascrivere l'intero codice di `programma.html` proposto inizialmente, ho chiesto di isolare solo le righe da sostituire per facilitare un eventuale *undo last commit*.

**Come ho verificato:**

Ho controllato l'assenza di errori di sintassi nell'editor di VS Code e ho verificato nel browser la resa grafica, la responsività e la correttezza dei dati caricati.

**Problemi riscontrati e soluzioni:**

*Errore di sintassi JSON (`End of file expected`):* avevo incollato per errore il contenuto di entrambi i JSON dentro `eventi.json` e creato `SCHEMA` senza estensione `.md`. Ho risolto separando i due array nei rispettivi file e rinominando il file in `SCHEMA.md`.

*Margini laterali mancanti in `programma.html`:* sostituendo il codice avevo lasciato `</main>` chiuso prima della griglia degli eventi, facendola uscire dal `.container`. Ho spostato la chiusura `</main>` dopo `<section class="content-section">` ripristinando i margini coerenti con `index.html` e `info.html`.