# VolksRekening 🗳️

**Politieke Verantwoordelijkheidsmonitor — Nederland**

> Wie heeft het vertrouwen van het volk verdiend — en wie heeft het verbroken?

VolksRekening houdt bij wat politici beloven en wat ze er daadwerkelijk van nakomen. Op basis van objectieve criteria zoals beleidsresultaten, rechterlijke uitspraken, motiegedrag en volksimpact krijgt elke politicus een score van 0 tot 100. Van Volksheld tot Landverrader. Transparant, onderbouwd, en zonder politieke voorkeur.

---

## 🔍 Wat doet VolksRekening?

- **Belofte-tracking** — verkiezingsbeloften en regeerakkoorden vergeleken met wat er daadwerkelijk is uitgevoerd
- **Volksimpact score** — was het beleid positief voor gewone burgers, of begunstigde het multinationals en vermogensbezitters?
- **Vier scorelagen** die de gebruiker zelf aan/uit kan zetten:
  - ⚖️ **Basis** — objectieve beloften en beleidsresultaten (altijd actief)
  - 🔵 **Internationaal Recht** — naleving van rechterlijke uitspraken en internationaal humanitair recht
  - 🟢 **Moties** — ingediende moties en stemgedrag op volksbelang-gerelateerde moties, gebaseerd op officiële Handelingen Tweede Kamer
  - 🟠 **Volksgevoel** — aansluiting bij meerderheidsoordeel bevolking op basis van peilingen (expliciet gelabeld als subjectief)
- **Verdictschaal** van Volksheld (80+) tot Landverrader (0–29), gebaseerd op berekende scores
- **Volledige methodologiepagina** ingebouwd in de applicatie

---

## 👥 Politici in de huidige dataset

| Politicus | Partij | Rol |
|---|---|---|
| Mark Rutte | VVD | Minister-President 2010–2023 |
| Jesse Klaver | GroenLinks | Fractievoorzitter / Lijsttrekker |
| Rob Jetten | D66 | Minister Klimaat & Energie |
| Frans Timmermans | PvdA/GL-PvdA | Eurocommissaris / Lijsttrekker |
| Hugo de Jonge | CDA | Minister VWS / Volkshuisvesting |
| Pieter Omtzigt | NSC | Kamerlid / Lijsttrekker NSC |
| Geert Wilders | PVV | Partijleider / Informateur 2024 |
| Thierry Baudet | FvD | Partijleider / Oprichter FvD |
| Dilan Yeşilgüz | VVD | Fractievoorzitter / Lijsttrekker VVD |
| Tunahan Kuzu | DENK | Fractievoorzitter / Medeoprichter DENK |

---

## 🚀 Installatie en gebruik

VolksRekening is één zelfstandig HTML-bestand zonder externe afhankelijkheden (behalve Google Fonts). Er is geen build-stap, geen server en geen database nodig.

**Lokaal openen:**
```bash
# Clone de repository
git clone https://github.com/TanoWira/Volksrekening.git

# Open het bestand direct in je browser
open index.html
```

