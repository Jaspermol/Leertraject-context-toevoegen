# ACS Academy — Kennisbank M&R (index, begin hier)

Bron: interne onboarding "Climatics cursus" van ACS (acs-academy.nl), een partner van Saever. Samenvattingen in eigen woorden, voor intern gebruik; niet doorgeven of publiceren zonder toestemming van ACS. Laatst bijgewerkt: 27-10-2026. Momentopname van de site: controleer bij twijfel de bron.

## Hoe je deze kennisbank gebruikt
1. **Zoek eerst in dit overzicht** welke les over het onderwerp gaat (tabel "Vraag → les" hieronder).
2. Open dan de les. Elke les heeft dezelfde opbouw: kopregel met module/voorkennis → **Trefwoorden** → **Beantwoordt vragen als** → inhoud → **Zie ook**.
3. Voor snel opzoeken zonder de les te lezen: `begrippen.md` (A–Z), `formules-en-vuistregels.md` (alle getallen en rekenregels), `diagnose-symptomen.md` ("ik zie X, wat is het?").
4. Bij een vraag over een concrete installatie: combineer met de project-documenten over GACS en EPBD en de Saever-context (ACS = software/Climatics, Weidmüller = hardware/UR20-u-OS, Saever = projectregie en klantrelatie).

## Cursusoverzicht

| Module | Les | Bestand | Kernonderwerp |
|---|---|---|---|
| Techniek | 01 | `techniek-01-algemene-kennis-elektrotechniek.md` | Ohm, vermogen, watt→ampère, 230/400 V, 24 V AC/DC, trafo, voeding, beveiligen, kabels, meten |
| Techniek | 02 | `techniek-02-nen3140-en-vop-aanwijzing.md` | NEN 3140, IV/WV/VP/VOP, wat mag een VOP, vijf veiligheidsregels, vlamboog |
| Techniek | 03 | `techniek-03-elektrische-schemas-lezen.md` | Hoofd-/stuurstroom, kenletters, relais, motorgroep, I/O-bladen, procescode |
| Techniek | 04 | `techniek-04-basis-regeltechniek.md` | BMS/EMS/SRI, W-X-Y-Z, PID, band, signalen, klepaandrijving, UR20, omrekenen |
| Techniek | 05 | `techniek-05-hvac-installatie.md` | Afgifte HT/LT, mengen/smoren, ΔT, koelen, bron, ventilatie, luchtbehandelingskast |
| Techniek | 06 | `techniek-06-climatics-instellen.md` | Schematics, device/adres/datapunt, tags, bewaking, stooklijn |
| Techniek | 07 | `techniek-07-modbus-en-bacnet.md` | RS485, afsluitweerstanden, slave-id, registers, BACnet, stille busfouten |
| Veldwerk | 01 | `veldwerk-01-installeren-en-aansluiten.md` | Nieuwe kast vs ombouw, labelen, aandraaimoment, controles, onder spanning |
| Veldwerk | 02 | `veldwerk-02-testen-en-inbedrijfstellen.md` | I/O-test, veiligheidsketen, inregelen, regelkring instellen, oplevering, checklist |
| Veldwerk | 03 | `veldwerk-03-storingzoeken.md` | Keten halveren, voeler-/klep-/busfouten, vier cases, deadman-periode |
| Praktijk | 1–5 | `praktijk-01-05-oefenopstelling.md` | Demokoffer en oefenopdrachten per blok |
| Overzicht | — | `begrippen.md`, `formules-en-vuistregels.md`, `diagnose-symptomen.md` | Doorsnijdende naslag |

## Vraag → les
| Als je vraag gaat over… | Ga naar |
|---|---|
| Stroom, vermogen, kabel/automaat/voeding kiezen, spanningsval | Techniek 01 + formules |
| Duspol, multimeter, meetfouten, CAT | Techniek 01 |
| Mag ik dit als VOP? Veiligheidsregels, LOTO | Techniek 02 |
| Schema lezen, kenletters, relais, motorbeveiliging | Techniek 03 |
| P/I/D, pendelen, band, dode band | Techniek 04 (theorie), Veldwerk 02 (instellen) |
| Signaaltype, 2–10 V, 4–20 mA, omrekenen, klepklemmen, driepunt | Techniek 04 |
| Welke UR20-kaart voor welk signaal | Techniek 04 |
| HT/LT, warmtepomp-eisen, ΔT, mengen vs smoren, cascade | Techniek 05 |
| Luchtbehandelingskast, vorstbeveiliging, WTW, ventilatiesystemen | Techniek 05 (+ Veldwerk 02 beproeven) |
| Koelen, vrije koeling, condens, bron/WKO | Techniek 05 |
| Climatics: schema opbouwen, device/adres/datapunt, tags | Techniek 06 |
| Alarmtypes: grenswaarde, deadman, no-change | Techniek 06 (+ Veldwerk 03 deadman-periode) |
| Stooklijn instellen en beoordelen | Techniek 06 |
| Modbus/RS485, afsluitweerstand, slave-id, registers, schaalfactor | Techniek 07 |
| BACnet-objecten, COV vs polling | Techniek 07 |
| Ombouw bestaande kast, voorbereiding, klemmen aandraaien | Veldwerk 01 |
| Hoe test ik een punt? Wat leg ik vast? Wanneer opleverbaar? Nazorg? | Veldwerk 02 |
| Iets werkt niet of waarde klopt niet | Veldwerk 03 + `diagnose-symptomen.md` |
| Wat oefen ik waar, wat levert elk praktijkblok op | Praktijk |

## Afspraken voor het toevoegen van nieuwe lessen
Zodat de kennisbank doorzoekbaar blijft naarmate er lessen bijkomen:
1. **Eén bestand per les**, naam `<module>-<nr>-<korte-naam>.md` (kleine letters, koppeltekens).
2. **Vaste opbouw**: titel · kopregel (module, lesnummer, bron, datum gelezen, status) · Voorkennis · Volgende les · **Trefwoorden** · **Beantwoordt vragen als** · inhoud met `##`-koppen · **Zie ook**.
3. **Zoektermen letterlijk opnemen**: de Nederlandse term én het Climatics-/Engelse woord (bijv. "deadman", "linear conversion", "holding register").
4. **Getallen, formules en tabellen niet weglaten**: zet ze bovendien in `formules-en-vuistregels.md`.
5. **Nieuwe begrippen** toevoegen aan `begrippen.md` met verwijzing naar de les.
6. **Nieuwe symptomen/oorzaken** toevoegen aan `diagnose-symptomen.md`.
7. **Index bijwerken**: rij in cursusoverzicht en zo nodig in "Vraag → les".
8. **Zelftoetsen/toetsen niet opnemen**, maar redenaties daaruit die inhoudelijk iets toevoegen wel in de les zelf.

## Status van verwerking
- Verwerkt (samenvatting): Techniek 01–07, Veldwerk 01–03, Praktijk 1–5 (op niveau van opzet en opdrachten).
- Nog niet verwerkt: nieuwe lessen die ACS toevoegt (o.a. aangekondigd in de cursus: kloktijden/modes/setpoints-module, aparte les over storingzoeken aan draaiende installaties, vervolgcursus eigen regelcomponenten bouwen).
- Niet opgenomen: afbeeldingen, schema's en interactieve simulaties van de site; de oefeningen-, zelftoets- en toetsvragen.
