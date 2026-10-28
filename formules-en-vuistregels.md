# Formules, getallen en vuistregels (uit de ACS Academy-lessen)

Doel: snel opzoeken zonder de les te lezen. Bij elke regel staat de les waar de uitleg staat. Zie `00-index.md`.

## Elektra (Techniek 01)
- Wet van Ohm: U = I·R · I = U/R · R = U/I
- Vermogen: P = U·I = I²·R
- Energie: kWh = kW × uren (2 kW × 4 h = 8 kWh)
- Stroom eenfasig: I = P / U
- Stroom driefasig: I = P / (√3 · U · cos φ) · P = √3·U·I·cos φ
- Motor: I = P_elektrisch / (√3·U·cos φ), P_elektrisch = P_as / rendement; vergelijk met typeplaatje
- Spanning tussen twee fasen: 230 × √3 ≈ 400 V; RMS 230 V = piek ≈ 325 V; periode 20 ms, fasen 6,7 ms uit elkaar
- Voorbeelden: 5 W / 24 V = 0,21 A · 2 W / 24 V = 0,08 A · 0,55 kW / 230 V = 2,4 A · 1,5 kW / 400 V / cos φ 0,85 = 2,5 A
- Trafo/voeding: P = U × I (24 V × 1,3 A ≈ 31 W; 24 V × 5 A = 120 W). Aantal verbruikers = vermogen / vermogen per verbruiker. Marge inschakelstroom ca. 20 %; boven 80 % belasting zwaardere voeding kiezen. Trafo: 100 VA bij 24 V ≈ 4 A.
- Spanningsval: driefasig ΔU = √3·ρ·L·I/A · eenfasig ΔU = 2·ρ·L·I/A · ρ koper = 0,0175 Ω·mm²/m · max 3 % licht, 5 % kracht
- Doorsnede installatiedraad in buis (vuistregel): 1,5 mm² ≈ 16 A · 2,5 mm² ≈ 20 A · 4 mm² ≈ 25 A (NEN 1010 voor echte waarden)
- Automaatkarakteristiek: B 3–5 × In · C 5–10 × In · D 10–20 × In
- Aardlek: 30 mA persoon · 300 mA brand · type B achter frequentieregelaar
- Aandraaimoment 230 V-klemmen: meestal 2 Nm (waarde op component gaat voor)

## Veiligheid (Techniek 02)
- Stroom door lichaam: 1 mA voelbaar · 10–20 mA verkramping · >30 mA ademhaling · >50 mA hartfibrilleren
- Veilige spanning droog: 50 V AC / 120 V DC
- NEN 3140: tot 1000 V AC · hoogspanning NEN 3840
- Herinstructie aanwijzing: gebruikelijk elke 3 jaar

## Regeltechniek (Techniek 04)
- Regelafwijking: e = W − X
- Omrekenen signaal → waarde: waarde = ondergrens + (signaal ÷ bereik) × (bovengrens − ondergrens); 0–10 V deel door 10 V; 2–10 V trek 2 V af, deel door 8 V; 4–20 mA trek 4 mA af, deel door 16 mA
- Voorbeelden: −10…+40 °C op 0–10 V → 5 K/V, 2 V = 0 °C, 6 V = 20 °C · vocht 0–100 %RV → 1 V = 10 %
- Ruwe kaartwaarde UR20 analoog: 0–27648 (controleer handleiding)
- Proportionele band 5 K: 1 K afwijking = 20 % uitgang · band 1 K: 1 K = 100 %. Versterking = omgekeerd van band.
- Driepunt: puls = (gewenste verplaatsing in %) × looptijd. 10 % bij 30 s = 3 s open-contact.
- Ni1000: ~1000 Ω bij 0 °C, ~1100 Ω bij kamertemperatuur, ca. 6 Ω/K; Pt1000 ca. 4 Ω/K. Siemens (LG-Ni1000) 5000 ppm/K vs DIN 43760 6180 ppm/K; verschil ca. 10 K bij 60 °C, ca. 17 K bij 100 °C.
- PI-instelling: Ti van de orde van de reactietijd van het proces; D meestal 0

## Water en lucht (Techniek 05)
- Vermogen water: kW = debiet (m³/h) × ΔT (K) × 1,16 (2 m³/h × 20 K ≈ 46 kW)
- ΔT radiatorgroep 70/50 = 20 K · vloerverwarming 35/28 = 7 K
- HR-ketel condenseert bij retour < ca. 55 °C
- Warmtepomp: ca. 2–3 % rendement per graad lagere aanvoer; COP ≈ 5 bij 35 °C, ≈ 3 bij 55 °C (bron 10 °C)
- Koelen: ventilatorconvector/koelbatterij 7/12 °C · klimaatplafond/betonkern ≥ 16 °C (dan vrije koeling mogelijk)
- Bodemtemperatuur ca. 10–12 °C
- Ventilatie: ca. 30 m³/h per persoon · CO₂ buitenlucht ca. 420 ppm · goed geventileerd < 800–950 ppm
- Vorstbeveiliging AHU: ca. 5 °C
- Frisse Scholen: klasse C wettelijk basis, A strengst

## Climatics (Techniek 06, Veldwerk 03)
- Stooklijn: twee punten (bijv. −10 °C en +20 °C) plus parallelverschuiving
- Standaard: locatie ontkoppeld na 15 min zonder data, waarde rood na 1 uur (deadman-periode per datapunt instelbaar)
- IO-interval demokoffer: 10 s

## Bus (Techniek 07)
- Slave-ID Modbus: 1–247 · max 32 apparaten per RS485-segment
- Afsluitweerstand 120 Ω aan beide uiteinden: gemeten tussen A en B ca. 60 Ω goed · ca. 120 Ω één mist · ca. 40 Ω één te veel
- Rustspanning (bias): > 200 mV tussen A en B
- Slave-id met hex-schakelaars: adres = hoog × 16 + laag (8 en E → 8×16+14 = 142)
- Modbus TCP poort 502
- Negatieve waarde als uint16: ~65 000 · schaalfactor ×10 vergeten: 45,2 → 452
