# Bigliettino digitale per Noemi 💌

Pagina statica (un solo `index.html`, niente build, niente librerie) pensata per essere aperta dal telefono.

L'apertura parte **da sola** appena la pagina è visibile (pensata per un tag NFC sul pacco): busta che cade, sigillo che batte, scoppio di petali e cuori, la carta esce e si apre diventando il biglietto. Durata ~5s. In fondo c'è "↺ Rivedi l'apertura".

Per il tag NFC: scrivi sul tag un record URL con l'indirizzo GitHub Pages (es. con l'app gratuita *NFC Tools*).

## Due versioni

| File | Apertura |
|---|---|
| `index.html` | Busta rosa con sigillo di ceralacca che batte ed esplode |
| `alternativa.html` | Pacco regalo: fiocco che si scioglie, coperchio che salta, raggi di luce e coriandoli |

Il biglietto interno è identico. Sono pubblicate entrambe:
- `https://<utente>.github.io/bigliettino-noemi/` → busta
- `https://<utente>.github.io/bigliettino-noemi/alternativa.html` → pacco

Scrivi sul tag NFC l'URL della versione scelta. I due file sono indipendenti: se modifichi `CONFIG`, fallo in quello che usi.

## Modificare testi e colori

Apri `index.html` e cerca `const CONFIG` all'inizio dello `<script>`, in fondo al file. Tutto quello che si vede nella pagina sta lì:

| Chiave | Cosa cambia |
|---|---|
| `destinatario` | Nome usato nell'etichetta accessibile della busta |
| `titolo` | Titolo sul biglietto e nella scheda del browser ("Per Noemi") |
| `sopratitolo` | Piccola riga in maiuscolo sopra il titolo ("Da parte di tutti noi") |
| `sottotitolo` | Frase sotto la busta durante l'apertura |
| `messaggio` | La dedica: un array, **un elemento = un paragrafo** |
| `titoloNomi` | Intestazione della lista dei partecipanti |
| `etichettaConteggio` | Testo accanto al numero dei partecipanti ("colleghi, un solo pensiero") |
| `invitoScorri` | Etichetta del pulsantino che invita a scorrere |
| `partecipanti` | I nomi, mostrati nell'ordine e con la grafia esatti |
| `firmaIntro` / `firma` | Chiusura ("Con tutto il nostro affetto," / "I tuoi colleghi") |
| `colori` | Palette: sfondo, busta/pacco, ombra, accento (sigillo/titoli/cuori), biglietto, bordo, testo |
| `petali` | Numero di petali (15–25 consigliato) |

Esempio, aggiungere un paragrafo:

```js
messaggio: [
  "Primo paragrafo…",
  "Secondo paragrafo…",
  "Nuovo paragrafo."
],
```

Le virgolette doppie dentro un testo vanno scritte come `\"`; gli apostrofi vanno bene così come sono.

> Nota: titolo e anteprima del link (tag `og:title` nell'`<head>`) sono scritti a mano: se cambi destinatario, aggiornali anche lì.

## Provare in locale

```bash
python3 -m http.server 8000
```

Poi apri http://localhost:8000.

## Accessibilità

Con "Riduci movimento" attivo sul dispositivo, il biglietto compare già aperto, senza busta, petali o animazioni.
