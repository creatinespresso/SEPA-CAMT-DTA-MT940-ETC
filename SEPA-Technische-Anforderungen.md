# Kapitel 1: Einleitung

Die grundsätzlichen, allgemein gültigen technischen Anforderungen an SEPA sind dem Artikel 5 der EU-Verordnung Nr. 260/2012 zu entnehmen.

# Kapitel 2: SEPA Rulebooks XML Formate

Die Spezifikationen der für SEPA verwendbaren Nachrichten werden vom European Payments Council (EPC) definiert.

- Bereits 2007 begann SWIFT mit den ersten Umstellungen von MT-Nachrichtenformaten auf XML-Definitionen, die auf dem ISO 20022 Standard basieren.
- Zusätzlich existieren Vorgaben der Euro Banking Association und der Deutschen Bundesbank, um Zahlungsverkehrstransaktionen in deren Systemen im SEPA XML Format (z. B. Universal Financial Industry Message Scheme Standard, UNIFI Standard ISO 20022) abzuwickeln.

# Kapitel 3: SEPA Technische Anforderungen und Scheme Management Internal Rules

Im Rahmen der Verfahrensbeschreibungen für SEPA-Überweisungen und SEPA-Lastschriften (Basislastschriftverfahren, Firmenlastschriftverfahren) wird der Prozess der alle zwei Jahre durchzuführenden Regelwerksänderungen transparent dargelegt. Die vom European Payments Council (EPC) vorgeschlagenen Änderungen werden in den „Scheme Management Internal Rules“ dokumentiert. Dabei werden die Nutzer der SEPA-Verfahren aktiv in die Konsultationsprozesse einbezogen.

# Kapitel 4: Spezifische Angaben für SEPA Transaktionen

## Grundlegende Pflichtangaben

- **Zahlungsempfänger:** Name und IBAN-Code
- **Zahler:** Name und IBAN-Code
- **Zahlungsdienstleister:** BIC des Zahlers und BIC des Zahlungsempfängers

## Zusätzliche Angaben

### Für SEPA-Überweisung

- Überweisungsbetrag
- Identifikationscode der Zahlungsregelung
- Verrechnungsdatum der Überweisung

### Für SEPA-Lastschrift

- Lastschriftbetrag
- Identifikationsnummer des Zahlungsempfängers
- Fälligkeitstermin der Lastschrift
- Art der Lastschrift (Erst-, Einmal- oder Folgelastschrift)
- Einmalige SEPA-Mandatsreferenz
- Bestandteile des entmaterialisierten Mandats
- Datum der ersten Unterzeichnung des Mandats

# Kapitel 5: SEPA Verordnung und End-to-End Regulierung

Die SEPA-Verordnung legt wichtige Anforderungen (Datenelemente eines Zahlungsauftrages) fest, die von den SEPA-Verfahren erfüllt werden müssen. Sobald die Daten in elektronischer Form vorliegen, muss die Zahlung vollautomatisch von allen Beteiligten verarbeitet werden – ohne erneute Dateneingabe oder manuelle Eingriffe (sogenannte End-to-End Regulierung).

- **Durchgängigkeit:** Es wird kein Datenverlust akzeptiert. Referenzen müssen im gesamten SEPA-Zahlungsverkehr lückenlos weitergegeben werden.
- **Automatisierung:** Der gesamte Zahlungsprozess muss elektronisch abgewickelt werden.
- **Umwandlungsverbot:** Aufgrund des End-to-End Ansatzes ist es der Deutschen Bundesbank untersagt, Dateien zur Umwandlung in SEPA-Formate entgegenzunehmen.
- **Nachrichtenstandards:** Von den vollständigen ISO-Nachrichten werden nur jene Datenelemente verwendet, die für SEPA notwendig sind. So werden unnötige Elemente, wie z. B. die US-amerikanische Sozialversicherungsnummer, ausgeklammert.

# Kapitel 6: SEPA Attribute gemäß SEPA Implementation Guidelines

Die folgenden Attribute definieren die Datenelemente für SEPA-Nachrichten. Dabei gibt es unterschiedliche Listen für SEPA-Überweisungen (SCT) und SEPA-Lastschriften (SDD).

## SEPA-Überweisung (SCT)

