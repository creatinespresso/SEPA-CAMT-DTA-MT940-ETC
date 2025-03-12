# EBICS Umstellung im Überblick

## Multibankfähigkeit
- Deutschland durch das DFÜ Abkommen sicher gestellt

## Kommunikationsweg
- HTTP(S), TCP/IP, IP Netze (insbesondere Internet, auch LAN)

## Sicherheit
- Verbesserungen durch mehr Signaturen als bisher:
  - Authentifikationssignatur
  - Unterschrift bei jeder Einreichung
- Doppelte Verschlüsselung zwingend:
  - ZKA Verschlüsselung
  - TLS (SSL) Verschlüsselung

## Infrastrukturkosten
- Kosten für Internetanschluss

## Bandbreite der Übertragung/Datenvolumen
- Kann beliebig erhöht werden, schnelle Internetverbindungen können genutzt werden
- ZIP Komprimierung ist Pflicht (verringert Datenvolumen, erhöht somit Geschwindigkeit)

## Unterschriftsversionen
- Elektronische Unterschrift erst ab A004 unterstützt

## Programmarchitektur
- Es können Client/Server Anwendungen genauso wie Applet Lösungen oder Thin Clients angebunden werden
- Die Kundenprodukte müssen jedoch an die speziellen Anforderungen des neuen Standards angepasst werden

## Stammdaten
- Die kundenseitigen Stammdaten (Auftraggeber und Empfängerdaten bzw. -konten, Währungen) sind weitestgehend unabhängig vom EBICS Verfahren
- Daher können die Stammdaten in einer Kundensystemversion, die EBICS unterstützt, weiterverwendet werden

## Datenformate
- Die bankfachlichen Datenformate (DTAUS, DTAZV, MT940 etc.) bleiben unverändert
- Daher brauchen kundenseitige Schnittstellen, die nichts Weiteres tun, als Inhalte für diese Formate anzuliefern, für EBICS nicht angepasst werden

## Senden von Dateien (Kunde an Bank)
- Über Auftragsarten, jedoch es muss jede gesendete Datei unterschrieben werden
- Entweder bankfachlich durch die Elektronische Unterschrift (Autorisierung) oder reiner Transport (Transportunterschrift)
- Jeder Teilnehmer hat eine bestimmte Unterschriftsklasse (Transport = "T")

## Abholen von Dateien (Bank an Kunden)
- Über Auftragsarten

## Anwendungsprotokoll
- XML Schnittstelle

## Anmerkung
- Änderungen im Abkommen über die Datenfernübertragung zwischen Kunden und Kreditinstituten zur Einführung des EBICS Standard
- Die im Zentralen Kreditausschuss (Deutsche Kreditwirtschaft) zusammengeschlossenen Spitzenverbände des Kreditgewerbes haben sich darauf verständigt, ab dem 1. Januar 2008 neben dem bisherigen FTAM Verfahren als neue Variante des DFÜ Verfahrens den Electronic Banking Internet Communication Standard (EBICS) anzubieten
- Die Verpflichtung, die bisherigen FTAM Anbindungen institutsseitig zu unterstützen lief zum 31. Dezember 2010 aus
- Seit dem 1. Januar 2011 ist die Nutzung von FTAM demnach nur noch nach bilateraler Abstimmung möglich
