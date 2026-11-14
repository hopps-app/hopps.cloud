# Verzeichnis von Verarbeitungstätigkeiten (Art. 30 DSGVO)

> **Stand: September 2026.** Open Project e.V. (Betreiber hopps.cloud). Umfasst
> Tätigkeiten als **Verantwortlicher** (Art. 30 Abs. 1) und als **Auftragsverarbeiter**
> (Art. 30 Abs. 2). Löschfristen mit dem tatsächlichen Betrieb abgleichen.

**Verantwortlicher:** Open Project e.V., Birkengrund 22, 85276 Pfaffenhofen a.d. Ilm; Vorstand Manuel Hummler; info@hopps.app.
**Empfänger/Sub-Prozessoren (alle Tätigkeiten):** siehe [Sub-Prozessoren.md](Sub-Prozessoren.md).
**Drittland:** nur OpenAI (USA), SCC; Umstellung auf Azure OpenAI (EU) geplant. Alle übrigen Verarbeitungen in der EU.

---

## Teil A — als Verantwortlicher (Art. 30 Abs. 1)

### A1 — Bereitstellung der Website / Server-Logs
- **Zweck:** Auslieferung, Sicherheit, Stabilität.
- **Betroffene:** Websitebesucher.
- **Daten:** IP-Adresse, Zeitpunkt, Request, Browser-/Systemangaben.
- **Rechtsgrundlage:** Art. 6 Abs. 1 lit. f.
- **Empfänger:** Hetzner (Hosting).
- **Löschfrist:** kurzfristig (Log-Rotation) — *konkretisieren*.

### A2 — Benutzerkonten / Authentifizierung
- **Zweck:** Konto, Anmeldung, Zugriffsschutz.
- **Betroffene:** handelnde Personen der Vereine (Vorstand, Kassenwart u. a.).
- **Daten:** Name, E-Mail, Passwort (Hash), Funktion, Status, `keycloakId`.
- **Rechtsgrundlage:** Art. 6 Abs. 1 lit. b.
- **Systeme:** Keycloak, `member`-Tabelle. Empfänger: All-Inkl (Einladungs-Mails).
- **Löschfrist:** mit Beendigung des Kontos (Löschkonzept P1.3 offen).

### A3 — Nutzungs-/Aktivitätsdaten und Support-Zugriffe
- **Zweck:** Sicherheit, Fehler-/Missbrauchserkennung, Nachvollziehbarkeit.
- **Betroffene:** Nutzer; Administratoren (bei Impersonation).
- **Daten:** `last_seen`, tägliche Nutzungsdauer (`member_activity_day`), `impersonation_audit` (Actor-/Target-E-Mail, IDs).
- **Rechtsgrundlage:** Art. 6 Abs. 1 lit. f.
- **Löschfrist:** Nutzungsdauer 400 Tage; **Impersonation-Log derzeit unbefristet → Frist definieren (P2.1)**.

---

## Teil B — als Auftragsverarbeiter (Art. 30 Abs. 2)

> Verantwortlicher ist jeweils der Verein. Grundlage: [AVV](AVV-Auftragsverarbeitung.md).

### B1 — Beleg-/Dokumentenverwaltung inkl. KI-Belegerkennung
- **Zweck:** Erfassung, Speicherung, automatisierte Auslesung und Verschlagwortung von Belegen.
- **Betroffene:** Geschäftspartner, Mitglieder, auf Belegen genannte Dritte.
- **Daten:** Beleg-Dateien (beliebige PII), `trade_party` (Name, Anschrift, Steuer-/USt-ID), Beträge; `uploadedBy/analyzedBy/reviewedBy`.
- **Empfänger/Sub-Prozessoren:** DigitalOcean (Objektspeicher, EU), Microsoft Azure Document Intelligence (EU), **OpenAI (USA, SCC)**.
- **Löschfrist:** nach Weisung des Vereins; handels-/steuerrechtliche Fristen (bis 10 Jahre) beim Verein.

### B2 — Transaktions- und Kontenverwaltung
- **Zweck:** Buchhaltung (Transaktionen, Kategorien, Kostenstellen/Bommel, Sphären).
- **Daten:** Beträge, Gegenparteien, `created_by`, Zuordnungen.
- **Empfänger:** DB (EU).
- **Rechtsgrundlage:** Auftrag des Vereins (Art. 28).

### B3 — Bank-CSV-Import und -Abgleich
- **Zweck:** Zahlungsabgleich.
- **Betroffene:** Kontoinhaber, Zahlungsgegenparteien.
- **Daten:** IBAN, BIC, Kontoinhaber, Verwendungszweck, SEPA-Mandat/Gläubiger-ID, `rawRow` (Roh-CSV), Original-CSV im Objektspeicher.
- **Empfänger:** DigitalOcean (EU).
- **Löschfrist:** Original-CSV kurzfristig (Lifecycle-Regel **verifizieren, P2.4**); Buchungsdaten nach Vereinsweisung.

### B4 — Mitglieder-/Organisationsstammdaten
- **Zweck:** Verwaltung der Organisation und Mitglieder.
- **Daten:** Organisation + Adresse, Mitglieder (Name, E-Mail, Funktion), verantwortliche Personen je Bommel.
- **Empfänger:** DB / Keycloak (EU).
- **Rechtsgrundlage:** Auftrag des Vereins (Art. 28).

---

**Technische/organisatorische Maßnahmen:** siehe [AVV](AVV-Auftragsverarbeitung.md), Anlage 1.
