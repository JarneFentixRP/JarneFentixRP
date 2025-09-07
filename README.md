# FiveM Politie Wetboek – GitHub‑ready repository

Hieronder staat een complete mappenstructuur met alle benodigde bestanden (in Markdown) om een politie‑wetboek voor een FiveM RP‑server te beheren op **GitHub**. Kopieer de structuur 1‑op‑1 naar een nieuwe repository. Je kunt vervolgens GitHub Pages (of MkDocs/Docsify) gebruiken om de documentatie als website te publiceren.

---

## 📁 Repository-structuur

```
politie-wetboek/
├─ README.md
├─ LICENSE
├─ CONTRIBUTING.md
├─ docs/
│  ├─ index.md
│  ├─ beleid-en-procedures.md
│  ├─ wetboek.md
│  ├─ boetecatalogus.md
│  ├─ radio-codes.md
│  ├─ sjablonen/
│  │  ├─ arrestatieformulier.md
│  │  └─ inbeslagnameformulier.md
│  └─ changelog.md
└─ .github/
   ├─ ISSUE_TEMPLATE/
   │  ├─ bug_report.md
   │  └─ law_change_request.md
   └─ pull_request_template.md
```

---

## 📄 `README.md`

````md
# Politie Wetboek (FiveM RP)

Een open source wetboek en procedureset voor politie/justitie binnen een FiveM roleplay server. Beheer wijzigingen via Pull Requests, bespreek voorstellen via Issues en publiceer de docs met GitHub Pages.

## Snelstart
1. **Fork** of **Clone** deze repo.
2. Bewerk de bestanden in `docs/` om de wetten, boetes en procedures aan te passen aan jouw server.
3. Activeer **GitHub Pages**: *Settings → Pages → Build and deployment → Deploy from branch* en kies `main` en map `docs/`.
4. Deel de URL met je team; deze leest live mee.

## Integratie met FiveM
- Voeg in je server een `/wetboek` chatcommand toe dat de GitHub Pages URL opent in NUI of chat (zie voorbeelden onderaan in dit bestand).
- Exporteer de **boetecatalogus** naar JSON/CSV voor scripts die automatisch boetes/jail-tijden invullen.

## Mappen
- `docs/wetboek.md` — materieel recht (strafrecht, verkeersrecht, orde).
- `docs/beleid-en-procedures.md` — professioneel gedrag, use-of-force, escalatie.
- `docs/boetecatalogus.md` — tarieven en strafmaten.
- `docs/radio-codes.md` — 10-codes/sein-codes.
- `docs/sjablonen/` — formulieren voor arrestaties en inbeslagname.

## Voorbeeld: eenvoudig chatcommand (Lua)
```lua
RegisterCommand('wetboek', function(src)
    TriggerClientEvent('chat:addMessage', src, {
        args = {'WETBOEK', 'Open: https://<jouw-github-gebruikersnaam>.github.io/politie-wetboek/'}
    })
end)
````

## Licentie

MIT — zie `LICENSE`.

````

---

## 📄 `LICENSE` (MIT)

```txt
MIT License

Copyright (c) 2025 <Jouw Naam>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
````

---

## 📄 `CONTRIBUTING.md`

```md
# Bijdragen

Bedankt voor je hulp! Zo houden we het wetboek consistent en fair:

## Richtlijnen
- 1 onderwerp per Pull Request.
- Voeg onderbouwing toe (realistische RP, balans, jurisprudentie in-lore).
- Pas ook de `boetecatalogus.md` aan als straffen wijzigen.
- Update `docs/changelog.md` met datum en korte samenvatting.

## Stijl
- Korte, duidelijke artikelen: *"Doen/Verbod → Strafmaat"*.
- Gebruik eenduidige termen (verdachte, agent, OVD, Officier van Justitie).

## Reviewproces
1. Issue aanmaken (sjabloon: *Law change request*).
2. PR openen en link naar issue.
3. Minimaal 2 goedkeuringen van staf (bijv. Hoofdcommissaris + OVJ).
```

---

## 📄 `docs/index.md`

