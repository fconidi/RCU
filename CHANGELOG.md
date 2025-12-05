# ENGLISH Changelog - RCU (Rename Comics Universal)

## v2.7 - 2025-12-05
- Added `.deb` package with icon and `.desktop` file for menu integration on major Linux distributions.
- Improved Windows support via `.bat` wrapper and “click & run” `.exe` option.
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





XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX



# ITALIAN Changelog - RCU (Rename Comics Universal)

## v2.7 - 2025-12-05
- Aggiunto pacchetto `.deb` con icona e file `.desktop` per integrazione nel menu delle principali distro.
- Migliorata compatibilità con Windows tramite wrapper `.bat` e possibilità di creazione `.exe` “click & run”.
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

