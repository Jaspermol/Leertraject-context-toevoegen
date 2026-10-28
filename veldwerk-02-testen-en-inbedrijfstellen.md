# Veldwerk 02 — Testen en inbedrijfstellen

Module: Veldwerk · Les 2 van 3 · Bron: ACS Academy (Climatics cursus), gelezen 27-10-2026 · Status: samenvatting (zonder praktijkopdracht en toetsen)
Voorkennis: Techniek 02 (NEN 3140/VOP), Techniek 06 (Climatics instellen), Veldwerk 01
Volgende les: Veldwerk 03 (storingzoeken)

Trefwoorden: inbedrijfstelling, I/O-test, veiligheidsketen, noodstop, vorstbeveiliging, referentiemeting, forceren, inregelen, ΔT, expansievat, ontluchten, begindrukval filter, PI-instelling, regelkring instellen, oplevering, opleverbaar, logboek, nazorg, checklist
Beantwoordt vragen als: In welke volgorde stel ik een installatie in bedrijf? Hoe bewijs ik per punttype dat een I/O-punt werkt? Hoe test ik de vorstbeveiliging? Hoe stel ik een regelkring in zonder te pendelen? Wanneer is een koppeling opleverbaar? Wat leg ik vast bij oplevering? Wanneer plan ik nazorg?

---

## Vaste volgorde
Documenten → kast → punten uit de klemmenlijst → water en lucht → pas daarna de regeling. Elke stap steunt op de vorige, zodat een fout niet ongemerkt doorgaat.

## Voorbereiding (voordat je de kast opent)
- Actuele revisie elektroschema, installatieschema en klemmenlijst
- Regeltechnische omschrijving of programma van eisen (wat de installatie zou moeten doen)
- Adreslijst met procescodes; Climatics-locatie met componenten al aangemaakt
- Aanwijzing, werkopdracht en bij klant met eigen IV de werkvergunning
- LOTO-set, gekeurd meetgereedschap (CAT III/IV), PBM
- Bouwkundige gereedheid: gebouw dicht, spanning aanwezig, installatie gevuld en ontlucht, filters geplaatst (anders moet je metingen overdoen)

## Kast en spanning
- Visuele controle spanningsloos: geen losse aders, geen beschadigde isolatie, afscherming compleet, wartels dicht, aarding aanwezig en aangedraaid
- Aandraaimomenten op vermogensklemmen
- Instellingen van beveiligingen vergelijken met schema en motortypeplaatjes
- Spanning in stappen: hoofdschakelaar en stuurspanning, dan groep voor groep; meten na elke stap
- **Veiligheidsketen eerst testen**: noodstop, brandmeldcontact, vorstbeveiliging, maximaalthermostaat, drukbeveiliging. Elke veiligheid één keer echt activeren en het effect vaststellen, niet uit de tekening afleiden.
- Werk in geopende verdeelinrichting onder spanning valt buiten VOP; vakbekwaam persoon doet dat deel.

## I/O-test (veld → regelaar, nooit andersom)
Van elk punt toon je aan dat veldapparaat, klem, kanaal en datapunt in Climatics bij elkaar horen.

| Punttype | Bewijs | Wat je noteert |
|---|---|---|
| Analoge ingang | Referentiemeting op twee verschillende waarden (bijv. omgeving en warm water) | Beide waardeparen plus afwijking; verkeerd voelertype zie je pas bij de warme meting |
| Digitale ingang | Contact echt omzetten in het veld | Status in rust én bediend |
| Analoge uitgang | Forceren op 0, 50 en 100 % en klep-/toerentalstand in het veld aflezen | Werkelijke stand per waarde en looprichting |
| Digitale uitgang | Forceren en effect ter plaatse waarnemen | Bevestiging dat het juiste toestel schakelde |

- Twee punten met dezelfde functie (twee aanvoervoelers, twee kleppen): beweeg ze één tegelijk (voeler verwarmen, kijken welk datapunt meeloopt, laten afkoelen, dan pas de tweede). Anders zie je niet of ze verwisseld zijn.
- **Vuistregel**: een datapunt is pas opgeleverd als je het hebt zien veranderen doordat jij in het veld iets deed. Een waarde die er goed uitziet maar niet meebeweegt bewijst niets.

## Waterzijdig
- Vullen, spoelen, ontluchten (na een dag draaien herhalen; lucht = geluid, slechte afgifte, corrosie)
- Expansievat: voordruk controleren mét drukloos systeem (verkeerde voordruk geeft drukschommelingen die als "storing ketel" terugkomen)
- Draairichting en opgenomen stroom pompen vs typeplaatje
- Inregelen groepen op ontworpen debiet; daarna ΔT bij vollast; noteer aanvoer, retour, debiet per groep
- ΔT: vermogen (kW) = debiet (m³/h) × ΔT (K) × 1,16. ΔT kleiner dan ontwerp = te veel water; groter = te weinig. Beide zijn inregelproblemen, geen regelproblemen: eerst oplossen voordat je aan regelparameters draait.

