# Saldo — app personale per Android

Saldo è una PWA (Progressive Web App) per la gestione personale delle finanze. Non richiede account, backend o servizi esterni: i dati vengono salvati nel `localStorage` del browser sul dispositivo.

## Funzioni incluse
- Dashboard con saldo totale, entrate, uscite, risparmio netto e andamento degli ultimi 6 mesi.
- Movimenti: uscite, entrate e trasferimenti tra conti; scheda di dettaglio al tocco con descrizione e note, modifica, eliminazione, ricerca e filtro.
- Categorie e sottocategorie di base (categorie personalizzabili nel codice).
- Conti multipli con aggiornamento automatico dei saldi e saldo iniziale.
- Budget mensili per categoria.
- Analisi con distribuzione delle spese.
- Obiettivi di risparmio.
- Esportazione Excel `.xlsx` mensile strutturata per analisi: Dashboard, Categorie, Movimenti, Budget e riepilogo Giornaliero; formati in euro e percentuali, filtri, intestazioni bloccate e indicatori visivi.
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
- Tocca una riga o una voce di movimento per aprire la scheda completa con descrizione, note, conto, metodo e data; da qui puoi modificarlo.
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


## Aggiornamento grafico 2.0
- Navigazione inferiore ottimizzata per smartphone con accesso rapido alle sezioni principali.
- Pulsante flottante per registrare rapidamente un movimento.
- Schede, pulsanti, moduli e grafici ridisegnati per un uso touch.
- Accesso rapido a Conti e Obiettivi dalla sezione Altro/Impostazioni.
- Cache PWA aggiornata alla versione 2 per forzare il caricamento dei nuovi file.


## Aggiornamento 2.1.0
- Scheda dettagliata dei movimenti apribile toccando una voce, con descrizione e note sempre visibili.
- Report Excel mensile riorganizzato in cinque fogli: Dashboard, Categorie, Movimenti, Budget e Giornaliero.
- Migliorata la leggibilità e l'interazione touch degli elenchi.
- La struttura di archiviazione `localStorage` (`saldo-data`) è rimasta invariata: l'aggiornamento non migra, cancella o sovrascrive i movimenti esistenti.


## Versione 2.4.0
- Analisi avanzate con andamento entrate/uscite su 6 o 12 mesi.
- Confronto automatico con il mese precedente, tasso di risparmio e spesa media giornaliera.
- Stima delle uscite a fine mese per il mese corrente.
- Distribuzione delle spese per categoria e analisi per giorno della settimana.
- Individuazione indicativa di possibili spese ricorrenti (basata su descrizione e importo ripetuti).
- Filtri movimenti per conto e intervallo di date, oltre a ricerca e tipologia.
- Aggiornamento cache PWA per distribuire la nuova versione senza cancellare i dati locali.

I dati restano nella stessa chiave locale `saldo-data`; non è richiesta alcuna migrazione.

## Versione 2.3.0 — restyling mobile
- Interfaccia più leggibile: caratteri, controlli, pulsanti e spaziature aumentati.
- Palette più vivace con colori distinti per entrate, uscite, budget e azioni principali.
- Pagina Movimenti con schede verticali ottimizzate per smartphone; la tabella resta disponibile su schermi più ampi.
- Filtri ridisposti in una griglia mobile più chiara; ricerca estesa anche alle note.
- Budget e statistiche con gerarchia visiva più chiara e barre di avanzamento più leggibili.
- Cache PWA aggiornata per distribuire la nuova interfaccia.
- Nessuna modifica alla struttura dei dati o alla chiave localStorage `saldo-data`.


## Versione 2.4.0 — sottocategorie e Sport
- Aggiunta la categoria di spesa Sport, con budget iniziale pari a 0 € (modificabile).
- Possibilità di creare sottocategorie personalizzate per ciascuna categoria di spesa da Impostazioni → Categorie e sottocategorie.
- Le sottocategorie sono selezionabili quando si crea o modifica un movimento; i movimenti precedenti restano validi senza sottocategoria.
- Dettagli, elenchi, ricerca, esportazione CSV ed Excel includono la sottocategoria.
- Il foglio Excel Categorie include anche un riepilogo specifico per sottocategoria; il budget continua a essere gestito e aggregato sulla categoria principale.
- I dati aggiuntivi sono salvati nella stessa chiave `saldo-data`; nessun movimento esistente viene cancellato o riscritto.


## Versione 2.5.0 — analisi e personalizzazione
- Modulo movimento riordinato: nome, categoria e sottocategoria, importo, metodo di pagamento, una sola data, conto e note.
- Grafici mensili con colonne delle uscite impilate per categoria; segmenti colorati proporzionali alla spesa di ciascuna categoria.
- Media giornaliera calcolata sull'intero numero di giorni del mese.
- Rimossa la scheda «In sintesi» dalla pagina Analisi.
- Le categorie nel dettaglio Analisi sono selezionabili e aprono un grafico giornaliero del mese (giorni sull'asse X, importo sull'asse Y).
- Excel riorganizzato in sei fogli: Dashboard, Categorie, Sottocategorie, Movimenti, Budget e Giornaliero; dashboard con indicatori in evidenza, tabelle, formati euro/percentuali, intestazioni bloccate, filtri e colori coerenti.
- Aggiunta la scelta del colore principale dell'interfaccia: viola, blu, smeraldo, corallo e ambra.
- La chiave locale `saldo-data` e la struttura dei movimenti restano compatibili; nessun dato viene cancellato o migrato.
