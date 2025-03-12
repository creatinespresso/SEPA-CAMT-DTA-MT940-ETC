# SEPA CAMT.053 Spezifikation

## 1. Grundlegendes zum CAMT.053 Format

CAMT.053 (Bank To Customer Statement) ist ein XML-basiertes Format im SEPA-Zahlungsverkehr, das den elektronischen Kontoauszug zum Tagesende darstellt. Es ist der ISO 20022-konforme Nachfolger des MT940-Formats und Teil der Standardisierung im europäischen Zahlungsverkehr.

- **Format**: XML-basiert
- **Anwendung**: Tagesauszug, Interbankenauszug
- **Ersetzt**: MT940, MT950
- **Charakteristik**: Kontoauszug (von der Bank zum Kunden)

## 2. Hierarchischer Aufbau des CAMT.053 Formats

Die CAMT.053 Nachricht folgt einer hierarchischen Struktur:

1. **SEPA Wurzelelement**: `BkToCstmrStmt` (Bank to Customer Statement)
2. **Kontobezogene Elementgruppe**: `Stmt` (Statement)
3. **Umsatzbezogene Elementgruppe**: `Ntry` (Entry)
4. **Transaktionsbezogene Elementengruppe**: `NtryDtls` (Entry Details)
5. **Transaktionen Details**: `TxDtls` (Transaction Details)

## 3. XML-Struktur und wichtige Tags

### 3.1 Group Header (`<GrpHdr>`)

Der Group Header enthält grundlegende Informationen zu der Nachricht selbst:

```xml
<GrpHdr>
  <MsgId>CAMT053JJJJMMTT0000000000000001</MsgId>
  <CreDtTm>JJJJ-MM-TTT00:00:00.1+01:00</CreDtTm>
  <MsgRcpt>...</MsgRcpt>
  <MsgPgntn>
    <PgNb>1</PgNb>
    <LastPgInd>true</LastPgInd>
  </MsgPgntn>
</GrpHdr>
```

- `<MsgId>`: Eindeutige Nachrichtenidentifikation
- `<CreDtTm>`: Erstellungsdatum und -zeit der Nachricht (ISO DateTime Format: YYYY-MM-DDThh:mm:ss)
- `<MsgPgntn>`: Paginierungsinformationen für die Nachricht

### 3.2 Statement-Block (`<Stmt>`)

Der Statement-Block enthält die Kontoauszugsinformationen:

```xml
<Stmt>
  <Id>CAMT053999999999999999999</Id>
  <ElctrncSeqNb>1</ElctrncSeqNb>
  <CreDtTm>JJJJ-MM-TTT00:00:00.1+01:00</CreDtTm>
  <Acct>...</Acct>
  <Bal>...</Bal>
  <Ntry>...</Ntry>
</Stmt>
```

- `<Id>`: Identifikation des Kontoauszugs
- `<ElctrncSeqNb>`: Elektronische Sequenznummer
- `<CreDtTm>`: Erstellungszeitpunkt des Kontoauszugs

### 3.3 Account (`<Acct>`)

Der Account-Block enthält die Kontoinformationen:

```xml
<Acct>
  <Id><IBAN>DE99111111112222222222</IBAN></Id>
  <Tp><Prtry>CPD Konto</Prtry></Tp>
  <Ccy>EUR</Ccy>
  <Ownr><Nm>Kontoinhaber Name</Nm></Ownr>
  <Svcr>
    <FinInstnId>
      <BIC>AAAADEBBXXX</BIC>
      <Nm>NAME SEPA BANK</Nm>
    </FinInstnId>
  </Svcr>
</Acct>
```

- `<Id>`: Kontoidentifikation (IBAN)
- `<Ccy>`: Währung des Kontos
- `<Ownr>`: Kontoinhaber
- `<Svcr>`: Informationen zur kontoführenden Bank

### 3.4 Balance (`<Bal>`)

Der Balance-Block enthält die Saldeninformationen:

```xml
<Bal>
  <Tp><CdOrPrtry><Cd>PRCD</Cd></CdOrPrtry></Tp>
  <CdtLine><Incl>false</Incl></CdtLine>
  <Amt Ccy="EUR">1234567.89</Amt>
  <CdtDbtInd>DBIT</CdtDbtInd>
  <Dt><Dt>JJJJ-MM-TT</Dt></Dt>
</Bal>
```

- `<Tp>`: Art des Saldos 
  - `PRCD`: Previously Closed Booked (Eröffnungssaldo)
  - `CLBD`: Closing Booked (Schlusssaldo)
  - `CLAV`: Closing Available (Verfügbarer Schlusssaldo)
  - `FWAV`: Forward Available (Vorgemerkter Saldo)
