 SEPA, MT940, CAMT & DTA: Übersicht der Zahlungsverkehrsstandards

## 1. Historische Entwicklung im Zahlungsverkehr

### DTA (Datenträgeraustausch)
- **Einführung**: 1976 in Deutschland
- **Funktion**: Veraltetes Verfahren für den elektronischen Zahlungsverkehr in Deutschland
- **Format**: Feste, strukturierte Textdateien (früher per Diskette oder Dateiübertragung)
- **Anwendungsbereich**: Überweisungen, Lastschriften und Gutschriften zwischen Banken und Kunden
- **Status**: Durch SEPA weitgehend abgelöst
- **Charakteristik**: Zahlungsauftrag (vom Kunden an die Bank)

### MT940 (Message Type 940)
- **Funktion**: Elektronischer Kontoauszug im SWIFT-Format
- **Format**: Festgelegte Textfelder mit strukturierten Informationen
- **Anwendungsbereich**: Weltweiter Einsatz im internationalen Zahlungsverkehr
- **Status**: Wird durch CAMT.053 abgelöst
- **Charakteristik**: Kontoauszug (von der Bank zum Kunden)
- **Besonderheit**: Enthält GVC-Codes (Geschäftsvorfallcodes) zur Kennzeichnung der Buchungsarten

### SEPA (Single Euro Payments Area)
- **Funktion**: Europäischer Zahlungsverkehrsraum zur Standardisierung von Überweisungen, Lastschriften und Kartenzahlungen in Euro
- **Format**: XML-basiert (SEPA-XML)
- **Hauptmerkmale**:
  - IBAN & BIC als einheitliche Kontodaten
  - PAIN-Formate für Zahlungsaufträge
  - CAMT-Formate für Kontoauszüge
- **Status**: Aktueller Standard im europäischen Zahlungsverkehr
- **Ersetzt**: Nationale Formate wie DTA

### CAMT (Cash Management)
- **Funktion**: XML-basierte Kontoauszugsstruktur im Rahmen von SEPA
- **Formate**:
  - **CAMT.052**: Tagesaktuelle Kontoumsätze (Vormerkposten)
  - **CAMT.053**: Elektronischer Kontoauszug (Ende des Tages, ersetzt MT940)
  - **CAMT.054**: Einzeltransaktionsdaten (Detailinformationen zu Buchungen)
  - **CAMT.029**: Negativantwort auf eine Zahlungsuntersuchung
  - **CAMT.056**: Rückruf von Überweisungen bei Fehlern
- **Status**: Aktueller Standard für Kontoauszüge im SEPA-Raum

## 2. SEPA Geschäftsvorfallcodes (GVC) im Detail

### Überblick
Die Geschäftsvorfallcodes (GVC) ermöglichen eine standardisierte Verarbeitung von Kontobewegungen in elektronischen Bankingsystemen. Sie dokumentieren den SEPA-Zahlungsverkehr im MT940-Format und werden auch in CAMT-Formaten weitergeführt.

### Warum GVC-Codes im CAMT-Format?
Obwohl CAMT ein neues XML-Format ist, werden die alten GVC-Codes weiterhin verwendet aus folgenden Gründen:

1. **Rückwärtskompatibilität**: 
   - Viele Buchhaltungs- und ERP-Systeme basieren auf den alten GVC-Codes
   - Vermeidung von Systemanpassungen bei Unternehmen

2. **Automatisierung**:
   - Automatische Kategorisierung von Transaktionen
   - Einheitliche Interpretation von Buchungen

3. **Implementierung in CAMT**:
   - In CAMT im `<Prtry>`-Feld (Proprietary Code) zusätzlich mitgeführt
   - Beispiel: `<Prtry><Cd>NDDT+171+9075/625</Cd><Issr>DK</Issr></Prtry>`
     - "NDDT" = Non-Domestic Direct Debit (internationale Lastschrift)
     - "171" = GVC-Code für Lastschrift
     - "9075/625" = zusätzliche interne Codes der Bank
     - "DK" = Issuer-Code (Deutsche Kreditwirtschaft)

### SEPA Direct Debit (Lastschrift) GVC-Codes

| Code | Beschreibung |
|------|--------------|
| 104 | SEPA Direct Debit - Einzelbuchung Soll, SEPA B2B |
| 107 | SEPA Direct Debit - Einzelbuchung Soll, SEPA Core |
| 108 | SEPA Direct Debit - Rückbelastung Soll, SEPA B2B |
| 109 | SEPA Direct Debit - Rückbelastung Soll, SEPA Core |
| 171 | SEPA Direct Debit - Einzelbuchung Haben, SEPA Core |
| 174 | SEPA Direct Debit - Einzelbuchung Haben, SEPA B2B |
| 181 | SEPA Direct Debit - Wiedergutschrift Haben, SEPA Core |
| 184 | SEPA Direct Debit - Wiedergutschrift Haben, SEPA B2B |
| 192 | SEPA Direct Debit - Sammler Haben Core |
| 193 | SEPA Direct Debit - Soll, SEPA Reversal |
| 195 | SEPA Direct Debit - Sammler Soll, SEPA Core |
| 196 | SEPA Direct Debit - Sammler Haben, SEPA B2B |
| 197 | SEPA Direct Debit - Sammler Soll, SEPA B2B |

