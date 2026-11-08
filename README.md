# Saldo — app personale per Android

Saldo è una PWA (Progressive Web App) per la gestione personale delle finanze. Non richiede account, backend o servizi esterni: i dati vengono salvati nel `localStorage` del browser sul dispositivo.

## Funzioni incluse
- Dashboard con saldo totale, entrate, uscite, risparmio netto e andamento degli ultimi 6 mesi.
- Movimenti: uscite, entrate e trasferimenti tra conti; modifica, eliminazione, ricerca e filtro.
- Categorie e sottocategorie di base (categorie personalizzabili nel codice).
- Conti multipli con aggiornamento automatico dei saldi e saldo iniziale.
- Budget mensili per categoria.
- Analisi con distribuzione delle spese.
- Obiettivi di risparmio.
- Esportazione Excel `.xlsx` mensile con fogli Riepilogo, Categorie, Movimenti e Budget.
- Esportazione CSV, backup JSON e ripristino.
- Tema chiaro/scuro.
- Cache offline tramite Service Worker.

## Installazione su Android
Una PWA deve essere servita da un indirizzo HTTPS (oppure localhost per test). Non basta aprire `index.html` dal file manager.

### Opzione rapida: GitHub Pages
1. Estrai lo ZIP sul computer.
2. Crea un repository GitHub privato o pubblico e carica tutti i file nella cartella principale.
3. In Settings → Pages abilita la pubblicazione dal branch principale, cartella `/root`.
4. Apri l'indirizzo HTTPS generato da Chrome su Android.
5. Menu ⋮ → **Installa app** oppure **Aggiungi a schermata Home**.

### Opzione senza GitHub
Puoi servire la cartella da un computer sulla stessa rete con un server HTTPS, oppure usare un hosting statico HTTPS. Una volta installata e aperta almeno una volta, le risorse dell'app sono disponibili offline.

## Uso
- Premi **Nuovo movimento** per registrare una spesa o un'entrata.
- Per un trasferimento seleziona conto di origine e destinazione: non viene conteggiato come spesa o entrata.
- I saldi iniziali dei conti si inseriscono creando un conto e specificando il saldo iniziale.
- Seleziona il mese nella schermata per filtrare dashboard, movimenti, budget e analisi.
- Vai in Impostazioni → Esporta Excel mensile per scaricare il file `.xlsx`.
- Fai periodicamente un backup JSON, soprattutto prima di cancellare dati del browser o cambiare telefono.

## Nota sulla privacy e sui limiti
I dati sono locali al browser/profilo Android. Disinstallare i dati del browser, cancellare la memoria del sito o usare un browser diverso può cancellarli/non renderli disponibili: usa il backup JSON. Non è prevista la sincronizzazione automatica tra dispositivi né l'importazione diretta bancaria. L'Excel è creato localmente dall'app, senza inviare transazioni a servizi esterni.

## Struttura
- `index.html` interfaccia
- `styles.css` stile responsive e temi
- `app.js` logica, archivio locale ed esportazione XLSX
- `manifest.webmanifest` metadati PWA
- `sw.js` cache offline
- `icon.svg` icona
