# RCU
Rename Comics Converter is an app for Linux and Windows designed to automatically rename digital comic files (PDF, CBR, CBZ, EPUB) by detecting the series name, issue number, and optional title.

ENGLISH VERSION

Overview

Rename Comics Universal (RCU) is a Bash script designed to automatically rename digital comic files (PDF, CBR, CBZ, EPUB) by detecting the series name, issue number, and optional title, producing clean and consistent filenames like “Comics_Name 033 - Clean Title.cbz”.
It is aimed at readers and collectors who want to tidy up messy file names full of tags such as “scan”, “by”, group names, or random notes.

Main technical features
    • Format detection: scans a chosen directory and processes only PDF, CBR, CBZ, and EPUB files, ignoring subfolders.
    • Smart extraction: uses regular expressions to isolate issue numbers (for example “033” or “N.33”) and titles, removing tokens like “ScanBy”, “by”, “edit” with common Unix tools.
    • Automatic cleanup: applies functions to normalize spacing, remove brackets and special characters, and convert titles to proper title case, while padding issue numbers to three digits (e.g. 033).
    • Header detection: analyzes filenames to find the most frequent series header (such as “Zagor” or “Dylan Dog”), which can be confirmed or changed via a Zenity GUI dialog.
    • Colored output: shows colored terminal messages for successes and skips and prints a final summary with counters.

How it works

The script asks for a target folder either via command-line argument or through a small Zenity window, then scans all supported files in that directory.
For each file it tries to determine the series name, locate the issue number, and detect any following title that can be cleaned up.
It then builds a standardized name in one of these forms:

    • “Series 001 - Clean title.ext” when a title can be extracted
    • “Series 001.ext” when no usable title is found
    
If a file is already correctly named or a file with the target name already exists, the script skips it to avoid duplicates or overwrites.

What it fixes automatically

    • Removes useless tags like “scan by…”, “edited”, “by scan”, release group labels, or redundant technical notes.
    • Normalizes capitalization so that important words start with an uppercase letter, while articles and prepositions stay lowercase where appropriate.
    • Strips brackets and their internal content when they only contain technical info or repeated titles.
    • Keeps numbering consistent with three digits, which is especially helpful for long-running series.
    
Usage

To use the script you make it executable and run it, optionally passing the comics folder path; otherwise the script will ask for it interactively and let you review or edit the detected series header.

Example (Linux terminal):

chmod +x rename_comics_universal.sh
./rename_comics_universal.sh

or using rename-comics-universal_2.7.deb

sudo dpkg -i rename-comics-universal_2.7.deb
rename_comics_universal

Why it is useful for collectors

The script saves a large amount of manual work by renaming hundreds of files in one go, making the library easier to browse in file managers and comic readers.
It is particularly suited to Italian and English comics from real scans, where filenames often contain many superfluous details, and it is lightweight, with no dependencies beyond Bash and optionally Zenity. It is highly configurable.


XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

ITALIANO

Hai una collezione di fumetti digitali in disordine? Rename Comics Universal (RCU) è uno script bash universale che automatizza il rinominamento di file PDF, CBR, CBZ ed EPUB, estraendo intestazioni comuni (come "Zagor" "Spider Man" o "Dylan Dog"), numeri di albo e titoli, per ottenere nomi puliti e standardizzati.

​
Caratteristiche Tecniche Principali

Riconoscimento Formati: Analizza PDF, CBR, CBZ, EPUB in una directory specifica, ignorando sottodirectory.

Estrazione Intelligente: Regex per isolare numeri (es. "033", "N.33") e titoli, rimuovendo token come "ScanBy", "by", "By tizio", "edit" con sed -E e tr.

Pulizia Automatica: Funzioni cleantitle e titlecase per title case, eliminazione di parentesi, spazi multipli e caratteri speciali; padding numerico a 03d (es. "Zagor 033 - Titolo pulito.cbz").

Header Detection: Cerca il nome del fumetto di e seleziona  quello principale o quello più comune, si può modificare tramite Zenity GUI.

    ​
Come Funziona:

