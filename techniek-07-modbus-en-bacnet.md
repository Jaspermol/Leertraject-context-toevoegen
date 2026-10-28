# Techniek 07 — Modbus en BACnet

Module: Techniek (Techniekbasis) · Les 7 van 7 · Bron: ACS Academy (Climatics cursus), gelezen 27-10-2026 · Status: samenvatting in eigen woorden (zonder praktijkopdracht, zelftoets en toets)
Voorkennis: Techniek 04, 06
Volgende les: Veldwerk 01 — Installeren en aansluiten

Trefwoorden: Modbus TCP, Modbus RTU, RS485, gateway, daisy chain, afsluitweerstand 120 Ω, bias, slave-ID, hex-schakelaars, CIM 200, holding register, input register, schaalfactor, parse type, signed, BACnet, device-instantie, AI AV BI BV MSV, COV, polling
Beantwoordt vragen als: Hoe leg ik een RS485-bus aan? Hoe meet ik afsluitweerstanden (60 Ω)? Hoe stel ik een slave-id in met hex-schakelaars? Wat vul ik in bij Create address? Hoe lees ik een BACnet-object? Waarom een plausibel maar fout getal?

---

- Bus voor waarden die een apparaat zelf kent; kaart voor wat je zelf bedraadt. Waarden via bus komen uit de software van het apparaat en zijn niet met een eigen meter te verifiëren.
- Modbus TCP (ethernet, poort 502, unit-id, te pingen) vs. Modbus RTU (RS485, via gateway, max 32 apparaten per segment, slave-ID 1–247). ACS-server is master, apparaat slave.
- RS485: één doorlopende daisy chain, doorlussen onder de klemschroef, geen sterren of aftakkingen. Getwist paar, A en B in hetzelfde paar, 0 V als derde ader, afscherming aan één kant aarden. Afsluitweerstand 120 Ω alleen aan de twee uiteinden; pull-up/pull-down alleen bij de master/gateway.
- Meten: spanningsloos, Ω tussen A en B: ca. 60 Ω goed, ca. 120 Ω = één weerstand, ca. 40 Ω = drie. Rustspanning met bus aan: > 200 mV verschil tussen A en B; 0 V = geen bias. Snelheid, pariteit en stopbits moeten bij alle apparaten en de gateway gelijk zijn. Diagnose-tool: USB-RS485 (FTDI USB-RS485-WE-1800-BT) om mee te lezen.
- Slave-ID hex-schakelaars (bijv. Grundfos CIM 200): adres = SW6 × 16 + SW7; 8 en E = 142. Pas na spanningsloos maken en herstarten geldig.
- Climatics-adresvelden (Create address): Data type (holding_register, input_register, coil, discrete_input), Register number (Set range), Slave ID, Factor, Parse type (byte-/woordvolgorde), Signed, Only write on change, High priority, linear conversion/offset. Registerlijst van de fabrikant is de bron; noteer de herkomst van de lijst.
- BACnet/IP: device-instantie + objecttype (AI, AV, BI, BV, MSV) + objectnummer, present value, eenheid zit in het object. COV (bij verandering) vs. polling.
- Vier fouten zonder storing: register ernaast, schaalfactor vergeten, verkeerd datatype (negatief als uint16 → ~65 000), dubbel slave-ID. Controleer elk nieuw punt tegen een fysieke referentie op twee waarden en zet no-change-bewaking op kritieke adressen, deadman op device-niveau.

## Zie ook
Techniek 06, Veldwerk 03 (bus praat niet).
