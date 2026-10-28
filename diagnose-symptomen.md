# Diagnose per symptoom — "ik zie X, wat is het?"

Doorsnijdende naslag uit Techniek 03–07 en Veldwerk 02–03. Bron: ACS Academy-lessen. Werkwijze eerst: **keten halveren** (veldapparaat → bedrading → klem → kanaal → adres → datapunt → regelcomponent), vergelijk met een fysieke referentie, beweeg het punt zelf. Zie `00-index.md`.

## Meetwaarden
| Symptoom | Meest waarschijnlijk | Controle | Les |
|---|---|---|---|
| Voeler: extreem hoge waarde / kabelbreuk | Ader gebroken, klem los, voeler onderbroken | Voeler los, Ω meten (geen doorgang) | V03 |
| Voeler: extreem lage waarde | Kortsluiting in kabel of voeler | Ω ≈ 0 | V03 |
| Voeler: plausibel maar mis, hoe warmer hoe meer | Verkeerd voelertype op kaart (Siemens vs DIN Ni1000) | Ω klopt met tabel; type vergelijken met kanaalinstelling | V03, T04 |
| Voeler: constant paar tienden mis | Lange dunne kabel op tweedraads aansluiting | Kabelweerstand meetellen | V03 |
| 0–10 V-voeler blijft op onderkant | Geen 24 V of geen gemeenschappelijke GND | Voeding op voeler meten; GND's koppelen | V03, T01 |
| Waarde beweegt mee maar klopt nergens | Bereik/lineaire conversie verkeerd | Grenzen typeplaatje vs datapunt | V03, T04 |
| 4–20 mA leest 0 mA | Lus onderbroken (levend nulpunt) | Kabelbreuk, losse klem, voeding zender | V03 |
| Aanvoer en retour lijken verwisseld | Voelers verwisseld | Één voeler tegelijk bewegen | V03, V02 |
| Drukverschil nul of negatief | Slangetjes verwisseld/nulpunt | Plus hoog, min laag, nulpunt met ventilator uit | V03 |
| Buitentemperatuur overdag veel te hoog | Voeler in de zon | Vergelijk met weerstation | V03 |
| Waarde ×10 of ÷10 | Schaalfactor/eenheid | Fysieke referentie op twee waarden | T07, V03 |
| Negatieve temperatuur springt naar ~65 000 | Datatype uint16 i.p.v. signed | Signed aanvinken | T07 |
| Waarde plausibel maar van "buurwaarde" | Register één ernaast (0- vs 1-gebaseerd) | Registerlijst fabrikant | T07 |
| Waardes absurd bij 32-bits | Woord-/bytevolgorde (parse type) | Parse type wisselen | T07 |
| Waarde kaarsrecht, weken dezelfde | Dode waarde die wel binnenkomt | No-change-bewaking, adres/koppeling | V03, T06 |
| Waarde staat stil, na uur rood | Apparaat antwoordt niet | IP, slave-id, poort, bus | V03 |
| Eén waarde ontbreekt, rest loopt door | Datapunt niet meer aan adres gekoppeld | Adressenlijst filteren op gekoppeld datapunt | V03, T06 |
| Waarde komt van verkeerd punt na kaartwijziging | Adres verschoven door moduleopbouw | Datapunten aan bedoeld kanaal controleren | T06 |

## Schakelen en bewegen
| Symptoom | Meest waarschijnlijk | Controle | Les |
|---|---|---|---|
| Storingsmelding permanent, apparaat draait | Contacttype maak/verbreek verwisseld | Contact echt forceren | V03 |
| Relais trekt niet aan | Open voorwaarde bovenin keten of spoel stuk | Meten over A1/A2; van boven naar beneden | T03 |
| Spoel trekt aan, motor draait niet | Hoofdstroomdeel of vastgebrand contact | Contactspiegel volgen | T03 |
| Klep draait verkeerde kant op | Looprichting-schakelaar; driepunt: aders verwisseld | Schakelaar/aders | V03 |
| Klep beweegt niet, motor draait wel | Klembout los op as | As vastzetten in bekende stand | V03 |
| Klep staat anders dan gevraagd | Bereik 2–10 vs 0–10 V; looptijd driepunt | Beide kanten gelijk; looptijd vs typeplaatje | V03 |
| Meerbladige luchtklep sluit niet | Lamellen klemmen / frame verwrongen | Met de hand door bereik | V03 |
| Component onverklaarbaar aan of uit | Hand-0-auto staat op hand | Schakelaar controleren, melden | T03 |
| Ventilator weinig lucht, lage stroom | Verkeerde draairichting | Twee fasen verwisselen | V03, T01 |
| Automaat valt bij start van motor | Verkeerde karakteristiek (B i.p.v. C) | Karakteristiek | T01 |
| Aardlek valt achter omvormer / beveiligt niet | Type A i.p.v. B | Type B | T01 |
| Pomp en klepregeling werken tegen elkaar | Pomp in verkeerde regelstand | Constante druk/proportioneel/vast toerental | V03 |