- `<Amt>`: Betrag mit Währungsattribut
- `<CdtDbtInd>`: Soll/Haben-Indikator (DBIT = Soll, CRDT = Haben)
- `<Dt>`: Datum des Saldos

### 3.5 Entry (`<Ntry>`)

Der Entry-Block enthält Informationen zu einer Buchung:

```xml
<Ntry>
  <NtryRef>TTMMJJ0000000000123456748</NtryRef>
  <Amt Ccy="EUR">123.45</Amt>
  <CdtDbtInd>DBIT</CdtDbtInd>
  <Sts>BOOK</Sts>
  <BookgDt><Dt>JJJJ-MM-TT</Dt></BookgDt>
  <ValDt><Dt>JJJJ-MM-TT</Dt></ValDt>
  <AcctSvcrRef>9876543210</AcctSvcrRef>
  <BkTxCd>...</BkTxCd>
  <NtryDtls>...</NtryDtls>
  <AddtlNtryInf>SEPA UEBERWEISUNG</AddtlNtryInf>
</Ntry>
```

- `<NtryRef>`: Eindeutige Referenz der Buchung
- `<Amt>`: Betrag der Buchung
- `<CdtDbtInd>`: Soll/Haben-Indikator (DBIT = Soll, CRDT = Haben)
- `<Sts>`: Status der Buchung (BOOK = gebucht)
- `<BookgDt>`: Buchungsdatum
- `<ValDt>`: Wertstellungsdatum
- `<AcctSvcrRef>`: Referenz der kontoführenden Bank
- `<AddtlNtryInf>`: Zusätzliche Informationen zur Buchung

### 3.6 Transaktionsdetails (`<TxDtls>`)

Die Transaktionsdetails enthalten detaillierte Informationen zu einer Transaktion:

```xml
<TxDtls>
  <BkTxCd>
    <Prtry>
      <Cd>ABCD+000</Cd>
      <Issr>ZKA</Issr>
    </Prtry>
  </BkTxCd>
  <RltdPties>
    <Cdtr><Nm>Name SEPA Creditor</Nm></Cdtr>
    <CdtrAcct>
      <Id><Othr><Id>9999999999</Id></Othr></Id>
    </CdtrAcct>
  </RltdPties>
  <RltdAgts>...</RltdAgts>
  <RmtInf>
    <Ustrd>SEPA TEST SEPA Buchungen SEPA CAMT.053</Ustrd>
  </RmtInf>
</TxDtls>
```

- `<BkTxCd>`: Bank-Transaktionscode (GVC)
- `<RltdPties>`: Beteiligte Parteien (Zahler/Zahlungsempfänger)
- `<RltdAgts>`: Beteiligte Banken
- `<RmtInf>`: Verwendungszweck-Informationen
  - `<Ustrd>`: Unstrukturierter Verwendungszweck
  - `<Strd>`: Strukturierter Verwendungszweck (bei SEPA)

## 4. SEPA Geschäftsvorfallcodes (GVC) im CAMT.053

Die Geschäftsvorfallcodes werden im `<BkTxCd>` Element mitgeführt und dienen der standardisierten Kategorisierung von Transaktionen.

### 4.1 SEPA Direct Debit (Lastschrift) GVC-Codes

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

### 4.2 SEPA Credit Transfer (Überweisung) GVC-Codes

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

## 5. SEPA Verwendungszweck und strukturierte Informationen

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

## 6. Vollständiges CAMT.053 Beispiel

