# Veldwerk 03 — Storingzoeken (tijdens aansluiten en inbedrijfstellen)

Module: Veldwerk · Les 3 van 3 · Bron: ACS Academy (Climatics cursus), gelezen 27-10-2026 · Status: samenvatting (zonder praktijkopdracht en toetsen)
Voorkennis: Techniek 04 (basis regeltechniek), Veldwerk 02
Let op: gaat over fouten bij aansluiten en inbedrijfstellen. Storingzoeken aan een installatie die al lang draait is volgens de cursus een ander vak met een eigen (nog te volgen) les.

Trefwoorden: storingzoeken, keten halveren, Ni1000, kabelbreuk, kortsluiting, tweedraads, 0–10 V, 4–20 mA, GND, bereik, contacttype, potentiaalvrij, klepmotor, looprichting, klembout, luchtklep, lamellen, looptijd driepunt, pompregelstand, draairichting ventilator, offset, drukverschil, deadman-periode, no-change, bus praat niet, logboek
Beantwoordt vragen als: Hoe pak ik storingzoeken aan? Wat betekent een extreem hoge/lage voelerwaarde? Waarom beweegt de klep niet? Waarom staat mijn waarde stil? Wat controleer ik als een Modbus-bus niet praat? Waarom meldt Climatics pas na een kwartier ontkoppeld?

---

## Principe: de keten halveren
Keten: veldapparaat → bedrading → klem → kanaal → adres → datapunt → gebruik in regelcomponent. Een storing zit in één schakel. Werk niet van voren naar achteren maar vanuit het midden: kies een punt dat je met de werkelijkheid kunt vergelijken. Klopt het daar, dan zit de fout erna, anders ervoor.

Vijf vragen:
1. **Wat is de klacht precies?** (welke ruimte, wanneer, sinds wanneer, wat is er veranderd)
2. **Klopt het getal met de werkelijkheid?** Meet ter plaatse of vergelijk met tweede bron (manometer naast drukopnemer, weerstation naast buitenvoeler, thermometer in luchtstroom).
3. **Beweegt het punt als ik iets doe?** Een waarde die nooit verandert is verdacht, ook als hij plausibel is. Forceren, contact omzetten, voeler opwarmen.
4. **Doet de regelcomponent wat je verwacht?** Vergelijk vraag met uitgang; zo niet: configuratie of uitgangskant, niet de meting.
5. **Kan de installatie het wel?** Ontbrekend debiet, te grote klep, verkeerd voorgedrukt expansievat en lucht zijn geen regelproblemen en laten zich niet wegregelen.
- Niet aan parameters draaien als de oorzaak mechanisch/hydraulisch is: regelaar traag zetten maakt het erger (klep blijft te groot).

## Weerstandsvoelers (Ni1000, Pt1000)
| Je ziet in Climatics | Je meet aan voeler | Oorzaak |
|---|---|---|
| Uiterst hoge waarde of kabelbreukmelding | Geen doorgang | Ader gebroken, klem los of voeler onderbroken |
| Uiterst lage waarde | Bijna 0 Ω | Kortsluiting in kabel of voeler |
| Plausibel maar mis, hoe warmer hoe meer | Weerstand klopt met tabel | Verkeerd voelertype ingesteld op kaart (Siemens vs DIN) |
| Plausibel maar constant paar tienden mis | Weerstand klopt met tabel | Lange dunne kabel telt mee op tweedraads aansluiting |
- Meten met voeler losgenomen: ca. 1000 Ω bij 0 °C, ca. 1100 Ω bij kamertemperatuur. Ni1000 ≈ 6 Ω per K, Pt1000 ≈ 4 Ω per K.
- Ni1000-Siemens en DIN 43760 zijn gelijk bij 0 °C en lopen daarna uit elkaar: 10 K of meer verschil op een warme aanvoerleiding.

## Actieve voelers 0–10 V
- Geen 24 V op de voeler → uitgang blijft 0 V, regelaar leest onderkant bereik. Meet eerst of voeding aankomt.
- Geen gemeenschappelijke GND → signaal zweeft, waarde springt.
- Uitgang op voedingsklem → apparaat meestal kapot.
- Verkeerd bereik ingesteld (voeler 0–50 °C, kaart rekent 0–100 °C) → waarde beweegt netjes mee maar klopt nergens. Vergelijk grenzen op typeplaatje met het datapunt.

## Stroomsignalen 4–20 mA
4 mA is de onderkant, niet nul. Lees je 0 mA: lus onderbroken (kabelbreuk, losse klem, zender zonder voeding).

## Digitale in- en uitgangen
- Contacttype verwisseld (verbreekcontact op ingang ingesteld als maakcontact): permanent storing terwijl niets aan de hand is.
- Geen potentiaalvrij contact: spanning uit het veld op een ingang die zelf 24 V levert → onbetrouwbaar of kaart kapot. Spanningsloos controleren of het contact echt vrij is.
- Uitgang op verkeerde spanningssoort (24 V AC-klepmotor op DC-uitgang): doet niets of gaat stuk.