```md
---
title: Politie Wetboek
---

Welkom bij het officiële **Politie Wetboek** van onze FiveM roleplay server. Gebruik het menu/links hieronder:

- [Wetboek (Materieel recht)](./wetboek.md)
- [Beleid & Procedures](./beleid-en-procedures.md)
- [Boetecatalogus](./boetecatalogus.md)
- [Radio Codes](./radio-codes.md)
- [Sjablonen](./sjablonen/arrestatieformulier.md)
- [Changelog](./changelog.md)
```

---

## 📄 `docs/beleid-en-procedures.md`

```md
# Beleid & Procedures

## 1. Gedragscode voor Agenten
- Professionaliteit, geen metagaming/powergaming.
- Bodycam verplicht tijdens dienst (indien server dit ondersteunt).
- Corruptie RP alleen met schriftelijke toestemming staf.

## 2. Escalatie & Use-of-Force
1. **Aanwezigheid** → 2. **Mondeling bevel** → 3. **Fysiek geleiden** → 4. **Niet-dodelijke middelen** (taser/pepperspray/baton) → 5. **Vuurwapen** als *ultimum remedium* bij onmiddellijke dreiging.
- **Waarschuwingsschot** indien mogelijk en veilig.
- **Schieten op voertuig** alleen bij levensgevaar.

## 3. Staandehouding & Fouillering
- **Staandehouding** bij redelijke verdenking (OVT/feit uit wetboek).
- **Fouillering**: oppervlakkig bij veiligheidsrisico; volledig na arrestatie of met toestemming OVJ/OVD.

## 4. Aanhouding & Rechten
- Noem reden van aanhouding.
- Mededelen van rechten (zwijgrecht, recht op advocaat indien aanwezig).
- Max. aanhoudingstijd pre-voorgeleiding: **45 min** (serverconfig aanpasbaar).

## 5. Voertuigprocedures
- Achtervolgingsmatrix: licht (1), normaal (2), hoog (3); toestemming OVD voor (3).
- PIT/manoeuvres alleen door getrainde units en bij vrij verkeer.
- Sleep/inbeslagname per wetboek-artikelen en formulieren.

## 6. Bewijs & Dossiervorming
- Screenshots/bodycam-tijdstempels.
- Bewijslijst opnemen in arrestatieformulier.

## 7. Rangstructuur (voorbeeld)
- **Agent** → **Hoofdagent** → **Brigadier** → **Inspecteur** → **Hoofdinspecteur** → **Commissaris** → **Hoofdcommissaris**.
- **OVD** (Officier van Dienst) en **OVJ** (Officier van Justitie) met specifieke bevoegdheden.
```

---

## 📄 `docs/wetboek.md`