```xml
<?xml version="1.0" encoding="utf-8"?>
<Document>
  <BkToCstmrStmt>
    <GrpHdr>
      <MsgId>CAMT053JJJJMMTT0000000000000001</MsgId>
      <CreDtTm>JJJJ-MM-TTT00:00:00.1+01:00</CreDtTm>
      <MsgRcpt>
        <Id>
          <OrgId>
            <Othr>
              <Id>999999999</Id>
              <Issr>NAME BANK</Issr>
            </Othr>
          </OrgId>
        </Id>
      </MsgRcpt>
      <MsgPgntn>
        <PgNb>1</PgNb>
        <LastPgInd>true</LastPgInd>
      </MsgPgntn>
    </GrpHdr>
    <Stmt>
      <Id>CAMT053999999999999999999</Id>
      <ElctrncSeqNb>1</ElctrncSeqNb>
      <CreDtTm>JJJJ-MM-TTT00:00:00.1+01:00</CreDtTm>
      <Acct>
        <Id><IBAN>DE99111111112222222222</IBAN></Id>
        <Tp><Prtry>CPD Konto</Prtry></Tp>
        <Ccy>EUR</Ccy>
        <Ownr><Nm>Deutsche Bundesbank</Nm></Ownr>
        <Svcr>
          <FinInstnId>
            <BIC>AAAADEBBXXX</BIC>
            <Nm>NAME SEPA BANK</Nm>
            <Othr>
              <Id>DE1234567890</Id>
              <Issr>UmsStID</Issr>
            </Othr>
          </FinInstnId>
        </Svcr>
      </Acct>
      <Bal>
        <Tp><CdOrPrtry><Cd>PRCD</Cd></CdOrPrtry></Tp>
        <CdtLine><Incl>false</Incl></CdtLine>
        <Amt Ccy="EUR">1234567.89</Amt>
        <CdtDbtInd>DBIT</CdtDbtInd>
        <Dt><Dt>JJJJ-MM-TT</Dt></Dt>
      </Bal>
      <Bal>
        <Tp><CdOrPrtry><Cd>CLBD</Cd></CdOrPrtry></Tp>
        <CdtLine><Incl>false</Incl></CdtLine>
        <Amt Ccy="EUR">98765.45</Amt>
        <CdtDbtInd>DBIT</CdtDbtInd>
        <Dt><Dt>JJJJ-MM-TT</Dt></Dt>
      </Bal>
      <Ntry>
        <NtryRef>TTMMJJ0000000000123456748</NtryRef>
        <Amt Ccy="EUR">123.45</Amt>
        <CdtDbtInd>DBIT</CdtDbtInd>
        <Sts>BOOK</Sts>
        <BookgDt><Dt>JJJJ-MM-TT</Dt></BookgDt>
        <ValDt><Dt>JJJJ-MM-TT</Dt></ValDt>
        <AcctSvcrRef>9876543210</AcctSvcrRef>
        <NtryDtls>
          <TxDtls>
            <BkTxCd>
              <Prtry>
                <Cd>ABCD+000</Cd>
                <Issr>ZKA</Issr>
              </Prtry>
            </BkTxCd>
            <RltdPties>
              <Cdtr><Nm>Name SEPA Creditor</Nm></Cdtr>
              <CdtrAcct>
                <Id><Othr><Id>9999999999</Id></Othr></Id>
              </CdtrAcct>
            </RltdPties>
            <RltdAgts>
              <CdtrAgt>
                <FinInstnId>
                  <ClrSysMmbId>
                    <ClrSysId><Cd>AAAAA</Cd></ClrSysId>
                    <MmbId>00000000</MmbId>
                  </ClrSysMmbId>
                </FinInstnId>
              </CdtrAgt>
            </RltdAgts>
            <RmtInf>
              <Ustrd>SEPA TEST SEPA Buchungen SEPA CAMT.053</Ustrd>
            </RmtInf>
          </TxDtls>
        </NtryDtls>
        <AddtlNtryInf>SEPA UEBERWEISUNG</AddtlNtryInf>
      </Ntry>
    </Stmt>
  </BkToCstmrStmt>
</Document>
```

## 7. CAMT.053 im Kontext anderer SEPA-Formate

CAMT.053 ist Teil einer Familie von Kontoauszugs- und Zahlungsverkehrsformaten im SEPA-Raum:

### 7.1 CAMT-Formate (Cash Management)

- **CAMT.052**: Tagesaktuelle Kontoumsätze (Vormerkposten)
- **CAMT.053**: Elektronischer Kontoauszug (Ende des Tages, ersetzt MT940)
- **CAMT.054**: Einzeltransaktionsdaten (Detailinformationen zu Buchungen)
- **CAMT.029**: Negativantwort auf eine Zahlungsuntersuchung
- **CAMT.056**: Rückruf von Überweisungen bei Fehlern

### 7.2 PAIN-Formate (Payment Initiation)

- **PAIN.001**: Überweisungen (vom Kunden an die Bank)
- **PAIN.008**: Lastschriften (vom Kunden an die Bank)
- **PAIN.002**: Status Report (von der Bank zum Kunden)

### 7.3 PACS-Formate (Payments Clearing and Settlement)

- **PACS.008**: Kundenüberweisungen (zwischen Banken)
- **PACS.003**: Lastschriften (zwischen Banken)
- **PACS.004**: Rücklastschriften (zwischen Banken)
- **PACS.002**: Status Report (zwischen Banken)

## 8. Zusammenfassung

CAMT.053 ist das XML-basierte SEPA-Format für elektronische Kontoauszüge, das den bisherigen MT940-Standard ersetzt. Es bietet eine strukturierte Darstellung aller Kontobewegungen mit detaillierten Informationen zu Transaktionen, verwendeten Geschäftsvorfallcodes (GVC) und strukturierten Verwendungszwecken. Die hierarchische XML-Struktur ermöglicht eine automatisierte Verarbeitung und Integration in Buchhaltungs- und ERP-Systeme.
