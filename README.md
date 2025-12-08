# RCU - Rename Comics Universal

**Rename Comics Universal** is an app for Linux and Windows designed to automatically rename digital comic files (PDF, CBR, CBZ, EPUB) by detecting the series name, issue number, and optional title.

---

[🇬🇧 English](#-english-version) | [🇮🇹 Italiano](#-versione-italiana)

---

# 🇬🇧 ENGLISH VERSION


## Download for Linux

You can get the full RCU package (Linux & Windows, with source code and installers) on Buy Me a Coffee:


👉 https://buymeacoffee.com/fconidi/e/487102


![RCU-Linux](https://github.com/user-attachments/assets/bc53bd6f-f58e-46b4-a549-c11d6d5e6e1d)



## Download for Windows

You can get the full RCU package (Linux & Windows, with source code and installers) on Buy Me a Coffee:

👉 https://buymeacoffee.com/fconidi/e/485941


![RCU-Windows](https://github.com/user-attachments/assets/54f76cfd-9796-4965-afc6-507c466448b8)



## Overview

**Rename Comics Universal (RCU)** is a Bash script designed to automatically rename digital comic files (PDF, CBR, CBZ, EPUB) by detecting the series name, issue number, and optional title, producing clean and consistent filenames like **"Comics_Name 033 - Clean Title.cbz"**.

It is aimed at readers and collectors who want to tidy up messy file names full of tags such as "scan", "by", group names, or random notes.

## Main Technical Features

- **Format detection**: Scans a chosen directory and processes only PDF, CBR, CBZ, and EPUB files, ignoring subfolders
- **Smart extraction**: Uses regular expressions to isolate issue numbers (e.g., "033" or "N.33") and titles, removing tokens like "ScanBy", "by", "edit" with common Unix tools
- **Automatic cleanup**: Applies functions to normalize spacing, remove brackets and special characters, and convert titles to proper title case, while padding issue numbers to three digits (e.g., 033)
- **Header detection**: Analyzes filenames to find the most frequent series header (such as "Zagor" or "Dylan Dog"), which can be confirmed or changed via a Zenity GUI dialog
- **Colored output**: Shows colored terminal messages for successes and skips and prints a final summary with counters

## How It Works

The script asks for a target folder either via command-line argument or through a small Zenity window, then scans all supported files in that directory.

For each file it tries to determine:
1. The series name
2. The issue number location
3. Any following title that can be cleaned up

It then builds a standardized name in one of these forms:

- **"Series 001 - Clean title.ext"** when a title can be extracted
- **"Series 001.ext"** when no usable title is found

If a file is already correctly named or a file with the target name already exists, the script skips it to avoid duplicates or overwrites.

## What It Fixes Automatically

✅ Removes useless tags like "scan by…", "edited", "by scan", release group labels, or redundant technical notes  
✅ Normalizes capitalization so that important words start with an uppercase letter, while articles and prepositions stay lowercase where appropriate  
✅ Strips brackets and their internal content when they only contain technical info or repeated titles  
✅ Keeps numbering consistent with three digits, which is especially helpful for long-running series  

## Usage

### Linux Terminal

```bash
chmod +x rename_comics_universal.sh
./rename_comics_universal.sh
```

### Or Using .deb Package

```bash
sudo dpkg -i rename-comics-universal_2.7.deb
rename_comics_universal
```

### For Windows only drag and drop


## Why It Is Useful for Collectors

- **Saves time**: Renames hundreds of files in one go instead of doing it manually
- **Improves browsing**: Makes the library easier to navigate in file managers and comic readers
- **Lightweight**: No dependencies beyond Bash and optionally Zenity
- **Highly configurable**: Easy to customize for specific needs
- **Perfect for scans**: Particularly suited to Italian and English comics from real scans, where filenames often contain many superfluous details

## Video/Screencast Linux

[Watch demo video](https://github.com/user-attachments/assets/6e5d87a3-7b75-423d-adc6-f67b4f0a4c72)

---
---
---

## Video/Screencast Windows

![RCU-Windows](https://github.com/user-attachments/assets/91466ea5-865f-4492-a52e-d4d1f590d32d)

---
---
---

## 📋 Requirements

- **Linux**: Bash 4.0+, Zenity (opzionale per GUI)
- **Windows**: Powershell
- **Supported formats**: PDF, CBR, CBZ, EPUB

## 👤 About

**Franco Conidi aka Edmond - SysLinuxOS**  
System Integrator, Network Engineer, IT Consultant
Blogger Linux


# 🇮🇹 VERSIONE ITALIANA


## Scarica zip per Linux

You can get the full RCU package (Linux & Windows, with source code and installers) on Buy Me a Coffee:

👉 https://buymeacoffee.com/fconidi/e/487102


![RCU-Linux](https://github.com/user-attachments/assets/bc53bd6f-f58e-46b4-a549-c11d6d5e6e1d)



## Scarica zip per Windows

You can get the full RCU package (Linux & Windows, with source code and installers) on Buy Me a Coffee:

👉 https://buymeacoffee.com/fconidi/e/485941


![RCU-Windows](https://github.com/user-attachments/assets/54f76cfd-9796-4965-afc6-507c466448b8)



## Panoramica

Hai una collezione di fumetti digitali in disordine? **Rename Comics Universal (RCU)** è uno script bash universale che automatizza il rinominamento di file PDF, CBR, CBZ ed EPUB, estraendo intestazioni comuni (come "Zagor", "Spider-Man" o "Dylan Dog"), numeri di albo e titoli, per ottenere nomi puliti e standardizzati.

## Caratteristiche Tecniche Principali

- **Riconoscimento Formati**: Analizza PDF, CBR, CBZ, EPUB in una directory specifica, ignorando sottodirectory
- **Estrazione Intelligente**: Regex per isolare numeri (es. "033", "N.33") e titoli, rimuovendo token come "ScanBy", "by", "edit" con sed -E e tr
- **Pulizia Automatica**: Funzioni `clean_title` e `title_case` per Title Case, eliminazione di parentesi, spazi multipli e caratteri speciali; padding numerico a 3 cifre (es. "Zagor 033 - Titolo pulito.cbz")
- **Header Detection**: Cerca il nome del fumetto e seleziona quello principale o quello più comune, si può modificare tramite Zenity GUI
- **Output Colorato**: ANSI colors (GREEN per successi, YELLOW per skip), summary finale con contatori

## Come Funziona

1. **Seleziona cartella** via CLI o Zenity
2. **Detect header**: Scansiona file, estrae potenziali header (pre-numero), sceglie il più frequente
3. **Rename files**: Per ogni file, estrae numero + titolo, applica pulizia, formatta nuovo nome e rinomina (con check duplicati)

Lo script analizza tutti i file supportati nella cartella e cerca di capire:
- Qual è il "nome serie" più usato (es. "Zagor", "Dylan Dog")
- Dove si trova il numero dell'albo nel nome del file
- Se dopo il numero è presente un titolo da ripulire

Per ogni file costruisce un nuovo nome del tipo:

- **"Serie 001 - Titolo pulito.cbz"** se esiste un titolo
- **"Serie 001.cbz"** se non c'è titolo recuperabile

## Cosa Sistema Automaticamente

✅ Toglie scritte inutili come "scan by…", "edited", "colori", tag di gruppi, ecc.  
✅ Sistema maiuscole/minuscole: articoli e preposizioni rimangono in minuscolo, le parole importanti hanno l'iniziale maiuscola  
✅ Elimina parentesi e contenuto dentro le parentesi quando sono solo note tecniche o ripetizioni del titolo  
✅ Evita di creare doppioni: se esiste già un file con il nuovo nome, salta quel fumetto  

## Vantaggi

- **Ideale per collezioni italiane** (Zagor, Tex Willer) o USA (Marvel/DC)
- **Gestisce varianti** underscore/spazi, normalizza zeri iniziali
- **Evita sovrascritture** con error handling robusto
- **Personalizzabile** per nuovi formati estendendo il loop
- **Script leggero** (13KB), zero dipendenze oltre bash/zenity (opzionale)

## Come Si Usa

### Linux Terminal

```bash
chmod +x rename_comics_universal.sh
./rename_comics_universal.sh
```

### Oppure Installare il Pacchetto .deb

```bash
sudo dpkg -i rename-comics-universal_2.7.deb
rename_comics_universal
```

In alternativa puoi lanciarlo senza parametri e inserire il percorso quando richiesto, oppure confermare/modificare l'intestazione proposta (il nome della serie).


### Windows basta solo drag and drop da powershell


## Perché è Utile per i Collezionisti

- **Risparmia tempo**: Invece di rinominare centinaia di file a mano, basta un comando
- **Migliora la ricerca**: Con nomi coerenti è più facile trovare un numero specifico o sfogliare l'intera serie
- **Pensato per fumetti italiani ed americani**: Gestisce scansioni "reali" dove i nomi dei file spesso includono un sacco di informazioni superflue
- **Altamente configurabile**: Aggiungendo eventuali nomi da rimuovere all'interno dello script

> **Nota**: Per fumetti in inglese potrebbe richiedere adattamenti

## Video/Screencast Linux

[Guarda il video dimostrativo](https://github.com/user-attachments/assets/6e5d87a3-7b75-423d-adc6-f67b4f0a4c72)

---
---
---

## Video/Screencast Windows

![RCU-Windows](https://github.com/user-attachments/assets/91466ea5-865f-4492-a52e-d4d1f590d32d)



---

## 📋 Requisiti

- **Linux**: Bash 4.0+, Zenity (opzionale per GUI)
- **Windows**: Powershell
- **Formati supportati**: PDF, CBR, CBZ, EPUB

## 👤 Autore

**Franco Conidi aka Edmond - SysLinuxOS**  
System Integrator, Network engineer, IT Consultant
Blogger Linux Developer

---

**Versione**: 2.7 | **Data**: Dicembre 2025 | **Piattaforma**: Linux/Windows

🎉 **Scarica ed ordina la tua libreria in pochi secondi!** 🎉