**Live versie:**
👉 [https://tanowira.github.io/Volksrekening](https://tanowira.github.io/Volksrekening)

---

## 🏗️ Technische opbouw

```
index.html          — volledige applicatie (HTML + CSS + JavaScript in één bestand)
README.md           — deze pagina
```

De applicatie is gebouwd met vanilla HTML, CSS en JavaScript. Geen frameworks, geen build tools, geen dependencies. Hierdoor is het:

- Direct te hosten op GitHub Pages, Netlify of elk ander statisch hostingplatform
- Volledig te forken en aan te passen zonder installatiegedoe
- Eenvoudig uitbreidbaar met nieuwe politici of scorelagen

---

## ➕ Een politicus toevoegen

Zoek in `index.html` de `POLITICIANS` array. Voeg een nieuw object toe volgens dit patroon:

```javascript
{
  id: "unieke_id",
  naam: "Volledige Naam",
  partij: "Partijnaam",
  periode: "2020–heden",
  rol: "Functie",
  ihl: {
    id: "ihl",
    belofte: "Omschrijving van de IHL-belofte",
    categorie: "Buitenland/IHL",
    status: "nagekomen",       // nagekomen | gedeeltelijk | gebroken
    impact: "positief",        // positief | gemengd | negatief
    toelichting: "Onderbouwing met verwijzing naar bronnen.",
    jaar: 2024,
    type: "ihl"
  },
  vg: {
    id: "vg",
    belofte: "Positie Israël-Palestina conflict: volksgevoel",
    categorie: "Buitenland/IHL",
    status: "gedeeltelijk",
    impact: "gemengd",
    toelichting: "Onderbouwing.",
    jaar: 2024,
    type: "vg"
  },
  mot: {
    id: "mot",
    belofte: "Motiegedrag volksbelang",
    categorie: "Moties",
    status: "nagekomen",
    impact: "positief",
    toelichting: "Welke moties ingediend en hoe gestemd op volksbelang-moties. Bron: Handelingen Tweede Kamer.",
    jaar: 2024,
    type: "mot"
  },
  beloftes: [
    {
      id: 1,
      belofte: "Omschrijving van de belofte",
      categorie: "Zorg",
      status: "gebroken",
      impact: "negatief",
      toelichting: "Onderbouwde toelichting met bronverwijzing.",
      jaar: 2022
    }
  ]
}
```

**Beschikbare categorieën:**
`Zorg` `Wonen` `Klimaat` `Economie` `Sociaal` `Democratie` `Financiën` `Veiligheid` `Werk` `Migratie` `Onderwijs` `Buitenland/IHL` `Moties`

---

## 📊 Hoe werkt de score?

```
item_score      = (status_score + impact_score) / 2

status_score:   nagekomen = 100 | gedeeltelijk = 50 | gebroken = 0
impact_score:   positief  = 100 | gemengd      = 50 | negatief = 0

eindscore       = gemiddelde van alle actieve item_scores (schaal 0–100)
```

| Score | Verdict |
|---|---|
| 80–100 | ★ VOLKSHELD |
| 60–79 | ✓ BETROUWBAAR |
| 45–59 | ~ WISSELVALLIG |
| 30–44 | ! VERDACHT |
| 0–29 | ✗ LANDVERRADER |

De gebruiker bepaalt zelf welke lagen actief zijn. De basiscore is altijd zichtbaar ter vergelijking.

---

## ⚖️ Juridische positie

VolksRekening is een opinie-analyse platform dat gebruikmaakt van het recht op vrije meningsuiting (artikel 10 EVRM, artikel 7 Grondwet). Alle scores en verdicts zijn **meningen gebaseerd op feiten**, geen feitelijke beweringen op zichzelf.

- Elke claim is onderbouwd met een toelichting
- De scoringsformule is volledig openbaar en reproduceerbaar
- De volksgevoel-laag is expliciet gelabeld als subjectief
- Correcties worden verwerkt bij gegronde bezwaren met bronverwijzing

---

## 🤝 Bijdragen

1. Fork de repository
2. Maak je wijziging met een duidelijke bronvermelding
3. Open een Pull Request met uitleg

**Spelregels:**
- Elke claim herleidbaar naar een publieke bron (Kamerstukken, Handelingen, rechterlijke uitspraken, gevestigde media, CBS/CPB/SCP)
- Geen anonieme aanvallen — onderbouw of het gaat niet in
- De methode is voor alle politieke stromingen gelijk

---

## 📬 Contact

Vragen, correcties of aanvullingen: [contact@volksrekening.nl](mailto:contact@volksrekening.nl)

---

## 📄 Licentie

MIT License — vrij te gebruiken, aan te passen en te verspreiden, mits met bronvermelding.

---

*VolksRekening — Want het volk vergeet niet.*