## Regeling en hydrauliek
| Symptoom | Meest waarschijnlijk | Controle | Les |
|---|---|---|---|
| Kring pendelt | P te scherp, of regelorgaan te groot | P rustiger; kijk of klep in eerste 10 % werkt | T04, V02 |
| Blijvende afwijking | Alleen P, geen I | I-actie toevoegen | T04 |
| ΔT te klein | Te veel debiet, bypass, weinig vraag | Debiet inregelen | T05, V02 |
| ΔT te groot | Te weinig debiet: pomp, klep, lucht, filter | Pomp/klep/ontluchten/filter | T05, V02 |
| Drukschommelingen "storing ketel" | Verkeerd voorgedrukt expansievat | Voordruk met drukloos systeem | V02 |
| Geluid, slechte afgifte | Lucht in systeem | Ontluchten, na een dag herhalen | V02 |
| Gebouw te warm, kranen dicht, hoge retour | Stooklijn te steil | Stooklijn, eerst buitenvoeler checken | T06 |
| Ruimten worden niet warm op koude dagen | Stooklijn te vlak | Idem | T06 |
| HR-ketel haalt geen rendement | Retour boven ca. 55 °C | Retour/afgiftetemperatuur | T05 |
| Onderdruk, klapperende deuren | Teveel afzuigen | Debietbalans | T05, V02 |
| AHU-vervuilingsmelding onbetrouwbaar | Beginwaarde schone filters niet genoteerd | Begindrukval vastleggen | V02 |

## Bus (RS485/Modbus)
Volgorde: voeding en leds → A/B verwisseld → afsluitweerstanden (60 Ω) → bias (>200 mV) → slave-id uniek → snelheid/pariteit/stopbits gelijk → enige apparaat op de bus? Zie T07 en V03. Typische oorzaken van haperen: sterren of aftakkingen, lasdop naast apparaat, derde afsluitweerstand midden op de lijn, afscherming aan twee kanten geaard, dubbel slave-ID (afwisselend antwoorden).

## Climatics-configuratie
| Symptoom | Oorzaak | Les |
|---|---|---|
| Component draait niet, foutmelding/waarschuwing | Ontbrekende koppeling, lege verplichte ingang, verkeerde node | T06 |
| Datapunt met herkomst unaddressed | Geen adres gekoppeld | T06 |
| Adres zonder datapunt | Signaal komt binnen waar niemand iets mee doet | T06 |
| Melding komt pas na kwartier/uur | Standaard deadman-vertraging | V03 |
| Geschreven waarde komt niet aan (BACnet) | Hogere prioriteit op object; Climatics leest niet terug of het schrijven gelukt is | V03 |
| Waarde komt zomaar van ander apparaat | Interne doorschrijving (write to/from) niet zichtbaar in schema | T06 |

## Ontwerp- en werkprincipes die in de cursus steeds terugkomen
1. Procescode is de rode draad van schema tot datapunt.
2. Faalveilig bedraden: veiligheden als verbreekcontact; levend nulpunt (2–10 V, 4–20 mA).
3. Terugmelding naast aansturing, anders weet je niet of de klep echt staat waar hij moet staan.
4. Stille fouten zijn gevaarlijker dan storingen: verkeerd voelertype, schaalfactor, verschoven adres, verkeerd meetende voeler. Bewaak met no-change en controleer tegen een fysieke referentie op twee waarden.
5. Lage temperatuur verwarmen en hoge temperatuur koelen: kleiner verschil overbruggen = minder energie.
6. Bij ΔT, filterdrukval en WTW-temperatuurverschil meten, niet alleen kijken of iets draait.
7. Configuratie opruimen vóór oplevering: geen waarschuwingen, geen adressen zonder datapunt, geen datapunten zonder procescode of tags.
8. Een datapunt is pas opgeleverd als je hem hebt zien veranderen doordat jij in het veld iets deed.
9. Inregelproblemen (debiet, ΔT, klepgrootte) los je niet op met regelparameters.
