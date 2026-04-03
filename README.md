# Zuurdesem Planner

Een interactieve webapp om het bakken van een zuurdesembrood te plannen op basis van tijdvensters, slaapmomenten, drukke periodes en een gewenste uiterlijke klaartijd.

De applicatie helpt bepalen **of** een brood nog in je planning past en **wanneer** je elke stap moet uitvoeren. De planningslogica houdt rekening met minimale en maximale duur per stap, gekoppelde stappen die direct op elkaar moeten volgen en periodes waarin je niet beschikbaar bent.

## Inhoud

- [Functies](#functies)
- [Voor wie](#voor-wie)
- [Hoe de planner werkt](#hoe-de-planner-werkt)
- [Planningsregels](#planningsregels)
- [Gebruiken](#gebruiken)
- [Installatie](#installatie)
- [GitHub Pages publiceren](#github-pages-publiceren)
- [Gebruik op iPhone](#gebruik-op-iphone)
- [Bestandsstructuur](#bestandsstructuur)
- [Technische details](#technische-details)
- [Bekende aandachtspunten](#bekende-aandachtspunten)
- [Toekomstige verbeteringen](#toekomstige-verbeteringen)
- [Licentie](#licentie)

## Functies

- Automatische planning van een zuurdesembrood op basis van een **uiterlijke klaartijd**.
- Invoer van **drukke periodes** met een begin- en eindmoment.
- Invoer van **slaapperiodes** met een begin- en eindmoment.
- Rekenen in **blokken van 30 minuten** voor praktische dagplanning.
- Visuele tijdlijn van alle broodstappen.
- Conflictcontrole tussen actieve broodstappen en jouw agenda.
- Slim zoeken binnen **minimale en maximale tijdvensters** per stap.
- Ondersteuning voor gekoppelde stappen die **direct op elkaar moeten volgen**.
- Donkere en lichte modus.
- Werkt als statische HTML-app, dus zonder backend of database.

## Voor wie

Deze app is bedoeld voor mensen die:

- zuurdesembrood bakken naast werk, afspraken of slaap;
- niet handmatig willen rekenen met alle rust-, rijs- en baktijden;
- vooraf willen weten of een brood **haalbaar** is in de komende 1 tot 2 dagen;
- een simpele webapp willen die ook op mobiel bruikbaar is.

## Hoe de planner werkt

De planner zoekt automatisch een haalbare starttijd vanaf het huidige moment tot aan de gekozen deadline.

Daarbij wordt elk kandidaatmoment getoetst aan:

- jouw drukke periodes;
- jouw slaapperiodes;
- de minimale en maximale duur van specifieke broodstappen;
- vaste ketens van stappen die zonder onderbreking moeten plaatsvinden.

Als er een geldig schema wordt gevonden, toont de app:

- de gekozen starttijd;
- het volledige stap-voor-stap schema;
- een visuele tijdlijn;
- eventuele conflicten.

## Planningsregels

De app houdt rekening met de volgende regels:

### Stap 1 → Stap 2

- De starter moet minimaal **1 uur** en maximaal **12 uur** uit de koelkast zijn.
- Het mengen van de ingrediënten moet dus starten binnen dit venster.

### Stap 2 → Stap 3 → Stap 4

- Na het **mengen** begint direct de **autolyse**.
- De autolyse duurt minimaal **30 minuten** en maximaal **45 minuten**.
- Daarna moet direct het **4× stretch & fold-blok** beginnen.

### Stretch & fold-blok

Dit blok wordt als één aaneengesloten deel ingepland:

1. Stretch & fold 1 — 5 minuten
2. Rust — 30 minuten
3. Stretch & fold 2 — 5 minuten
4. Rust — 30 minuten
5. Stretch & fold 3 — 5 minuten
6. Rust — 30 minuten
7. Stretch & fold 4 — 5 minuten

Dit totale blok mag **niet** worden onderbroken door slaap of andere bezette activiteiten.

### Stap 6 → Stap 7

- Het deeg moet minimaal **1 uur** en maximaal **24 uur** in de koelkast rijzen.
- Daarna moet het moment van voorverwarmen en afbakken logisch aansluiten binnen dat venster.

### Actieve versus passieve stappen

**Actieve stappen** vereisen dat je beschikbaar en wakker bent, bijvoorbeeld:

- ingrediënten mengen;
- stretch & fold;
- oven voorverwarmen;
- brood vormen.

**Passieve stappen** mogen doorlopen terwijl jij iets anders doet of slaapt, bijvoorbeeld:

- starter buiten de koelkast laten staan;
- bulk fermentatie;
- koelkastrijs;
- bakken;
- rusten na bakken.

## Gebruiken

1. Kies een **uiterlijke klaartijd**.
2. Voeg je **drukke periodes** toe met een begin- en eindtijd.
3. Voeg je **slaapperiodes** toe met een begin- en eindtijd.
4. Klik op **Zoek beste planning**.
5. Bekijk de uitkomst in de statuskaart, tijdlijn en stap-voor-stap planning.

## Installatie

Deze app heeft geen installatieproces nodig.

### Lokaal gebruiken

1. Sla de applicatie op als `index.html`.
2. Open het bestand in een browser op desktop.

> Let op: op iPhone werkt een los lokaal HTML-bestand vaak niet goed via de snelle voorvertoning in de Bestanden-app. Gebruik daarvoor liever GitHub Pages of een andere statische hostingoplossing.

## GitHub Pages publiceren

De eenvoudigste manier om de app te delen is via GitHub Pages.

### Stap 1 — Repository maken

Maak een nieuwe GitHub-repository aan, bijvoorbeeld:

```text
zuurdesem-planner
```

### Stap 2 — Bestand toevoegen

Zorg dat het hoofdbestand exact zo heet:

```text
index.html
```

### Stap 3 — Structuur

Gebruik bij voorkeur deze structuur:

```text
zuurdesem-planner/
├── index.html
└── README.md
```

### Stap 4 — GitHub Pages inschakelen

Ga in GitHub naar:

```text
Settings → Pages
```

Kies vervolgens:

- **Source**: Deploy from a branch
- **Branch**: `main`
- **Folder**: `/ (root)`

### Stap 5 — Open de URL

Na publicatie is de app meestal bereikbaar op:

```text
https://jouw-gebruikersnaam.github.io/zuurdesem-planner/
```

## Gebruik op iPhone

Voor iPhone is het aan te raden de gehoste GitHub Pages-link in Safari te openen.

Daarna kun je in Safari kiezen voor:

```text
Deel → Zet op beginscherm
```

Dan voelt de app bijna als een native iPhone-app, zonder dat je iets uit de App Store hoeft te installeren.

## Bestandsstructuur

```text
.
├── index.html
└── README.md
```

## Technische details

- Volledig gebouwd in **HTML, CSS en JavaScript**.
- Geen externe backend nodig.
- Geen database nodig.
- Alle planning gebeurt client-side in de browser.
- Geschikt voor publicatie als statische site.
- Ontworpen voor desktop en mobiel gebruik.

## Bekende aandachtspunten

- Lokale HTML-bestanden openen op iPhone via de Bestanden-app is onbetrouwbaar voor interactieve JavaScript-functionaliteit.
- De planner werkt het best wanneer de app gehost wordt via GitHub Pages of een andere statische webhost.
- De app rekent momenteel in stappen van **30 minuten** voor beschikbaarheid en zoekvensters.

## Toekomstige verbeteringen

Mogelijke uitbreidingen:

- meerdere recepten of deegschema’s;
- export naar agenda;
- notificaties of herinneringen;
- voorkeuren opslaan;
- PWA-ondersteuning voor offline gebruik;
- apart instelbare perfecte duur per stap.

## Licentie

Kies hier zelf een licentie voor, bijvoorbeeld MIT:

```text
MIT License
```

Als je de app openbaar deelt en anderen hem wilt laten hergebruiken, is een MIT-licentie meestal een goede eenvoudige keuze.