## Het toestel doet niet wat je vraagt
- **Klepmotor verkeerde kant op**: looprichting-schakelaar op motor; vergelijk met bedoelde open/dicht.
- **Motor zit niet vast op de as** (klembout bij luchtklep): zet vast met klep in een bekende stand.
- **Asstand klopt niet met stuurstand**: as van luchtklep is rond; monteur maakt vaak zelf een snede in de kop in lijn met het klepblad. Stuur 0 % en 100 % en kijk of de snede meedraait en het blad echt dicht/open gaat.
- **Klep zit vast**: aandrijving losmaken/handstand, as met de hand draaien; zwaar = afsluiter, niet regeling.
- **Meerbladige luchtklep klemt** (tandwieltjes/koppelstang; niet vlak ingebouwd, frame verwrongen, vuil, corrosie, plakkende afdichtstrips): met de hand door het hele bereik bewegen, alle lamellen moeten meegaan en sluiten. Los het op aan de klep, niet met een zwaardere motor.
- **Stuurbereik klopt niet** (aandrijving 2–10 V, uitgang 0–10 V): bij 50 % staat de klep op ruim een derde en onder 2 V beweegt hij niet. Stel beide kanten gelijk in.
- **Driepunt: looptijd klopt niet**: regelaar telt eigen pulsen. Vergelijk typeplaatje met instelling, laat de klep één keer helemaal dichtlopen. Klep draait verkeerd om = twee aders verwisseld.
- **Pomp in verkeerde regelstand** (constante druk / proportionele druk / vast toerental): pomp en klepregeling regelen tegen elkaar in.
- **Ventilator draait verkeerde kant op**: nog steeds lucht maar veel minder, te laag debiet bij te lage stroom. Twee fasen verwisselen.

## De meting klopt niet
- Aanvoer en retour verwisseld (retour hoger dan aanvoer terwijl groep verwarmt): één voeler tegelijk bewegen.
- Voeler wijkt af: vergelijken met geijkte referentie op dezelfde plaats, afwijking als offset in regelaar/Climatics, **afwijking in logboek**.
- Drukverschilmeter verkeerd: plus aan hoge kant, min aan lage; slangetjes op juiste meetpunten; nulpunt afstellen met ventilator uit.
- Datapunt hangt aan verkeerde component: adres en waarde kloppen, maar de ene groep regelt op de meting van de andere.

## De bus praat niet (volgorde)
1. Spanning op apparaat? Leds op gateway: alleen voeding of ook verkeer?
2. A en B verwisseld? (namen verschillen per fabrikant)
3. Afsluitweerstanden meten spanningsloos tussen A en B: ca. 60 Ω goed, ca. 120 Ω = één mist, ca. 40 Ω = één te veel
4. Bias aan? Gelijkspanning tussen A en B zonder verkeer: > 200 mV; ca. 0 = zwevende lijn
5. Slave-id juist én uniek op deze bus?
6. Snelheid, pariteit, stopbits overal gelijk?
7. Werkt het als dit het enige apparaat is? Zo ja: bekabeling of een ander apparaat.

## Wat Climatics laat zien, en wanneer
- Standaard: locatie pas "ontkoppeld" na een kwartier zonder data, waarde pas rood na een uur. Bij oplevering: je rijdt weg en de melding komt pas thuis.
- Per datapunt een **deadman-periode**: tijdens inbedrijfstelling korter zetten, daarna terug naar wat bij de installatie past (anders onnodige meldingen). Melding kan ook uit of notificatie gedempt.
- Kijk naar de leeftijd van de waarde (tooltip toont minuten geleden). Rode markering en connection card bewegen pas na pagina herladen.

| Je ziet | Meestal |
|---|---|
| Waarde staat stil, na een uur rood | Apparaat antwoordt niet: IP, slave-id, poort, meepraten op bus |
| Geschreven waarde wordt niet overgenomen | BACnet: hogere prioriteit op object wint; Climatics leest na schrijven niet terug, controle doe je zelf |
| Eén waarde ontbreekt, rest loopt door | Datapunt hangt niet meer aan adres (bijv. verwijderd en opnieuw aangemaakt) |

## Vier cases (koppelfouten zonder storingsmelding)
1. **Aanvoertemperatuur weken exact 21,0 °C, kaarsrechte lijn**: dode waarde die wél binnenkomt (vastgelopen veldregelaar of gekopieerd adres naar niet-bestaand punt). Deadman gaat niet af; **no-change** is hiervoor bedoeld. Adres controleren, koppeling herstarten, no-change aanzetten.
2. **Buitentemperatuur 's nachts goed, overdag 8 K te hoog**: plaatsingsfout, voeler op zonbeschenen gevel. Stooklijn vraagt te weinig aanvoer juist als het nodig is. Voeler naar noordgevel of weerdata; altijd eerst vergelijken met weerstation voordat je aan de stooklijn draait.
3. **Nieuwe drukopnemer 3,5 bar, manometer 0,35 bar**: factor 10 schaalfout (tienden niet teruggerekend of verkeerde eenheid). 3,5 bar is plausibel, dus valt niet op. Elk analoog punt tegen fysieke referentie op twee waarden; met één punt zie je een nulpuntfout niet.
4. **Pomp meldt permanent storing maar draait**: contacttype (maak/verbreek) verwisseld t.o.v. configuratie. Test door contact echt te forceren: een storingsmelding die je nooit hebt zien wisselen heb je niet getest.

## Wat je vastlegt (logboek)
Klacht, gemeten waarden, wat je hebt veranderd, wat er nog openstaat. Een vermoeden mag erin, als vermoeden.

## Tot slot (norm van de cursus)
Je bent klaar met de opleiding als je een installatie in vier zinnen kunt beschrijven: wat wekt op, hoe komt het bij de afgifte, waarop wordt geregeld, en waar zit de zwakke plek.

## Zie ook
Techniek 04 (signalen, bereik, Ni1000-tabellen), Techniek 06 (bewaking), Techniek 07 (bus, vier stille fouten), Veldwerk 02, diagnose-symptomen.md.