## Luchtzijdig
- Filters geplaatst en **begindrukval genoteerd** (nulpunt van elke latere vervuilingsmelding)
- Draairichting ventilatoren, opgenomen stroom, kleppen open vóór ventilator start
- Debieten per zone inregelen, balans toe-/afvoer bewust instellen (deurtest: klapt hij dicht of gaat hij zwaar open, dan is de balans scheef)
- WTW: temperatuurverschil over de wisselaar meten, bypass laten schakelen
- **Vorstbeveiliging beproeven**: instelwaarde tijdelijk boven de gemeten temperatuur zetten zodat hij aanspreekt; controleer dat kast stopt, luchtklep sluit en pomp draait; waarde terugzetten en vastleggen. Kan de waarde niet verzet worden: capillair of voeler afkoelen met koudespray.

## Regelkringen instellen (pas als installatie mechanisch en hydraulisch klopt)
1. Handbedrijf: beïnvloedt het regelorgaan het proces, en in de juiste richting?
2. Alleen P-actie met brede proportionele band; setpointstap geven en reactie bekijken
3. Band versmallen tot lichte uitdempende slingering, dan een stap terug
4. I-actie toevoegen tegen blijvende afwijking (te snel = traag pendelen); vuistregel: Ti van dezelfde orde als reactietijd van het proces
5. Een dag laten draaien, beoordelen over de hele dag, niet over vijf minuten
- Trage processen (vloerverwarming, betonkern): brede band en lange tijden. Snelle processen (inblaastemperatuur na batterij): scherper.
- Pendelt een kring: regelaar te scherp óf regelorgaan te groot gedimensioneerd (een klep die zijn hele werkgebied in de eerste 10 % doorloopt is met geen enkele instelling rustig te krijgen).

## Wanneer is een koppeling opleverbaar (zes punten)
1. Adreslijst compleet (procescode, omschrijving, eenheid, signaaltype, klem, kanaal, protocoladres, schaalfactor)
2. Punt voor punt getest (analoog op twee waarden, digitaal echt omgezet, uitgangen geforceerd met effect in het veld)
3. Herkomst gecontroleerd: geen punten met source *unaddressed* die wel gebruikt worden
4. Getagd en gekoppeld aan regelcomponent en ruimte/installatiedeel
5. Bewaking ingericht: grenzen, deadman, no-change op punten waarop de regeling steunt
6. Vastgelegd: adreslijst en testresultaten in opleverdossier, afwijkingen in logboek

## Climatics-koppeling en overdracht
- Configuratiewaarschuwingen oplossen, elke automatisering runnable
- Managed datapoints logisch laten bewegen (vraag aan → gevraagde temp omhoog → klep open → aanvoer volgt)
- Kloktijden, modes, setpoints volgens gebruik; vastleggen wie welke waarde heeft afgesproken
- Bewaking activeren (grenswaarden, deadman, no-change)
- **Opleverwaarden in logboek**: begindrukval filters, ingeregelde debieten, gemeten ΔT, ingestelde stooklijn, PI-parameters
- Gebruiker instrueren: wat kan hij zelf, wat melden, wat gebeurt automatisch; afspreken welke waarden hij mag wijzigen
- **Nazorg plannen**: 2–4 weken na oplevering trends beoordelen, en opnieuw na de eerste seizoenswisseling. Een installatie die in mei prima werkt laat pas in november zien of de stooklijn klopt (lage buitentemperatuur, nachtverlaging, opstarten).

## Checklist inbedrijfstelling (20 punten)
**Voorbereiding** 1 actuele revisie schema's/klemmenlijst/RTO · 2 werkopdracht, aanwijzing, werkvergunning · 3 installatie gevuld, ontlucht, op druk, filters geplaatst
**Kast** 4 visueel gecontroleerd, klemmen aangedraaid, afscherming compleet · 5 beveiligingsinstellingen vs schema/typeplaatjes · 6 aarding gecontroleerd en gemeten · 7 veiligheidsketen stuk voor stuk beproefd
**I/O-test** 8 alle AI op twee waarden vs referentie · 9 alle DI echt omgezet, beide standen · 10 alle uitgangen geforceerd 0/50/100 % met effect in veld
**Water & lucht** 11 draairichting en stroom pompen/ventilatoren · 12 groepen waterzijdig ingeregeld, debiet en ΔT genoteerd · 13 luchtdebieten ingeregeld, balans vastgesteld · 14 begindrukval schone filters genoteerd · 15 WTW beproefd incl. bypass
**Regeling** 16 regelkringen ingesteld en een etmaal beoordeeld · 17 stooklijn, kloktijden, modes, setpoints ingesteld en vastgelegd
**Climatics** 18 alle automatiseringen runnable, waarschuwingen opgelost · 19 bewaking ingericht
**Overdracht** 20 opleverwaarden in logboek, gebruiker geïnstrueerd, nazorg ingepland

## Zie ook
Techniek 04 (P/I/D, band), Techniek 05 (ΔT, luchtkast), Techniek 06 (tags, bewaking, stooklijn), Techniek 07 (bus), Veldwerk 01, Veldwerk 03.
