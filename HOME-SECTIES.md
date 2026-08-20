# Homepagina — optionele secties instellen

De homepagina toont sinds deze update, naast "Volgende speeldag", ook een
reeks **optionele** uitklapbare kaartjes: Laatste nieuws, Sperrepelkesploeg,
Sperrepelkes CUP, 180's, Hoogste checkout, en een Sponsor-banner onderaan.

**Elke sectie is optioneel.** Heb je een tabblad nog niet aangemaakt (of
laat je de placeholder-URL in `config.js` staan), dan verschijnt die sectie
gewoon niet — geen foutmelding, geen kapotte layout. Je kan dus per sectie
kiezen of en wanneer je die activeert.

## Zo activeer je een sectie

1. Maak in dezelfde Google Sheet een nieuw tabblad met de kolommen zoals
   hieronder beschreven.
2. Publiceer dat tabblad als CSV: `Bestand > Delen > Publiceren op web` →
   kies het specifieke tabblad → formaat "Kommagescheiden waarden (.csv)".
3. Plak de gegenereerde URL in `js/app.js`, bovenaan bij `EXTRA_URLS`, bij
   de juiste sleutel (`nieuws`, `ploeg`, `cup`, `achttienen`, `checkout`,
   of `sponsor`).

## Kolomstructuur per tabblad

### 📰 Nieuws (`nieuws`)
Met kopregel:

| Datum | Titel | Tekst | Link |
|---|---|---|---|
| 15/08/2026 | Nieuwe dartborden! | We hebben 2 nieuwe boards hangen. | |
| 10/08/2026 | Ledenvergadering | Op 1 september om 20u. | https://... |

`Link` is optioneel. Het nieuwste bericht (op basis van `Datum`) wordt als
samenvatting getoond; de 5 recentste verschijnen in de uitklap.

### 🏆 Sperrepelkesploeg (`ploeg`)
**Zonder** kopregel — telkens een label en een waarde:

| | |
|---|---|
| Laatste wedstrijd | Sperrepelkes - KDC Leiestreek |
| Laatste wedstrijd datum | 12/07/2026 |
| Laatste wedstrijd uitslag | 7-5 winst |
| Volgende wedstrijd | Sperrepelkes - Darts Wakken |
| Volgende wedstrijd datum | 20/09/2026 |
| Ranking | 3e plaats (24 punten) |

Enkel deze exacte labels worden herkend; andere rijen worden genegeerd.
Laat een rij gewoon weg als je die info (nog) niet hebt.

### 🏅 Sperrepelkes CUP (`cup`)
**Zonder** kopregel, zelfde principe:

| | |
|---|---|
| Volgende datum | 14/03/2026 |
| Locatie | Ons lokaal |
| Info | Inschrijven kan tot 1 maart |

### 🎯 180's (`achttienen`)
Met kopregel:

| Speler | Aantal |
|---|---|
| Jan Peeters | 4 |
| Piet Janssens | 3 |

De speler(s) met het hoogste aantal worden als "leider(s)" getoond
(ex aequo mag).

### 🔥 Hoogste checkout (`checkout`)
Met kopregel:

| Speler | Uitworp | Datum |
|---|---|---|
| Jan Peeters | 156 | 12/07/2026 |

`Datum` is optioneel.

### Sponsor van de week (`sponsor`)
Met kopregel — zet gewoon **al je sponsors onder elkaar**, één rij per sponsor:

| Naam | Tekst | Website | Afbeelding |
|---|---|---|---|
| Café De Toog | Jouw stamcafé na de wedstrijd! | https://cafedetoog.be | https://i.imgur.com/abc123.png |
| Bouwteam DSM | DSM TEAM bv, Impestraat 23, 9420 Erondegem | https://www.bouwteamdsm.be/ | https://i.imgur.com/xyz789.png |

Enkel `Naam` is verplicht. `Afbeelding` is een directe beeld-URL: upload je
logo gratis op **imgur.com**, kopieer de "directe link" (eindigt op
`.png`/`.jpg`), en plak die hier. Laat je dit veld leeg, dan toont de app
een nette tekst-only kaart.

**Automatische wekelijkse rotatie:** de app kiest zelf, op basis van de
huidige kalenderweek, telkens een andere sponsor uit deze lijst — iedereen
die de app in dezelfde week opent ziet dezelfde sponsor, en de week erna
schuift het automatisch door naar de volgende rij. Is de lijst doorlopen,
dan begint het gewoon weer bij de eerste. Je hoeft dus niets manueel om te
wisselen: eenmaal alle sponsors in het tabblad staan, draait het vanzelf.
De volgorde van de rijen bepaalt de volgorde van de rotatie.
