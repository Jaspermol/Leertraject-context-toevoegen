# Praktijk 1–5 — Oefenopstelling (demokoffer) en oefeningen

Module: Praktijk · 5 blokken · Bron: ACS Academy (Climatics cursus), gelezen 27-10-2026 · Status: overzicht van opzet en opdrachten. De uitwerking van de theorie staat in de Techniek- en Veldwerk-lessen; dit document zegt welke vaardigheid waar geoefend wordt.

Trefwoorden: demokoffer, oefenlocatie, praktijkdag, opdrachtvolgorde, wat lever je af, logboeknotitie, ingebouwde fouten
Beantwoordt vragen als: Wat oefen ik in welk praktijkblok? Hoe is de demokoffer opgebouwd? Welke fouten bouwt de docent in? Wat moet ik opleveren bij een praktijkopdracht?

---

## De opstelling
- **Demokoffer** met regelaar (Weidmüller u-OS-station KS-01 plus Modbus-gateway, een SmartBase), voeler, drukknop, lamp en klemmenlijst. Aan een Modbus-gateway hangt een apparaat met registerlijst.
- **Oefenlocatie in Climatics**: één ingerichte locatie om te lezen en per cursist een lege locatie om zelf op te bouwen. De koffer wordt in praktijk 4 aan die locatie gekoppeld.
- Gereedschap: multimeter, stroomtang, duspol, LOTO-set, momentschroevendraaier, losse 120 Ω-weerstand.

## Overzicht

| Blok | Duur | Thema | Bouwt voort op | Wat je oefent |
|---|---|---|---|---|
| Praktijk 1 | ca. 3 u (45+45+60+30 min) | Meten, veilig werken, schema's lezen | Techniek 01, 02, 03 | Typeplaatje → stroom → meten (duspol bekend-onbekend-bekend, Ω-voeler, stroomtang); vijf veiligheidsregels op de koffer; ventilatorgroep van boven naar beneden lezen met één door de docent onderbroken voorwaarde |
| Praktijk 2 | ca. 3 u | Signalen, regelen en de bus | Techniek 04, 07 | Regelkring natekenen (W/X/Y/Z), voeler en actor aansluiten, regeling verstoren (P-term hoger/lager); afsluitweerstanden meten (60 Ω, met derde 120 Ω ≈ 40 Ω, met één ≈ 120 Ω); rustspanning; drie Modbus-registers uitlezen, bewust één register ernaast lezen |
| Praktijk 3 | ca. 3 u | De installatie in Climatics | Techniek 05, 06 | Installatie herkennen (zones, HT/LT, distributiegroep, AHU-secties, cascade; mengt of smoort de groep?); zelf opbouwen in Schematics (opwekking-distributie-afgifte), datapunten, tags, kloktijden, bewaking, stooklijn; drie aanvoertemperaturen uit eigen stooklijn bij −10, 0, +10 °C |
| Praktijk 4 | ca. 6,5 u (120 min ochtend, 60 min pauze/nabespreken, 180 min middag, 30 min overdracht) | Aansluiten en in bedrijf stellen | Veldwerk 01, 02 | Labelen, aansluiten, momentschroevendraaier, spanningsloze controles, in stappen onder spanning; testformulier uit klemmenlijst met waarden i.p.v. vinkjes; twee gelijksoortige voelers één voor één bewegen; regelkring in vijf stappen; waarschuwingen wegwerken; overdracht in vijf zinnen. Docent zet één ader op verkeerde klem en later een bedradingsfout |
| Praktijk 5 | ca. 3,5 u | Storingzoeken | Veldwerk 03 | Vijf ingebouwde fouten opsporen: verwisseld paar, schaal-/eenheidsfout, verkeerd contacttype, onderbroken ader naar voeler, klepaandrijving los op de as; vier cases in tweetallen; één storing als logboeknotitie |

## Terugkerende werkwijze
- **Per klacht eerst de vraag**: welke waarde is verdacht en waarmee vergelijk ik hem?
- **Per fout aantonen** in welke schakel van de keten hij zit, met twee waarnemingen.
- **Waarden noteren, niet "ok"**: testformulier met gemeten waarden.
- **Opruimen = terugzetten naar de startsituatie** (koffer en oefenlocatie), meters en LOTO-set opbergen. Bewaking die je in praktijk 2 inricht, gebruik je in praktijk 4 weer.
- **Af te leveren** staat per blok vast (meetbladen, tekening kring, ingevulde wel/niet-tabel, labelblad, testformulier, logboeknotitie).
- **Aanwijzing**: werk in geopende verdeelinrichting onder spanning valt buiten VOP; docent of vakbekwaam persoon doet dat deel.

## Zie ook
Techniek 01–07, Veldwerk 01–03.
