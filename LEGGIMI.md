# Green Up – cartellone botanico interattivo

## Contenuto
10 piante (basilico, rosmarino, salvia, menta, lavanda, prezzemolo, tulipano, narciso, giacinto, croco) in 6 lingue: italiano (it), rumeno (ro), russo (ru), albanese (sq), arabo (ar), spagnolo (es). I testi vengono dal documento «Podcast erbe e bulbi 6 lingue». L’arabo si legge da destra a sinistra.

## Struttura
```
GREEN_UP/
├── index.html                pagina (non serve modificarla)
├── piante.json               piante, nomi scientifici, testi e lingue
├── elenco_registrazioni.csv  i 60 nomi di file da registrare
├── immagini/                 una foto per pianta: basilico.jpg, rosmarino.jpg ...
└── audio/
    ├── basilico/   basilico_it.mp3, basilico_ro.mp3, basilico_ru.mp3,
    │               basilico_sq.mp3, basilico_ar.mp3, basilico_es.mp3
    ├── rosmarino/  rosmarino_it.mp3 ...
    └── ... (una cartella per pianta, già create)
```

## Come si collegano le registrazioni
Non serve modificare nulla: quando in `audio/<pianta>/` c’è il file `<pianta>_<lingua>.mp3`, la pagina lo trova da sola e attiva il pulsante. Se il file manca, il pulsante mostra «Audio in arrivo».
Il nome del file deve essere esatto, tutto minuscolo (vedi `elenco_registrazioni.csv`). Non mettere i nomi degli studenti nei nomi dei file.

## Immagini
Salva una foto per pianta in `immagini/` con il nome della pianta e l’estensione `.jpg` (es. `tulipano.jpg`). Formato consigliato 4:3, larghezza 1000-1200 px, meno di 300 KB. Se vuoi indicare autore e licenza, aggiungi in `piante.json`, dentro la pianta, la riga `"crediti": "Foto: ..., licenza ..."`.

## Nomi scientifici da verificare
Nel file ho inserito i nomi scientifici più comuni; per menta, tulipano, narciso e croco ho indicato solo il genere, perché il testo non dice di quale specie si tratta. Sostituiscili con quelli scelti dagli studenti per il cartellone (campo `"nomeScientifico"` in `piante.json`).

## Audio
- Letture di circa 20-30 secondi, in ambiente silenzioso, telefono vicino alla bocca.
- Esporta in MP3 mono a 64 kbps: ogni file pesa circa 150-250 KB, in totale circa 12-15 MB per le 60 registrazioni.
- Per il russo, la guida alla pronuncia presente nel documento serve a chi legge: non è stata inserita nel sito.

## Provare in locale
Aprire `index.html` con doppio clic non funziona (il browser blocca la lettura di `piante.json`). Dalla cartella GREEN_UP:
```
python3 -m http.server 8000
```
poi apri `http://localhost:8000`.

## Pubblicare su GitHub Pages
1. Crea un repository pubblico e carica il **contenuto** della cartella (*Add file → Upload files*).
2. *Settings → Pages* → branch `main`, cartella `/ (root)`.
3. L’indirizzo sarà `https://NOME.github.io/REPOSITORY/`.
Per aggiungere le registrazioni basta caricare gli MP3 nella cartella giusta.

## QR code
- QR generale del cartellone: l’indirizzo del sito seguito da `#piante` (elenco delle piante). L’indirizzo semplice apre la Home del progetto.
- QR della pianta: l’indirizzo seguito da `#id`, ad esempio `https://NOME.github.io/REPOSITORY/#tulipano`.
- Generali solo a sito pubblicato, e usa codici **statici** (senza scadenza).

## Prima di pubblicare le voci
- Liberatorie dei genitori per la diffusione delle registrazioni.
- Il sito non mostra i nomi di chi legge: così deve restare.
- Immagini con licenza adatta.

## Le sezioni del sito
Menu: **Home**, **Piante**, **Fasi del lavoro**, **Dati**. Ogni sezione legge un proprio file; per cambiare un contenuto si modifica il file con l’icona a matita su GitHub e si conferma con *Commit changes*.

- **Home** – `home.json`: titolo, presentazione, riquadri e pulsante del documento. Il documento completo è `documenti/Progetto_Green-up_your_school.pdf`: per aggiornarlo basta caricare in quella cartella un PDF con **lo stesso nome**.
- **Fasi del lavoro** – `fasi.json`: per ogni fase cambia `"stato"` in `"fatto"`, `"incorso"` o `"dafare"`, e se vuoi scrivi `"periodo"` e `"avanzamento"`. La barra e la linea del tempo si aggiornano da sole. Foto: caricale in `fasi/` e aggiungi nella fase `"foto": [{"file": "fasi/cartellone-1.jpg", "didascalia": "Gli studenti al lavoro"}]`. Niente volti riconoscibili senza liberatoria.
- **Dati** – `dati.json`: ora contiene dati di esempio (`"esempio": true`). Per usarlo a mano sostituisci le serie di numeri con le misure reali e porta `"esempio"` a `false`. In futuro i dati potranno arrivare automaticamente dai sensori.