```md
# Wetboek (Materieel Recht)

> **Let op:** Dit is een RP-wetboek geïnspireerd op NL/BE-concepten, vereenvoudigd voor gameplay. Pas strafmaten aan je server-economie aan.

## Hoofdstuk 1 — Algemene Bepalingen
**Art. 1.1** Begripsbepalingen: verdachte, agent, OVD, OVJ, openbaar terrein, verboden wapen.

**Art. 1.2** Medeplegen, uitlokking, poging: strafbaar volgens 2/3 van hoofdfeit.

**Art. 1.3** Recidive: +25% strafmaat (fines/jail) binnen 7 dagen RP.

**Art. 1.4** Weigerachtigheid/Fail-RP: kan leiden tot admin‑maatregelen.

## Hoofdstuk 2 — Misdrijven tegen Persoon & Eigendom
**Art. 2.1** Mishandeling: boete $2.500 | 10 min cel.

**Art. 2.2** Zware mishandeling (taser/vuurwapen/slagwapen): $5.000 | 20 min.

**Art. 2.3** Poging tot doodslag: $12.500 | 35 min.

**Art. 2.4** Doodslag/Moord (serverbesluit): $25.000 | 60 min | wapeninname.

**Art. 2.5** Diefstal (≤$10k): $3.000 | 10 min.

**Art. 2.6** Zware diefstal/overval/ATM/juwelier: $10.000 | 30 min | inbeslagname voertuig.

**Art. 2.7** Huisvredebreuk/inbraak: $7.500 | 20 min.

**Art. 2.8** Afpersing: $8.000 | 25 min.

**Art. 2.9** Vandalisme (publieke eigendom): $4.000 | 10 min | schadevergoeding RP.

## Hoofdstuk 3 — Openbare Orde & Veiligheid
**Art. 3.1** Wapenbezit verboden categorie (SMG/AR): $12.500 | 35 min | inname.

**Art. 3.2** Illegale munitie/explosieven: $15.000 | 40 min | inname.

**Art. 3.3** Maskerplicht bij misdrijf (vermomming bij delict): $2.500 | 10 min.

**Art. 3.4** Openbare dronkenschap/wanordelijk gedrag: $1.500 | 5 min.

**Art. 3.5** Vluchten voor politie (voet): $3.000 | 10 min.

**Art. 3.6** Vluchten met voertuig: $7.500 | 20 min | rijontzegging 24u RP.

**Art. 3.7** Heling bezit (illegale goederen): $5.000 | 15 min | inname.

**Art. 3.8** Belemmeren ambtsdrager (hinderen, weigeren identiteit): $2.500 | 10 min.

**Art. 3.9** Valse aangifte: $3.000 | 10 min.

## Hoofdstuk 4 — Verkeersrecht
**Art. 4.1** Snelheidsovertreding licht (≤20 km/u): $600.

**Art. 4.2** Snelheidsovertreding zwaar (>20–60): $1.500 | 5 min.

**Art. 4.3** Roekeloos rijgedrag (door rood, te dicht op): $2.500 | 10 min.

**Art. 4.4** Rijden zonder rijbewijs/geschorst: $3.000 | 10 min | voertuig inbeslagname.

**Art. 4.5** Onverzekerd voertuig: $1.500 | platen ingehouden 24u RP.

**Art. 4.6** Alcohol/drogen achter het stuur: $5.000 | 15 min | ontzegging 48u RP.

**Art. 4.7** Vluchten na ongeval: $3.000 | 10 min.

## Hoofdstuk 5 — Procedurele Delicten
**Art. 5.1** Niet voldoen aan bevel/vordering: $1.500 | 5 min.

**Art. 5.2** Beletten aanhouding/ontsnapping helpen: $4.000 | 15 min.

**Art. 5.3** Bewijsvernietiging/looting crime scene: $3.500 | 10 min.

**Art. 5.4** Omkoping ambtenaar: $7.500 | 20 min.

## Hoofdstuk 6 — Inbeslagname & Civiel
**Art. 6.1** Inbeslagname verboden goederen: altijd; afgifte aan bewijsopslag.

**Art. 6.2** Voertuiginbeslagname: bij art. 2.6, 3.6, 4.4, 4.6.

**Art. 6.3** Teruggave: via formulier, na beoordeling OVD/OVJ.

## Slotbepaling
**Art. 7.1** Staff override bij uitzonderlijke situaties (misbruik → sanctie).
```

---

## 📄 `docs/boetecatalogus.md`

