# SEPA Geschäftsvorfallcodes (GVC) im MT 940

## Überblick SEPA Zahlungsverkehr

Der SEPA Zahlungsverkehr wird durch spezifische Geschäftsvorfallcodes (GVC) im MT 940 Format dokumentiert. Diese Codes ermöglichen eine standardisierte Verarbeitung von Kontobewegungen in elektronischen Bankingsystemen.

## SEPA Direct Debit (Lastschrift)

- **GVC 104**: SEPA Direct Debit - Einzelbuchung Soll, SEPA B2B
- **GVC 107**: SEPA Direct Debit - Einzelbuchung Soll, SEPA Core
- **GVC 108**: SEPA Direct Debit - Rückbelastung Soll, SEPA B2B
- **GVC 109**: SEPA Direct Debit - Rückbelastung Soll, SEPA Core
- **GVC 171**: SEPA Direct Debit - Einzelbuchung Haben, SEPA Core
- **GVC 174**: SEPA Direct Debit - Einzelbuchung Haben, SEPA B2B
- **GVC 181**: SEPA Direct Debit - Wiedergutschrift Haben, SEPA Core
- **GVC 184**: SEPA Direct Debit - Wiedergutschrift Haben, SEPA B2B
- **GVC 192**: SEPA Direct Debit - Sammler Haben Core
- **GVC 193**: SEPA Direct Debit - Soll, SEPA Reversal
- **GVC 195**: SEPA Direct Debit - Sammler Soll, SEPA Core
- **GVC 196**: SEPA Direct Debit - Sammler Haben, SEPA B2B
- **GVC 197**: SEPA Direct Debit - Sammler Soll, SEPA B2B

## SEPA Credit Transfer (Überweisung)

- **GVC 116**: SEPA Credit Transfer - Einzelbuchung Soll
- **GVC 117**: SEPA Credit Transfer Instant - Einzelbuchung Soll
- **GVC 118**: SEPA Credit Transfer Instant - Einzelbuchung Soll
- **GVC 119**: SEPA Credit Transfer - Einzelbuchung Spende (SEPA Purpose Code: CHAR)
- **GVC 152**: SEPA Credit Transfer - Einzelbuchung Dauerauftrag
- **GVC 153**: SEPA Credit Transfer - Einzelbuchung Haben, Lohn, Gehalt, Rentengutschrift
- **GVC 154**: SEPA Credit Transfer - Einzelbuchung Haben, Vermögenswirksame Leistungen
- **GVC 156**: SEPA Credit Transfer - Einzelbuchung Haben, Überweisung öffentlicher Kassen
- **GVC 159**: SEPA Credit Transfer - Retoure Haben für einbringliche SEPA Überweisung
- **GVC 160**: SEPA Credit Transfer Instant - Rücküberweisung (wegen Rückruf)
- **GVC 166**: SEPA Credit Transfer - Einzelbuchung Haben
- **GVC 168**: SEPA Credit Transfer Instant - Einzelbuchung Haben
- **GVC 169**: SEPA Credit Transfer - Einzelbuchung Spende (SEPA Purpose Code: CHAR)
- **GVC 177**: SEPA Credit Transfer - Online Einzelbuchung Soll
- **GVC 188**: SEPA Credit Transfer Instant - Sammler Soll [Reserviert]
- **GVC 189**: SEPA Credit Transfer Instant - Sammler Haben
- **GVC 191**: SEPA Credit Transfer - Sammler Soll
- **GVC 194**: SEPA Credit Transfer - Sammler Haben

## SEPA Verwendungszweck und Felder

Der SEPA Verwendungszweck enthält strukturierte Informationen mit folgenden Elementen:

- **IBAN+**: SEPA IBAN Auftraggeber
- **BIC+**: SEPA BIC Auftraggeber
- **EREF+**: SEPA End to End-Referenz
- **KREF+**: Kundenreferenz
- **MREF+**: SEPA Mandatsreferenz
- **CRED+**: SEPA Creditor Identifier
- **DEBT+**: Originator Identifier
- **COAM+**: Zinskompensationsbetrag
- **OAMT+**: Ursprünglicher Umsatzbetrag
- **SVWZ+**: SEPA Verwendungszweck
- **ABWA+**: Abweichender SEPA Auftraggeber
- **ABWE+**: Abweichender SEPA Empfänger
- **BREF+**: Bankreferenz, Instruction ID
- **RREF+**: Retourenreferenz

## Weitere wichtige Informationen

- **Bankleitzahl**: BIC wird im Unterfeld 20-29 übermittelt
  - SEPA SCT = Schuldner
  - SEPA SDD = Gläubiger

- **Kontonummer**: IBAN wird im Unterfeld 20-29 übermittelt
  - SEPA SCT = Schuldner
  - SEPA SDD = Gläubiger

- **Name**: Maximal 54 Zeichen
  - SEPA SCT = Schuldner
  - SEPA SDD = Gläubiger

- **Rückgabegrund**: Textschlüsselergänzung zum SEPA Code (z.B. AC01) sowie Transaktionstyp bei SEPA Lastschrift (FRST, RCUR, OOFF, FNAL)

- **Name/Anschrift des Zahlungsempfängers bei SEPA SCT bzw. des Zahlers SEPA SDD**: Maximal 54 Zeichen

- **Weiterer SEPA Verwendungszweck**: Fortführung aus Unterfeld 20-29 mit z.B. ISO-Reason, Rückgabegrund im Klartext, Text „AWV Meldepflicht"
