# Auftragsverarbeitungsvertrag (AVV) nach Art. 28 DSGVO

> **ENTWURF – Stand September 2026.** Vorlage für den Vertrag zwischen einem Verein
> (Verantwortlicher) und dem Betreiber von hopps (Auftragsverarbeiter). Vor
> Verwendung juristisch prüfen lassen. Vorgesehene Annahme: elektronisch bei der
> Registrierung (Checkbox „AVV akzeptieren" als Bestandteil der Nutzungsbedingungen).

## Parteien

- **Verantwortlicher** („Kunde"): der Verein bzw. die Organisation, die hopps nutzt (Angaben aus der Registrierung).
- **Auftragsverarbeiter** („Anbieter"):
  Open Project e.V., Birkengrund 22, 85276 Pfaffenhofen an der Ilm,
  vertreten durch den Vorstand Manuel Hummler, info@hopps.app.

## § 1 Gegenstand und Dauer

(1) Gegenstand ist die Verarbeitung personenbezogener Daten durch den Anbieter im
Auftrag des Kunden im Rahmen der Bereitstellung der Buchhaltungsanwendung hopps
(Beleg- und Belegerkennung, Transaktions- und Bankdatenverwaltung, Mitglieder-/
Kontenverwaltung, Auswertungen).

(2) Die Dauer entspricht der Laufzeit des Nutzungsverhältnisses. Der Vertrag endet
mit dessen Beendigung; die Regelungen zu Löschung/Rückgabe (§ 7) bleiben anwendbar.

## § 2 Art, Zweck, Datenkategorien und betroffene Personen

**Zweck:** Erbringung der vertraglich vereinbarten Buchhaltungsfunktionen für den Kunden.

**Art der Verarbeitung:** Erheben, Erfassen, Speichern, Auslesen, Auswerten (inkl.
KI-gestützter Belegerkennung), Abgleichen, Löschen.

**Kategorien personenbezogener Daten:**
- Stammdaten der Nutzer/Mitglieder (Name, E-Mail, Funktion, Zugangsdaten)
- Beleg-/Rechnungsdaten inkl. Angaben zu Geschäftspartnern (Name, Anschrift, Steuer-/USt-Nummern, Beträge)
- Bank- und Zahlungsdaten (IBAN, BIC, Kontoinhaber, Verwendungszweck, SEPA-Mandats-/Gläubigerangaben)
- Nutzungs-/Protokolldaten

**Kategorien betroffener Personen:** Mitglieder und handelnde Personen des Vereins,
Geschäftspartner und sonstige auf Belegen genannte Dritte.

## § 3 Weisungsrecht

(1) Der Anbieter verarbeitet die Daten ausschließlich auf dokumentierte Weisung des
Kunden. Die Nutzung der Anwendung gemäß ihrer Funktionen gilt als Weisung; darüber
hinausgehende Weisungen erfolgen in Textform an info@hopps.app.

(2) Hält der Anbieter eine Weisung für rechtswidrig, teilt er dies dem Kunden mit und
darf die Ausführung aussetzen.

## § 4 Pflichten des Anbieters

(1) **Vertraulichkeit:** Zur Verarbeitung eingesetzte Personen sind zur Vertraulichkeit
verpflichtet (Art. 28 Abs. 3 lit. b, Art. 29, 32 Abs. 4 DSGVO).

(2) **Datensicherheit:** Der Anbieter trifft die technischen und organisatorischen
Maßnahmen nach Art. 32 DSGVO gemäß **Anlage 1**.

(3) **Unterstützung:** Der Anbieter unterstützt den Kunden im Rahmen des Möglichen bei
der Beantwortung von Betroffenenanfragen (Art. 15–22) sowie bei Datenschutz-Folgen­
abschätzungen und Meldepflichten (Art. 32–36).

(4) **Meldung von Verletzungen:** Der Anbieter informiert den Kunden unverzüglich nach
Kenntnis von einer Verletzung des Schutzes personenbezogener Daten.

(5) **Nachweise/Kontrollen:** Der Anbieter stellt dem Kunden die zur Einhaltung des
Art. 28 erforderlichen Informationen bereit und ermöglicht Überprüfungen (z. B. durch
Auskünfte, Nachweise oder – nach Vereinbarung – Inspektionen).

## § 5 Unterauftragsverarbeiter (Sub-Verarbeiter)

(1) Der Kunde erteilt seine **allgemeine Genehmigung** zur Beauftragung der in
**Anlage 2** genannten Unterauftragsverarbeiter.

(2) Der Anbieter informiert den Kunden über beabsichtigte Änderungen (Hinzuziehung/
Ersetzung) mit einer Frist von **mindestens einem Monat** vorab. Der Kunde kann aus
wichtigem, datenschutzrechtlichem Grund innerhalb dieser Frist widersprechen; kann
keine Lösung gefunden werden, besteht ein Sonderkündigungsrecht.

(3) Der Anbieter verpflichtet jeden Unterauftragsverarbeiter auf gleichwertige
Datenschutzpflichten (Art. 28 Abs. 4 DSGVO).

## § 6 Drittlandübermittlung

Eine Übermittlung in ein Drittland erfolgt nur, soweit in **Anlage 2** ausgewiesen, und
auf Grundlage geeigneter Garantien nach Art. 44 ff. DSGVO (insbesondere EU-Standard­
vertragsklauseln). Der aktuelle Stand ergibt sich aus Anlage 2.

## § 7 Löschung und Rückgabe

Nach Beendigung löscht der Anbieter die Daten oder gibt sie – nach Wahl des Kunden –
zurück, sofern keine gesetzliche Aufbewahrungspflicht entgegensteht. Handels- und
steuerrechtliche Aufbewahrungspflichten für Buchhaltungsunterlagen treffen den Kunden.

## § 8 Schlussbestimmungen

Es gilt deutsches Recht. Bei Widersprüchen zwischen diesem AVV und sonstigen
Vereinbarungen gehen die Regelungen dieses AVV in Datenschutzfragen vor.

---

## Anlage 1 – Technische und organisatorische Maßnahmen (Art. 32 DSGVO)

- **Verschlüsselung:** TLS/HTTPS für alle Übertragungen; Passwörter nur als Hash gespeichert.
- **Zugangs-/Zugriffskontrolle:** Authentifizierung über Keycloak (OIDC), rollenbasierte
  Rechte; Administrationszugriffe (Impersonation) werden protokolliert.
- **Mandantentrennung:** Datentrennung je Organisation innerhalb der Anwendung.
- **Hosting:** Rechenzentren in Deutschland (Hetzner); Objektspeicher in Frankfurt (EU).
- **Verfügbarkeit/Wiederherstellung:** regelmäßige Datensicherung der Datenbank und des
  Objektspeichers. *(Backup-/Restore-Konzept konkretisieren.)*
- **Belastbarkeit:** Betrieb auf Kubernetes mit TLS-Terminierung über Traefik.
- **Datenminimierung/Löschung:** automatische Löschung importierter Bank-Originaldateien
  nach kurzer Frist; Löschung der täglichen Nutzungsdauer nach 400 Tagen.

> *To-do: TOM vor Freigabe mit dem tatsächlichen Betriebsstand abgleichen
> (Backup-Fristen, Zugriffskonzept, Monitoring, Incident-Prozess).*

## Anlage 2 – Unterauftragsverarbeiter

Siehe [Sub-Prozessoren.md](Sub-Prozessoren.md). Diese Liste ist Bestandteil des AVV.
