# English changelog — RCU Linux

## v3.3.0 — 2026-10-16

- Add "Include subfolders" (GTK, saved in preferences) and `--recursive`/`-r`: process a folder and everything below it, off by default.
- Each included folder is its own collection with its own series, journal and undo; previews show names relative to the chosen folder.

## v3.2.1 — 2026-10-11

- Recognize comma-delimited issue numbers and preserve the correct title when a rule removes the Bonelli metadata tail.
- List the GTK app as Rename Comics Converter in the Graphics menu; add current main-window and rules-editor screenshots.

## v3.2.0 — 2026-10-10

- Add protected CSV/JSON exports, cooperative cancellation, progress, history selection and a desktop history browser.
- Preserve selections across preview filters, diagnose filename length limits and harden undo journals.

## v3.1.0 — 2026-10-10

- Add a native GTK desktop with preview, file selection, guided rules and five interface languages.
- Preserve original extension spelling and add SHA-256 verification for undo.

## v2.8.1 — 2026-10-06

- Remove the full metadata tail beginning at a recognized publisher/date or colorization/version note, including ISO publisher dates.
- Allow GUI selection of one duplicate version per proposed filename; preserve other versions.

## v2.8 — 2026-10-06

- Added preview and confirmation, per-file GUI selection, undo history and collision-safe renaming.
- Fixed cancellation, mixed-series detection and corruption on repeated runs.
- Added explicit CLI/GUI modes, dry run, literal suffix tags and optional title case.
- Preserve title years, genuine parentheses and legitimate words.
- Added reproducible Debian packaging with Bash, Python 3.9+ and optional Zenity.



## v2.7 - 2025-12-05
- Added `.deb` package with icon and `.desktop` file for menu integration on major Linux distributions.
- Enhanced automatic series header detection in mixed folders (multiple series, multiple formats).
- Fixed minor bugs in issue number parsing and space normalization.

## v2.6 - 2025-11-15
- Extended title recognition logic for complex filenames containing tags like “c2c”, “scan by”, “a colori”.
- Optimized on-screen messages (colors and summary) for clearer end-of-process output.
- Improved handling of cases where an issue number exists but no usable title is present.

## v2.5 - 2025-10-20
- Introduced three-digit issue number formatting (`001`, `033`, `120`) for correct ordering in file managers.
- Improved `titlecase` function with a list of Italian articles and prepositions kept in lowercase.
- Automatic cleanup of parentheses and non-essential content (scanner notes, group tags, duplicate titles).

## v2.4 - 2025-09-30
- Full support for PDF, CBR, CBZ, and EPUB files in the same folder.
- Added automatic detection of series header (e.g. “Zagor”, “Dylan Dog”, “Spider Man”).
- If a file already has the “correct” name, the script now skips it without renaming.

## v2.3 - 2025-09-10
- Improved regular expressions to recognize patterns such as `N.33`, `033 - Title`, `033_Title`, `Title 033`.
- Added interactive options (Zenity when available) for folder selection and header confirmation.

## v2.2 - 2025-08-25
- Introduced non-interactive terminal mode by specifying the folder as a parameter.
- Better error handling when the folder does not exist or contains no supported files.

## v2.1 - 2025-08-10
- Code cleanup, split into separate functions for:
  - issue number extraction
  - title extraction
  - title cleaning
- Added colored log messages for successful renames, skipped files, and errors.

## v2.0 - 2025-08-01
- Complete rewrite into the “universal” RCU mode to handle multiple series and formats.
- First version with multi-format support and automatic issue number detection.

## v1.0 - 2025-07-10
- Initial version of the renaming script for a single series in CBR/CBZ format.
- Basic renaming: `Series Number - Title` with minimal space and capitalization normalization.








# Registro modifiche — RCU Linux

## v3.3.0 — 2026-10-16

- Aggiunta «Includi sottocartelle» (GTK, salvata nelle preferenze) e `--recursive`/`-r`: elabora una cartella e tutto ciò che contiene; spenta di predefinito.
- Ogni cartella inclusa è una raccolta a sé, con serie, registro e annullamento propri; le anteprime mostrano i nomi relativi alla cartella scelta.

## v3.2.1 — 2026-10-11