- **AT-01:** Account Number of the Originator (Debtor Account)
- **AT-02:** Name of the Originator (Name)
- **AT-03:** Address of the Originator (Postal Address)
- **AT-04:** Amount of the Credit Transfer in Euro (Interbank Settlement Amount)
- **AT-05:** Remittance Information (Remittance Information)
- **AT-06:** BIC of the Originator Bank (Debtor Agent)
- **AT-07:** Requested Execution Date of the Instruction (Requested Execution Date)
- **AT-08:** Name of the Originator Reference Party (Name)
- **AT-09:** Identification Code of the Originator Reference Party (Identification)
- **AT-10:** Originator’s Identification Code (Identification)
- **AT-20:** Account of the Beneficiary (Creditor Account)
- **AT-21:** Name of the Beneficiary (Name)
- **AT-22:** Address of the Beneficiary (Postal Address)
- **AT-23:** BIC of the Beneficiary Bank (Creditor Agent)
- **AT-24:** Beneficiary Identification Code (Identification)
- **AT-28:** Name of the Beneficiary Reference Party (Name)
- **AT-29:** Identification Code of the Beneficiary Reference Party (Identification)
- **AT-40:** Identification Code of the Scheme (Payment Type Information)
- **AT-41:** Originator’s Reference to the Credit Transfer (End-to-End Identification)
- **AT-42:** Settlement Date of the Credit Transfer (Interbank Settlement Date)
- **AT-43:** Originator Bank’s Reference (Transaction Identification)
- **AT-44:** Purpose of the Credit Transfer (Purpose)
- **AT-45:** Category Purpose of the Credit Transfer (Payment Type Information)
- **AT-R2:** Identification of the Type of Party Initiating the R-Message (Return Originator)
- **AT-R3:** Reason Code for Non-Acceptance (Return Reason)
- **AT-R4:** Settlement Date for the Return (Interbank Settlement Date)
- **AT-R5:** Specific Reference of the Bank Initiating the Return/Refund (Return Identification)

## SEPA-Lastschrift (SDD)

- **AT-01:** The Unique Mandate Reference (Mandate Identification)
- **AT-02:** Identifier of the Creditor (Creditor Scheme Identification)
- **AT-03:** Name of the Creditor (Creditor / Name)
- **AT-04:** IBAN of the Creditor Account (Creditor Account)
- **AT-05:** Address of the Creditor (Creditor / Postal Address)
- **AT-06:** Amount of the Collection in Euro (Interbank Settlement Amount)
- **AT-07:** IBAN of the Debtor Account (Debtor Account)
- **AT-09:** Address of the Debtor (Debtor / Postal Address)
- **AT-10:** Creditor’s Reference of the Collection (End-to-End Identification)
- **AT-11:** Due Date of the Collection (Requested Collection Date)
- **AT-12:** BIC Code of the Creditor Bank (Creditor Agent)
- **AT-13:** BIC Code of the Debtor Bank (Debtor Agent)
- **AT-14:** Name of the Debtor (Debtor / Name)
- **AT-15:** Debtor Identification (Ultimate Debtor)
- **AT-16:** Placeholder for the Electronic Signature (Electronic Signature)
- **AT-17:** Type of Mandate (bei Core Scheme immer „paper“) (Electronic Signature)
- **AT-18:** Identifier of the Original Creditor who Issued the Mandate (Original Creditor Scheme Identification)
- **AT-19:** Unique Mandate Reference as Given by the Original Creditor (Original Mandate Identification)
- **AT-20:** Identification Code of the Scheme (Payment Type Information/Local Instrument/Code)
- **AT-21:** Transaction Type (recurrent, one-off, first, last) (Sequence Type)
- **AT-22:** Remittance Information from the Creditor (Remittance Information)
- **AT-24:** Reason for Amendment of the Mandate (Amendment Information Details)
- **AT-25:** Date of Signing of the Mandate (Date Of Signature)
- **AT-26:** Settlement Date of the Collection (Interbank Settlement Date)
- **AT-27:** Debtor Identification Code (Debtor / Identification)
- **AT-37:** Identification Code of the Debtor Reference Party (Ultimate Debtor/Identification)
- **AT-38:** Name of the Creditor Reference Party (Ultimate Creditor / Name)
- **AT-39:** Identification Code of the Creditor Reference Party (Ultimate Creditor / Identifikation)
- **AT-43:** Creditor Bank’s Reference of the Collection (Transaction Identification)
- **AT-58:** Purpose of the Collection (Purpose)
- **AT-59:** Category Purpose of the Collection (Category Purpose)
- **AT-60:** Reference of the Validation Made by the Debtor Bank (Electronic Signature)
- **AT-R2:** Identification of the Type of Party Initiating the R-Message (Return Originator)
- **AT-R3:** Reason Code for Non-Acceptance (Return Reason)
- **AT-R4:** Settlement Date for the Return (Interbank Settlement Date)
- **AT-R5:** Specific Reference of the Bank Initiating the Return/Refund (Return Identification)
- **AT-R6:** Refund Compensation Recovered by the Debtor Bank from the Creditor Bank (Compensation Amount)
- **AT-R8:** Amount of the Balancing Payment Agreed Between the Debtor Bank and the Creditor Bank (Charges Information/Amount)

