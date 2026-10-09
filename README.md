# RCU — Rename Comics Universal 2.8.1

[Italiano](#italiano) | [English](#english)

## Download Linux

Download e supporto / Download and support — Buy Me a Coffee:

https://buymeacoffee.com/fconidi/e/487102

<img width="230" height="230" alt="rcu-qr-linux" src="https://github.com/user-attachments/assets/f188202e-01e6-4717-961c-e7dae397eec6" />

## Italiano

RCU riordina i nomi dei fumetti PDF, CBR, CBZ ed EPUB su Linux. Analizza i nomi,
mostra un'anteprima e rinomina solo dopo conferma. Non legge né modifica il
contenuto degli archivi. Ogni file mantiene la propria serie nelle cartelle miste.

## Requisiti e installazione

Servono Bash e Python 3.9 o successivo. Zenity abilita le finestre grafiche.

```bash
sudo apt install ./rename-comics-universal_2.8.1_all.deb
rename_comics_universal --gui
```

Per avviare gli script del pacchetto scaricato, conservare la cartella `lib/` accanto al launcher:

```bash
./rename_comics_universal --help
./rename_comics_universal --cli --dry-run /percorso/Fumetti
```

## Anteprima e conferma

Senza argomenti RCU usa Zenity se è disponibile una sessione grafica; altrimenti
chiede il percorso nel terminale. Un percorso passato come argomento seleziona
la CLI, anche quando Zenity è installato. `--cli` e `--gui` rendono la scelta esplicita.
Se la GUI non è disponibile, `--gui` ripiega sul terminale.

La GUI consente di scegliere **Rinomina file** oppure **Annulla ultima operazione**,
selezionare la cartella, confermare la serie e controllare la tabella dei nomi.
Lasciare vuota la serie mantiene il rilevamento per ciascun file. Una serie inserita
esplicitamente viene applicata a tutti i file. Nell'anteprima si possono deselezionare
singoli file. **Annulla** interrompe la procedura prima delle rinomine.
Se più versioni producono lo stesso nome, sono inizialmente deselezionate:
scegliere **una sola versione per nome proposto**. Le altre conservano il nome
originale. Selezionandone più di una, RCU segnala il conflitto e le lascia intatte.
La CLI non sceglie automaticamente fra versioni duplicate.

```bash
# Mostra soltanto il piano; non scrive nemmeno il registro.
rename_comics_universal --cli --dry-run /percorso/Fumetti

# Mostra il piano e chiede conferma.
rename_comics_universal --cli /percorso/Fumetti

# Applicazione esplicita senza richiesta interattiva.
rename_comics_universal --cli --yes /percorso/Fumetti

# Intestazione comune, utile per nomi come 033_Il_ponte.cbz.
rename_comics_universal --cli --header "Zagor" /percorso/Fumetti
```

Il secondo argomento posizionale resta disponibile come alternativa a `--header`:
`rename_comics_universal /percorso/Fumetti "Zagor"`.

## Formato e pulizia

Il formato è `Serie 001 - Titolo.cbz`, oppure `Serie 001.cbz` senza titolo.
Le estensioni diventano minuscole; i numeri hanno almeno tre cifre.

```text
Tex_001_Area_N.51.cbz              → Tex 001 - Area N.51.cbz
Batman_003_Stand_By_Me.cbz          → Batman 003 - Stand By Me.cbz
Zagor_002_Il_ritorno_(Parte_2).cbz → Zagor 002 - Il ritorno (Parte 2).cbz
Zagor N.733 - Il Regno Sommerso (SBE 2026-08-04) Rocky V (Colorazione 2.2 by Roy).pdf
                                → Zagor 733 - Il Regno Sommerso.pdf
```

La capitalizzazione originale viene conservata. `--title-case` la normalizza,
preservando sigle brevi come DC e USA. Anni, parole come "By" e "Scan" e contenuti
sconosciuti fra parentesi rimangono nel titolo. RCU rimuove metadati riconosciuti,
come `[dinofelix]`, suffissi scanner noti, `scan by ...` e date editoriali con
editore riconosciuto. Il primo blocco editore/data (anno, mese/anno o data ISO),
oppure una nota fra parentesi di colorazione/versione, segna l'inizio dei metadati:
quel blocco e tutto ciò che segue vengono rimossi. L'estensione segue il titolo;
il formato del file rimane lo stesso. I tag aggiuntivi si configurano con un file UTF-8:

```text
# Un suffisso letterale per riga
MioScanner
A+B
```

```bash
rename_comics_universal --cli --tags-file tags.txt /percorso/Fumetti
```

Vengono elaborati solo file regolari della cartella scelta. Sottocartelle e link
simbolici sono esclusi. Numerazioni non riconosciute o frazionarie vengono saltate.
I nomi ambigui vanno controllati nell'anteprima; i file senza serie richiedono
`--header`, oppure una sola serie riconoscibile nella cartella.

## Registro e annullamento

```bash
rename_comics_universal --cli --undo /percorso/Fumetti
rename_comics_universal --cli --yes --undo /percorso/Fumetti
```

Ogni operazione registra i nomi originali e l'identità dei file in
`$XDG_STATE_HOME/rename-comics-universal/`, normalmente
`~/.local/state/rename-comics-universal/`. Conservare questi registri per poter
annullare. L'annullamento ripristina i nomi, non il contenuto dei fumetti.

RCU rifiuta sovrascritture anche quando una destinazione compare dopo l'anteprima.
Se un file cambia dopo l'anteprima o dopo la rinomina, oppure il nome originale
è occupato, viene lasciato al suo posto e l'errore viene segnalato. Il ripristino
può essere parziale: risolvere il conflitto e ripetere `--undo` per i file rimanenti.
Due operazioni RCU sulla stessa cartella, con lo stesso registro, sono serializzate.

Il riepilogo distingue rinominati/ripristinati, invariati, saltati, conflitti ed errori.
Codici di uscita: `0` successo o annullamento, `1` errori/conflitti, `2` uso CLI errato.

## Pacchetto Debian

Il pacchetto `rename-comics-universal_2.8.1_all.deb` installa il comando in
`/usr/bin` e i moduli in `/usr/share/rename-comics-universal`.
Richiede Python 3.9 o successivo; Zenity abilita i dialoghi grafici.

## English

RCU previews and normalizes comic filenames on Linux. Requires Bash and Python
3.9+; Zenity is optional. Mixed folders preserve each file's series. Names use
`Series 001 - Title.ext`; original capitalization and unknown metadata are retained.
Recognized publisher/date or bracketed colorization/version notes start a metadata
tail: that marker and everything after it are removed, preserving the file format.

```bash
rename_comics_universal --cli --dry-run ~/Comics
rename_comics_universal --cli --yes ~/Comics
rename_comics_universal --cli --header "Batman" ~/Comics
rename_comics_universal --cli --undo ~/Comics
rename_comics_universal --gui
```

Every rename requires confirmation unless `--yes` is passed in CLI mode. GUI
preview checkboxes choose the files. Cancellation leaves filenames unchanged.
For duplicate proposed names, select only one version per name; unselected files
keep their original names. CLI mode leaves duplicate candidates unchanged.
`--title-case` enables capitalization; `--tags-file` reads literal suffix tags.
Existing destinations are never replaced. Undo uses the per-user journal and
refuses occupied original names or files modified since renaming. Subfolders are excluded. Use `--help` for all options.

## Video Linux

[Video dimostrativo della versione precedente / Previous-version demonstration](https://github.com/user-attachments/assets/6e5d87a3-7b75-423d-adc6-f67b4f0a4c72)

## Autore / Author

Franco Conidi aka Edmond — SysLinuxOS.

[Informazioni su RCU](https://francoconidi.it/rcu-rename-comics-universal/) · [francoconidi.it](https://francoconidi.it) · [syslinuxos.com](https://syslinuxos.com)