- Riconosciuti i numeri seguiti da virgola; le regole che eliminano la coda Bonelli conservano il titolo corretto.
- La voce GTK appare come Rename Comics Converter in Graphics; aggiunte schermate aggiornate della finestra e dell'editor.

## v3.2.0 — 2026-10-10

- Aggiunte esportazioni CSV/JSON protette, interruzione cooperativa, avanzamento, selezione dei registri e cronologia grafica.
- Conservata la selezione con i filtri; diagnosticati i limiti dei nomi e rafforzata la convalida dei registri.

## v3.1.0 — 2026-10-10

- Aggiunta interfaccia GTK nativa con anteprima, selezione dei file, regole guidate e cinque lingue.
- Conservata l'estensione originale e aggiunta verifica SHA-256 per l'annullamento.

## v2.8.1 — 2026-10-06

- Rimozione della coda completa dei metadati a partire da editore/data o note di colorazione/versione riconosciuti, incluse date ISO.
- Selezione GUI di una sola versione duplicata per nome proposto, conservando le altre.

## v2.8 — 2026-10-06

- Anteprima e conferma, selezione GUI dei file, registri di annullamento e rinomine senza sovrascrittura.
- Corretti annullamento, cartelle con serie miste e corruzione dei nomi nelle esecuzioni ripetute.
- Modalità CLI/GUI esplicite, dry run, tag letterali e capitalizzazione facoltativa.
- Conservati anni, parentesi dei titoli e parole legittime.
- Pacchetto Debian riproducibile con Bash, Python 3.9+ e Zenity facoltativo.



## v2.7 - 2025-12-05
- Aggiunto pacchetto `.deb` con icona e file `.desktop` per integrazione nel menu delle principali distro.
- Migliorata rilevazione automatica dell’header di serie in cartelle miste (più serie, più formati).
- Correzione di piccoli bug nel parsing dei numeri di albo e nella normalizzazione degli spazi.

## v2.6 - 2025-11-15
- Estesa la logica di riconoscimento titoli per nomi file complessi con tag come “c2c”, “scan by”, “a colori”.
- Ottimizzati i messaggi a schermo (colori e riepilogo) per una lettura più chiara a fine processo.
- Aggiunta gestione migliorata dei casi in cui il numero è presente ma il titolo è assente.

## v2.5 - 2025-10-20
- Introdotta la formattazione del numero di albo a tre cifre (`001`, `033`, `120`) per ordinamento corretto in file manager.
- Migliorata la funzione di `titlecase` con lista di articoli/preposizioni italiani da mantenere in minuscolo.
- Pulizia automatica di parentesi e contenuto non utile (note scanner, gruppi, ripetizioni del titolo).

## v2.4 - 2025-09-30
- Supporto completo per file PDF, CBR, CBZ ed EPUB nella stessa cartella.
- Aggiunta rilevazione automatica dell’header di serie (es. “Zagor”, “Dylan Dog”, “Spider Man”).
- Gestione dei casi in cui il file ha già il nome “corretto”: lo script li salta senza rinominare.

## v2.3 - 2025-09-10
- Migliorate espressioni regolari per riconoscere pattern come `N.33`, `033 - Titolo`, `033_Titolo`, `Titolo 033`.
- Aggiunte opzioni interattive (Zenity se presente) per scelta cartella e conferma header.

## v2.2 - 2025-08-25
- Introdotta modalità non interattiva da terminale specificando la cartella come parametro.
- Migliorata gestione degli errori quando la cartella non esiste o non contiene file supportati.

## v2.1 - 2025-08-10
- Pulizia del codice, funzioni separate per:
  - estrazione numero
  - estrazione titolo
  - pulizia del titolo
- Aggiunti messaggi di log colorati per rinomini riusciti, saltati ed errori.

## v2.0 - 2025-08-01
- Riscrittura completa dello script in modalità “universale” (RCU) per gestire più serie e formati.
- Prima versione con supporto multi-formato e rilevamento automatico del numero di albo.

## v1.0 - 2025-07-10
- Prima versione dello script di rinomina per una singola serie in formato CBR/CBZ.
- Rinomina base: `Serie Numero - Titolo` con normalizzazione minima di spazi e maiuscole.