# Kapitel 7: Spezifikation der SEPA Datenformate und Technische Anforderungen gem. Artikel 5

Auszug aus Artikel 5 der EU-Verordnung Nr. 260/2012:

## Allgemeine Anforderungen

- Zahlungsdienstleister und Zahlungsdienstnutzer müssen für die Identifikation von Zahlungskonten den IBAN-Code verwenden.
- XML-Nachrichtenformate auf Basis des ISO 20022 Standards sind bei der Übermittlung von Zahlungsvorgängen zu verwenden.
- Im Datenfeld „Verwendungszweck“ können bis zu 140 Zeichen erfasst werden.
- Alle Zahlungsangaben und weiteren Datenelemente werden zwischen den Zahlungsdienstleistern in der gesamten Zahlungskette vollständig und unverändert weitergegeben.
- Sobald Daten in elektronischer Form vorliegen, muss eine vollautomatische, elektronische Verarbeitung aller Prozessstadien möglich sein – ohne erneute Dateneingabe oder manuelle Eingriffe.
- Es werden keine Mindestbeträge für Zahlungsvorgänge vorgegeben.
- Zahlungsregelungen sind nicht verpflichtet, Überweisungen und Lastschriften über einen Betrag von 999.999.999,99 EUR auszuführen.

## Zusätzliche Technische Anforderungen ausschließlich für SEPA-Überweisungen

- Ein Zahlungsempfänger, der Überweisungen annimmt, teilt den Zahlern bei jedem Überweisungsersuchen seine IBAN und die BIC seines Zahlungsdienstleisters mit.
- Der Zahler übermittelt seinem Zahlungsdienstleister folgende obligatorische Datenelemente:
  1. Name des Zahlers und/oder IBAN-Code des Zahlers
  2. Überweisungsbetrag
  3. IBAN-Code des Zahlungsempfängers
  4. Name des Zahlungsempfängers
  5. Gegebenenfalls Transferangaben
- Der Zahlungsdienstleister des Zahlers stellt dem Zahlungsdienstleister des Zahlungsempfängers folgende Daten zur Verfügung:
  1. BIC des Zahlungsdienstleisters des Zahlers (sofern nicht anders vereinbart)
  2. BIC des Zahlungsdienstleisters des Zahlungsempfängers (sofern nicht anders vereinbart)
  3. Identifikationscode der Zahlungsregelung
  4. Verrechnungsdatum der Überweisung
  5. Referenznummer aus der Überweisungsnachricht

## Zusätzliche Technische Anforderungen ausschließlich für SEPA-Lastschriften

- Vor der ersten Lastschrift teilt der Zahler dem Zahlungsempfänger seine IBAN und, sofern relevant, die BIC seines Zahlungsdienstleisters mit.
- Mit der ersten Lastschrift sowie bei jeder folgenden Lastschrift werden die Mandatsangaben vom Zahlungsdienstleister übermittelt.
- Der Zahlungsdienstleister des Zahlungsempfängers leitet diese Mandatsangaben bei jeder Lastschrift an den Zahler weiter.
- Zahler können Anweisungen erteilen, Lastschrifteinzüge auf einen bestimmten Betrag oder eine bestimmte Periodizität zu begrenzen.
- Besteht zwischen Zahler und Zahlungsempfänger eine Vereinbarung, die ein Rückerstattungsrecht ausschließt, prüft der Zahlungsdienstleister jede Lastschrift anhand der Mandatsangaben vor Belastung des Kontos des Zahlers.
- Der Zahler kann zudem Anweisungen zur Blockierung sämtlicher Lastschriften oder nur der von bestimmten Zahlungsempfängern erteilten Lastschriften geben.
- Die Zustimmung zur Anweisung wird sowohl dem Zahlungsempfänger als auch dem Zahlungsdienstleister des Zahlers erteilt, und das Mandat wird – zusammen mit späteren Änderungen oder der Annullierung – aufbewahrt.

---

*Quelle: SEPA Technische Anforderungen – SEPA Rulebooks XML Formate – Hettwer UnternehmensBeratung GmbH*
