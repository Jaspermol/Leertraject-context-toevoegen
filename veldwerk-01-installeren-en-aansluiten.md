# Veldwerk 01 — Installeren en aansluiten

Module: Veldwerk · Les 1 van 3 · Bron: ACS Academy (Climatics cursus), gelezen 27-10-2026 · Status: samenvatting (zonder praktijkopdracht en toetsen)
Voorkennis: Techniek 02 (NEN 3140/VOP), Techniek 03 (schema's lezen)
Volgende les: Veldwerk 02 (testen en inbedrijfstellen)

Trefwoorden: nieuwe regelkast, ombouw, coderen, labelen, klemmenlijst, aandraaimoment, momentschroevendraaier, sluiting, aarde, vreemde spanning, onder spanning brengen, netwerk, aanmelden Climatics, gateway
Beantwoordt vragen als: Hoe pak ik een ombouw van een bestaande regelkast aan? Wat controleer ik voordat er spanning op gaat? Op welk moment trek ik klemmen aan en waarom? Hoe breng ik een kast stap voor stap onder spanning? Wat moet ik regelen voordat de regelaar zich bij Climatics kan melden?

---

## Twee soorten opdrachten
- **Complete nieuwe regelkast** (nieuwbouw, of oude kast zo verouderd dat alles vervangen wordt): de installateur legt en codeert de kabels volgens de klemmenlijst van ACS. Jouw werk: sensoren en actoren op de juiste klemmen aansluiten en testen.
- **Ombouw van een bestaande kast**: kast en klemmenstroken blijven, oude regelcomponenten eruit, nieuwe erin. Je moet eerst vaststellen wat er ligt en label zelf de bestaande kabels vóórdat er iets los gaat.

## Coderen en labelen
Coderen = aan elke kabel kunnen zien waar hij heen gaat. De klemmenlijst is de basis; per klem staat klemmenstrook, klemnummer, fysieke aansluiting, aansluitnummer op de sensor, aderkleur/nummer en functie (bijv. X31 klem 1 = retoursensor ketel, wit, voeding; klem 2 = rood, meetsignaal).

## Een bestaande kast ombouwen (volgorde)
1. **Afschakelen afstemmen**: vraag de projectleider of het uitzetten van de oude regeling met de gebruikers is afgestemd. Zolang de regeling uit staat liggen verwarming, koeling en ventilatie stil.
2. **Spanningsloos maken en aantonen** samen met de installatieverantwoordelijke of een vakbekwaam persoon (zie Techniek 02), altijd in overleg met de klant of diens installatieverantwoordelijke.
3. **Niet alleen op de tekening vertrouwen**: er kunnen ongedocumenteerde wijzigingen zijn. Voorbeeld: later aangesloten zonnepanelen = een tweede voeding die je niet verwacht.
4. **Nummering en mutaties controleren**: kloppen klemmenstroken nog met de lijst, staan er met de hand aangetekende wijzigingen op de schema's in de kast? Houd de oude schema's bij de hand tijdens de ombouw.
5. **Ombouwen volgens de nieuwe tekening**: vaak verdwijnen oude relais en wordt de opbouw anders.
6. **24 V AC en 24 V DC gescheiden houden**: verwisselen = iets werkt niet of gaat stuk. Is 24 V AC volgens het nieuwe schema niet meer nodig, dan verwijderen.
7. **Netwerk regelen**: is de internetaansluiting al gerealiseerd, zijn de netwerkgegevens bekend? Zonder die gegevens kan de regelaar aan het eind niet worden aangemeld.
- Binnen je aanwijzing blijven: een geopende verdeelinrichting onder spanning valt buiten een VOP-aanwijzing. Kan een stap niet spanningsloos, dan doet een vakbekwaam persoon dat deel.

## Controles spanningsloos, vóór inschakelen
- **Aansluitingen**: 230 V niet verwisseld met 24 V-circuit? 24 V AC niet verwisseld met 24 V DC? Elke ader op de klem waar hij volgens het schema hoort?
- **Aandraaimoment**: alle schroeven nalopen met momentschroevendraaier, ingesteld op de waarde die op het component staat; voor 230 V meestal 2 Nm. Te slap = overgangsweerstand, verbinding wordt warm, vlamboog, schroef brandt door. Te vast = schroef of klem kapot.
- **Sluiting**: alle fasen, nul en aarde onderling doormeten op sluiting.
- **Aarde**: overal goed doorverbonden?
- **Vreemde spanning**: nergens spanning op klemmen die spanningsloos horen te zijn, ook niet op buskabels. Bij een verkeerd aangesloten Modbus RTU-verbinding kan er 24 V of zelfs 230 V op de bus staan; de gateways zijn dan stuk voordat je iets hebt ingeschakeld.

## Spanning erop, stap voor stap
1. Alle installatieautomaten uit.
2. Meten aan de voedingskant of de juiste spanning binnenkomt.
3. Automaten één voor één inschakelen; circuit achter elke automaat controleren met de duspol.
4. Na de trafo's het laagspanningscircuit meten met de multimeter op de juiste stand (24 V DC op gelijkspanning).

## Netwerk en aanmelden bij Climatics
Branden op regelaar en I/O-kaarten alle lampjes groen, dan de internetaansluiting maken. Als alles goed geconfigureerd is melden regelaars en gateways zich zelf aan bij het Climatics-platform. Via laptop controleren of alle adressen binnenkomen. Daarna volgt Veldwerk 02.

## Zie ook
Techniek 01 (meten, duspol, aandraaimoment-achtergrond), Techniek 02 (vijf veiligheidsregels), Techniek 03 (klemmenlijst, I/O-bladen), Techniek 07 (bus, afsluitweerstanden), Veldwerk 02.
