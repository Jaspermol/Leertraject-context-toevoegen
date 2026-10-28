# Techniek 01 — Algemene kennis elektrotechniek

Module: Techniek (Techniekbasis) · Les 1 van 7 · Bron: ACS Academy (Climatics cursus), gelezen 27-10-2026 · Status: samenvatting in eigen woorden (zonder praktijkopdracht, zelftoets en toets)
Voorkennis: geen (begint bij nul)
Volgende les: Techniek 02 — NEN 3140 en de VOP-aanwijzing

Trefwoorden: Ohm, vermogen, ampère, cos φ, driefasig, 230 V, 400 V, 24 V AC/DC, trafo, schakelende voeding, typeplaatje, automaat B/C/D, aardlek type A/B, PE, IP-code, aderkleuren, doorsnede, spanningsval, duspol, multimeter, CAT, True RMS
Beantwoordt vragen als: Hoeveel stroom trekt een motor/pomp? Hoeveel klepmotoren passen op een voeding? Waarom C-automaat bij een motor? Welke aardlek bij een frequentieregelaar? Waarom meet ik 400 V tussen twee fasen? Duspol of multimeter? Hoe lees ik een voedingstypeplaatje?

---

**Basisrekenen.** Wet van Ohm U = I·R. Vermogen P = U·I = I²·R. Energie = vermogen × tijd (2 kW gedurende 4 uur = 8 kWh).

**Van watt naar ampère** (typeplaatje → kabel, automaat, voeding kiezen):
- Eenfasig: I = P / U.
- Driefasig: I = P / (√3 · U · cos φ).
- Voorbeelden: klepmotor 5 W / 24 V = 0,21 A; pomp 0,55 kW / 230 V = 2,4 A; ventilator 1,5 kW / 400 V / cos φ 0,85 = 2,5 A.
- Hoeveel verbruikers op een trafo: trafo 24 V × 1,3 A ≈ 31 W, gedeeld door 5 W = 6 klepmotoren. Houd ca. 20 % marge voor inschakelstroom. Tel alles op wat op de kring hangt (relais, regelaar, lampen). Boven 80 % belasting: zwaardere voeding kiezen.

**Wisselspanning.** 50 Hz, 230 V is RMS (piek ruim 325 V). Tussen fasen 400 V = 230 × √3 (de fasen liggen 120° uit elkaar, 6,7 ms per stap). Verdeel eenfasige verbruikers over de drie fasen. Draairichting van een motor volgt de fasevolgorde: controleer die bij elke pomp en ventilator vóór belasting. Frequentieregelaars brengen cos φ meestal rond 0,95.

**Spanningen in een regelkast:** 400 V AC (motoren), 230 V AC (kastvoeding, kleine pompen), 24 V AC (oudere klepmotoren, klassieke stuurstroom), 24 V DC (moderne regeltechniek: regelaars, I/O, voelers). 24 V is veilige lage spanning (SELV/PELV).

**Transformator.** Twee wikkelingen op één kern, alleen op wisselspanning, scheidt galvanisch, vermogen blijft gelijk (halve spanning = dubbele stroom). 100 VA bij 24 V ≈ 4 A.

**Schakelende voeding.** Gelijkrichten → hakken → hoogfrequent transformeren → gelijkrichten en regelen. Uitgang blijft stabiel tot het maximum, daarna begrenzen of afschakelen. Typeplaatje: Input 100–240 V ~, Output 24 V ⎓ 5 A = 120 W. Front: instelpotmeter 22–28 V (spanningsval compenseren), leds (geel = >90 % belast), potentiaalvrij meldcontact 13/14 (op een digitale ingang leggen).

**Valkuilen 24 V:** polariteit bij DC; gemeenschappelijke GND voor 0–10 V-signalen (GND ≠ aarde/PE, niet op eigen initiatief koppelen); spanningsval telt zwaar bij lage spanning (meet aan het kabeluiteinde); multimeter op V⎓ voor DC.

**Beveiligen.**
- Automaatkarakteristiek: B (3–5 × In) verlichting/wcd/regelkringen; C (5–10 × In) motoren, pompen, trafo's, LED-drivers; D (10–20 × In) zware aanloop.
- Aardlek 30 mA = persoonsbeveiliging, 300 mA = brandbeveiliging. Achter frequentieregelaars hoort type B (type A "verblindt" door gelijkstroomcomponent).
- Aarde (PE) is vluchtroute voor foutstroom, geen retour. Klasse I (geaard), klasse II (dubbel geïsoleerd), SELV/PELV. IP54 technische ruimte, IP65 dak/nat.

**Kabels.** Bruin/zwart/grijs = fasen, blauw = nul, geel-groen uitsluitend aarde. Vuistregel doorsnede: 1,5 mm² tot ca. 16 A, 2,5 mm² ca. 20 A, 4 mm² ca. 25 A (NEN 1010 voor de echte tabellen). Spanningsval: max 3 % licht, 5 % kracht. ΔU driefasig = √3·ρ·L·I/A, eenfasig 2·ρ·L·I/A, ρ koper = 0,0175 Ω·mm²/m.

**Meten.** Duspol (tweepolig) voor 230/400 V en voor spanningsloosheid vaststellen, niet de multimeter (schijnspanning). Regel "bekend – onbekend – bekend". Multimeter: rode snoer in V Ω voor spanning/weerstand, alleen in mA/10 A-bus voor stroom (gezekerd). Drie klassieke fouten: weerstand meten onder spanning, stroom meten met snoeren in A-bus over een spanning, verkeerde meetcategorie (minimaal CAT III 600 V in verdeling, CAT IV bij hoofdverdeling). In kasten met frequentieregelaars: True RMS-meter.

## Zie ook
Techniek 02 (veiligheid), Techniek 03 (voedingsblad in schema), Veldwerk 01 (aandraaimoment, meten bij aansluiten).
