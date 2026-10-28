# Techniek 06 — Climatics instellen

Module: Techniek (Techniekbasis) · Les 6 van 7 · Bron: ACS Academy (Climatics cursus), gelezen 27-10-2026 · Status: samenvatting in eigen woorden (zonder praktijkopdracht, zelftoets en toets)
Voorkennis: Techniek 04, 05
Volgende les: Techniek 07 — Modbus en BACnet

Trefwoorden: Climatics, Schematics, P&ID, control components, opwekking-distributie-afgifte, device, adres, datapunt, herkomst unaddressed, u-OS, KS-01, tags Haystack, deadman, no-change, grenswaarde, alert definitions, stooklijn, parallelverschuiving, configuratiewaarschuwing
Beantwoordt vragen als: Wat is het verschil tussen device, adres en datapunt? Hoe maak ik een installatie in Climatics? Waarom tags? Welke bewaking zet ik waar? Hoe stel ik een stooklijn in en beoordeel ik hem? Waarom draait een component niet (runnable)?

---

- Werkwijze: Schematics → leeg canvas → principeschema (P&ID) opbouwen. Begin altijd met Control components; andere palet-groepen (Equipments, Structure, Values, Energy management, Miscellaneous) zijn aanvulling op de weergave. Eigen regelcomponenten bouwen valt buiten deze cursus.
- Opbouw altijd opwekking → distributie → afgifte, gekoppeld in "Edit control component" (Receives heat demand from, Heating water supplied by). Ontbrekende koppeling = configuratiewaarschuwing, component draait niet (een gat in de configuratie, geen storing in het gebouw).
- Adres vs. device vs. datapunt: adres = plek in hardware (kanaal, register, BACnet-object); device = apparaat zoals Climatics het kent (Administrator → Devices, met IO-interval, op koffer 10 s); datapunt = object met naam, procescode, eenheid en herkomst (Administrator → Datapoints). Herkomsten: physical, external, control_variable, unaddressed (nooit een waarde). Adres zonder datapunt = signaal waar niemand iets mee doet.
- u-OS-station (Weidmüller UC20-WL2000-AC, op koffer "KS-01"): adressen verschijnen vanzelf per I/O-kaart (AI 0, AO 0, RTD 0 …, float64). Moduleopbouw bepaalt de adressenlijst: kaart bijplaatsen of verwisselen verschuift adressen zonder storing. Derden-apparatuur via Modbus/BACnet: adressen zelf aanmaken. Interne doorschrijving ("write to this address from / write this address to") is niet zichtbaar in het schema.
- Tags volgens Haystack (bijv. ['zone','air','temp']): voorwaarde voor schaalbare analyses. Ongetagd = blinde vlek.
- Bewaking: grenswaarde (exceedance), deadman (geen nieuwe waarde, bewaakt verbinding), no-change (waarde dood maar plausibel, verraderlijker). Device-niveau deadman geeft één melding in plaats van één per punt. Alarmdefinities onder Administrator → Alert definitions. Werk alle configuratiewaarschuwingen weg vóór oplevering.
- Stooklijn: twee punten (bijv. −10 °C en +20 °C) plus parallelverschuiving. Te steil = te warm, kranen dicht, hoge retour, slecht rendement; te vlak = koude ruimten. Controleer eerst de buitenvoeler (zon) tegen een weerstation en beoordeel over een dag, niet over een uur. Kloktijden, setpoints en modes: aparte module nog uit te werken.

## Zie ook
Techniek 07 (bus-adressen), Veldwerk 02 (opleverbaarheid), Veldwerk 03 (dode waarden).