```md
# Boetecatalogus

> **Aanpassen aan server-economie:** pas bedragen/straftijden aan gemiddelde inkomen/uur.

| Code | Overtreding/Delict | Boete | Cel | Extra |
|---|---|---:|---:|---|
| 2.1 | Mishandeling | $2.500 | 10 min |  |
| 2.2 | Zware mishandeling | $5.000 | 20 min |  |
| 2.3 | Poging doodslag | $12.500 | 35 min |  |
| 2.4 | Doodslag/Moord | $25.000 | 60 min | Wapeninname |
| 2.5 | Diefstal | $3.000 | 10 min |  |
| 2.6 | Zware diefstal/overval | $10.000 | 30 min | Voertuig inbeslagname |
| 2.7 | Inbraak | $7.500 | 20 min |  |
| 2.8 | Afpersing | $8.000 | 25 min |  |
| 2.9 | Vandalisme | $4.000 | 10 min | Schadevergoeding |
| 3.1 | Verboden wapenbezit | $12.500 | 35 min | Inname |
| 3.2 | Explosieven/munitie | $15.000 | 40 min | Inname |
| 3.3 | Vermomming bij delict | $2.500 | 10 min |  |
| 3.4 | Openbare dronkenschap | $1.500 | 5 min |  |
| 3.5 | Vluchten te voet | $3.000 | 10 min |  |
| 3.6 | Vluchten voertuig | $7.500 | 20 min | Rijontzegging 24u RP |
| 3.7 | Heling bezit | $5.000 | 15 min | Inname |
| 3.8 | Belemmeren ambt | $2.500 | 10 min |  |
| 3.9 | Valse aangifte | $3.000 | 10 min |  |
| 4.1 | Snelheid ≤20 | $600 | – |  |
| 4.2 | Snelheid >20–60 | $1.500 | 5 min |  |
| 4.3 | Roekeloos | $2.500 | 10 min |  |
| 4.4 | Zonder rijbewijs | $3.000 | 10 min | Inbeslagname |
| 4.5 | Onverzekerd | $1.500 | – | Platen inhouden |
| 4.6 | DUI/DWI | $5.000 | 15 min | Ontzegging 48u RP |
| 4.7 | Doorrijden na ongeval | $3.000 | 10 min |  |
| 5.1 | Niet voldoen bevel | $1.500 | 5 min |  |
| 5.2 | Hulp bij ontsnapping | $4.000 | 15 min |  |
| 5.3 | Bewijsvernietiging | $3.500 | 10 min |  |
| 5.4 | Omkoping | $7.500 | 20 min |  |
```

---

## 📄 `docs/radio-codes.md`

```md
# Radio Codes

- **10-4** Begrepen
- **10-7** Buiten dienst / Off duty
- **10-8** In dienst / On duty
- **10-20** Locatie
- **10-22** Negeren / Afbreken
- **10-23** Ter plaatse
- **10-32** Gewapend persoon
- **10-41** Start dienst
- **10-42** Einde dienst
- **Code 0** Officier in levensgevaar
- **Code 2/3** Spoed zonder/met sirene
```

---

## 📄 `docs/sjablonen/arrestatieformulier.md`

```md
# Arrestatieformulier

**Naam verdachte:**  
**Datum/tijd (RP):**  
**Locatie:**  
**Artikelen:**  
**Bewijs (bodycam, getuigen, items):**  
**Rechten medegedeeld (ja/nee):**  
**Opmerkingen:**  
**Naam agent(en):**  
```

---

## 📄 `docs/sjablonen/inbeslagnameformulier.md`

```md
# Inbeslagnameformulier

**Naam betrokkene:**  
**Datum/tijd (RP):**  
**Item/voertuig:**  
**Reden/Artikel:**  
**Bewijs/Foto's:**  
**Opslag/Referentie:**  
**Beoordeling OVD/OVJ:**  
```

---

## 📄 `.github/ISSUE_TEMPLATE/bug_report.md`

```md
---
name: "Foutmelding"
about: Meld een fout in de documentatie of inconsistentie
labels: bug
---

**Omschrijving**

**Waar** (bestand/regelnr)

**Voorstel fix**
```

---

## 📄 `.github/ISSUE_TEMPLATE/law_change_request.md`

```md
---
name: "Voorstel wetswijziging"
about: Vraagt wijziging van wet/boete/procedure
labels: enhancement, law
---

**Welke bepaling** (bijv. Art. 3.6)

**Huidige tekst**

**Voorgestelde tekst**

**Motivatie/Impact op gameplay**
```

---

## 📄 `.github/pull_request_template.md`

```md
### Samenvatting

### Wijzigingen
- [ ] Wetboek aangepast
- [ ] Boetecatalogus bijgewerkt
- [ ] Procedures geüpdatet
- [ ] Changelog ingevuld

### Bewijs/Overleg
Link naar issue(s): #
```

---

## 📄 `docs/changelog.md`

```md
# Changelog

- **2025-09-07**: Eerste publieke versie van het Politie Wetboek.
```