### SEPA Credit Transfer (Überweisung) GVC-Codes

| Code | Beschreibung |
|------|--------------|
| 116 | SEPA Credit Transfer - Einzelbuchung Soll |
| 117 | SEPA Credit Transfer Instant - Einzelbuchung Soll |
| 118 | SEPA Credit Transfer Instant - Einzelbuchung Soll |
| 119 | SEPA Credit Transfer - Einzelbuchung Spende (SEPA Purpose Code: CHAR) |
| 152 | SEPA Credit Transfer - Einzelbuchung Dauerauftrag |
| 153 | SEPA Credit Transfer - Einzelbuchung Haben, Lohn, Gehalt, Rentengutschrift |
| 154 | SEPA Credit Transfer - Einzelbuchung Haben, Vermögenswirksame Leistungen |
| 156 | SEPA Credit Transfer - Einzelbuchung Haben, Überweisung öffentlicher Kassen |
| 159 | SEPA Credit Transfer - Retoure Haben für einbringliche SEPA Überweisung |
| 160 | SEPA Credit Transfer Instant - Rücküberweisung (wegen Rückruf) |
| 166 | SEPA Credit Transfer - Einzelbuchung Haben |
| 168 | SEPA Credit Transfer Instant - Einzelbuchung Haben |
| 169 | SEPA Credit Transfer - Einzelbuchung Spende (SEPA Purpose Code: CHAR) |
| 177 | SEPA Credit Transfer - Online Einzelbuchung Soll |
| 188 | SEPA Credit Transfer Instant - Sammler Soll [Reserviert] |
| 189 | SEPA Credit Transfer Instant - Sammler Haben |
| 191 | SEPA Credit Transfer - Sammler Soll |
| 194 | SEPA Credit Transfer - Sammler Haben |

## 3. SEPA Verwendungszweck und strukturierte Informationen

Der SEPA Verwendungszweck enthält strukturierte Informationen mit folgenden Elementen:

| Kennung | Beschreibung |
|---------|--------------|
| IBAN+ | SEPA IBAN Auftraggeber |
| BIC+ | SEPA BIC Auftraggeber |
| EREF+ | SEPA End to End-Referenz |
| KREF+ | Kundenreferenz |
| MREF+ | SEPA Mandatsreferenz |
| CRED+ | SEPA Creditor Identifier |
| DEBT+ | Originator Identifier |
| COAM+ | Zinskompensationsbetrag |
| OAMT+ | Ursprünglicher Umsatzbetrag |
| SVWZ+ | SEPA Verwendungszweck |
| ABWA+ | Abweichender SEPA Auftraggeber |
| ABWE+ | Abweichender SEPA Empfänger |
| BREF+ | Bankreferenz, Instruction ID |
| RREF+ | Retourenreferenz |

## 4. Weitere Zahlungsverkehrsstandards und -begriffe

### PAIN-Format (Payment Initiation)
- **Funktion**: ISO 20022 Nachrichten für die Einreichung von Zahlungsaufträgen
- **Wichtige Formate**:
  - **PAIN.001**: Überweisungen
  - **PAIN.008**: Lastschriften

### PACS-Format (Payments Clearing and Settlement)
- **Funktion**: ISO 20022 Nachrichten für den Austausch von Zahlungsverkehrsinformationen zwischen Finanzinstituten
- **Wichtige Formate**:
  - **PACS.008**: Kundenüberweisungen
  - **PACS.009**: Banküberweisungen

### ISO 20022 Standard
- **Funktion**: Internationaler Standard für den elektronischen Datenaustausch zwischen Finanzinstituten
- **Format**: XML-basiert
- **Einsatzbereich**: SEPA-Zahlungsverkehr und internationaler Zahlungsverkehr

### EBICS (Electronic Banking Internet Communication Standard)
- **Funktion**: Übertragungsprotokoll für den sicheren Austausch von Zahlungsverkehrsdaten über das Internet
- **Entwicklung**: In Deutschland entwickelt
- **Einsatzbereich**: Zwischen Banken sowie zwischen Banken und Kunden
- **Spezifika**:
  - **Auftragsarten**: Spezifische Kennungen für Zahlungsauftragstypen (z.B. CCT für SEPA-Überweisungen)
  - **Return Codes**: Technische und fachliche Codes für Status oder Fehler bei der Verarbeitung

### FinTS (Financial Transaction Services)
- **Funktion**: Standard für den elektronischen Zahlungsverkehr
- **Entwicklung**: Deutsche Kreditwirtschaft (DK)
- **Einsatzbereich**: Kommunikation zwischen Kunden und Banken

## 5. Zusammenfassung der Entwicklung

1. **Historische Entwicklung**:
   - DTA → SEPA: Zahlungsaufträge
   - MT940 → CAMT: Kontoauszüge

2. **Moderne Standards**:
   - **XML-basierte Formate**: SEPA-XML, CAMT, PAIN, PACS
   - **Unterstützung des UTF-8 Zeichensatzes** für internationale Zeichen
   - **ISO 20022** als übergreifender Standard

3. **Kontinuität**:
   - GVC-Codes bleiben trotz neuer Formate relevant
   - Rückwärtskompatibilität für bestehende Systeme wird gewährleistet