Seleziona cartella via CLI o Zenity (targetdir).

detectheader: Scansiona file, estrae potenziali header (pre-numero), sceglie il più frequente.

renamefiles: Per ogni file, extractnumber + extracttitle, applica cleantitle, formatta nuovo nome e rinomina (mv con check duplicati).

Output colorato (ANSI: GREEN per successi, YELLOW per skip), summary finale con contatori.


Vantaggi:

Ideale per collezioni italiane (Zagor, Tex Willer) o USA (Marvel/DC): gestisce varianti underscore/spazi, normalizza zeri iniziali, evita sovrascritture. Robusto con error handling (skip se no numero/header). Personalizzabile per nuovi formati estendendo il loop "for ext in pdf cbr cbz"

​Script leggero (13KB), zero dipendenze oltre bash/zenity (opzionale). Scarica ed ordina la tua libreria in pochi secondi! 

RENAME COMICS UNIVERSAL è uno script pensato per mettere ordine in una cartella di fumetti digitali in modo automatico, partendo dai nomi dei file e trasformandoli in nomi puliti e uniformi come “Zagor 033 - Il ponte sull’inferno.cbz”.
​

​
A cosa serve:

Riorganizza file PDF, CBR, CBZ ed EPUB che hanno nomi caotici, pieni di tag tipo “scan”, “by tizio”, “c2caio” "ecc", riferimenti allo scanner o scritti tutti in maiuscolo o minuscolo.
Rende i nomi leggibili: numero dell’albo sempre con tre cifre, titolo in “Title Case”, niente parentesi inutili o caratteri strani. È ideale per serie lunghe (Zagor, Dylan Dog, Tex, Marvel/DC) dove avere tutti i numeri ordinati è fondamentale per consultare la collezione.

    ​

Come funziona:

Scegli una cartella che contiene i fumetti (da terminale o con una piccola finestra grafica, se hai Zenity installato). Lo script analizza tutti i file supportati nella cartella e cerca di capire:
qual è il “nome serie” più usato (es. “Zagor”, “Dylan Dog”)
dove si trova il numero dell’albo nel nome del file
se dopo il numero è presente un titolo da ripulire.
Per ogni file costruisce un nuovo nome del tipo:

“Serie 001 - Titolo pulito.cbz” se esiste un titolo
“Serie 001.cbz” se non c’è titolo recuperabile.

Cosa sistema automaticamente:

Toglie scritte inutili come “scan by…”, “edited”, “colori”, tag di gruppi, ecc. così nel nome resta solo ciò che serve alla consultazione. Sistema maiuscole/minuscole: articoli e preposizioni rimangono in minuscolo, le parole importanti hanno l’iniziale maiuscola. Elimina parentesi e contenuto dentro le parentesi quando sono solo note tecniche o ripetizioni del titolo. Evita di creare doppioni: se esiste già un file con il nuovo nome, salta quel fumetto; se il nome è già “corretto”, lo lascia così com’è.

Come si usa:

Rendi lo script eseguibile e lancialo indicando la cartella dei fumetti:

​chmod +x rename_comics_universal.sh
./rename_comics_universal.sh

in alternativa installare rename-comics-universal_2.7.deb

sudo dpkg -i rename-comics-universal_2.7.deb
rename_comics_universal

In alternativa puoi farlo partire senza parametri e inserire il percorso quando richiesto, oppure confermare/modificare l’intestazione proposta (il nome della serie).

Perché è utile per i collezionisti

Risparmia tempo: invece di rinominare centinaia di file a mano, basta un comando e la cartella viene normalizzata.
Migliora la ricerca: con nomi coerenti è più facile trovare un numero specifico o sfogliare l’intera serie in un file manager o in un reader.
È pensato in particolare per fumetti italiani ed americani di scansioni “reali”, dove i nomi dei file spesso includono un sacco di informazioni superflue. Altamente configurabile aggiungendo eventuali nomi da rimuovere all'interno dello script. Nei fumetti in inglese bisognerà adattarlo, oppure chiedere eventuali modifiche.
