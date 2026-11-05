# Datenschutz-Prüfbericht hopps.cloud

> **Stand: September 2026.** Technisch-organisatorische Prüfung auf Basis einer
> Codebase-Inventur (Services `org`, `az-document-ai`, `zugferd`, Frontend, Infra).
> Keine Rechtsberatung; für die Freigabe der Dokumente juristische Prüfung empfohlen.

## 1. Verantwortlicher und Rollen

- **Verantwortlicher / Betreiber:** Open Project e.V., Birkengrund 22, 85276 Pfaffenhofen a.d. Ilm; Vorstand Manuel Hummler; info@hopps.app.
- **Doppelrolle:** Verantwortlicher für Website, Nutzerkonten, Nutzungs-/Protokolldaten; **Auftragsverarbeiter** (Art. 28) für Vereinsdaten (Mitglieder, Belege, Bank). Azure/OpenAI = Sub-Prozessoren.
- **DSB:** nicht bestellt (Pflicht via §38 BDSG/Art. 37 prüfen, insb. falls DSFA nötig).
- **Aufsicht:** BayLDA, Ansbach.

## 2. Speicherorte / Datenflüsse (alle bestätigt)

| Komponente | Anbieter | Ort |
|---|---|---|
| Cluster/Hosting | Hetzner | Deutschland (EU) |
| Objektspeicher (Belege, CSV, Logos) | DigitalOcean Spaces | Frankfurt fra1 (EU); US-Konzern |
| SMTP | ALL-INKL | Deutschland (EU) |
| Identität/Login | Keycloak (selbst betrieben) | Cluster (EU) |
| Datenbank | PostgreSQL/CNPG (selbst betrieben) | Cluster (EU) |
| KI-OCR | Azure AI Document Intelligence | West Europe (EU) |
| KI-Tagging | **OpenAI** (gpt-4o-mini) | **USA** ⚠️ |

**Kernbefund:** Nach Umstellung des OpenAI-Schritts auf Azure OpenAI (EU) verlässt
**kein produktiver personenbezogener Datensatz mehr die EU.**

## 3. Personenbezogene Daten (Kurzinventar → siehe RoPA)

Nutzerkonten (Keycloak + `member`), Aktivitätsdaten (`member_activity_day`,
`last_seen`, `impersonation_audit`), Organisation + Adresse, Belege/Dokumente (S3 +
`trade_party`), Transaktionen, Bankdaten (IBAN/SEPA in `BankAccount`/`BankTransaction`,
inkl. `rawRow` = komplette Roh-CSV-Zeile), Server-Logs.

## 4. Befunde und Maßnahmenplan

### P1 — vor produktivem Betrieb mit echten Vereinen

| # | Befund | Maßnahme |
|---|---|---|
| P1.1 | OpenAI-Tagging sendet Beleg-JSON (mit PII) in die USA (`api.openai.com`), in `az-document-ai` **und** `zugferd` | AVV/DPA + SCC abschließen **oder** (empfohlen) auf **Azure OpenAI EU** umstellen (`quarkus.langchain4j.openai.base-url` + Deployment-Name) |
| P1.2 | AVVs mit Sub-Prozessoren noch nicht durchgängig geschlossen | OpenAI- & DigitalOcean-DPA aktiv annehmen; Hetzner/All-Inkl-AVV; Microsoft-DPA ablegen (→ [Sub-Prozessoren.md](Sub-Prozessoren.md)) |
| P1.3 | Keine Betroffenenrechte umgesetzt: **kein Art.-17-Löschkonzept** (Org-Löschung nur Soft-Delete), **kein Art.-20-Export** | Lösch-/Export-Prozess definieren (technisch + organisatorisch); Verantwortung Anbieter vs. Verein klären |
| P1.4 | Impressum + Datenschutzerklärung fehlten | ✅ erstellt (hopps.app kanonisch), App verlinkt per Link-Modus |

### P2 — mittelfristig

| # | Befund | Maßnahme |
|---|---|---|
| P2.1 | `impersonation_audit`: E-Mails **unbegrenzt**, keine Löschung | Aufbewahrungsfrist + Zweck definieren, Pruning ergänzen |
| P2.2 | `member_activity_day` + `last_seen`: Verhaltens-/Aktivitätstracking | Zweck/Rechtsgrundlage/Frist (400 Tage) dokumentiert ✅ (in DSE); Erforderlichkeit prüfen |
| P2.3 | `BankTransaction.rawRow` speichert komplette Roh-CSV-Zeile (evtl. mehr PII als geparst) | Datensparsamkeit prüfen (rawRow nach Verarbeitung verwerfen/kürzen?) |
| P2.4 | 30-Tage-Löschung der Bank-Original-CSV nur als Code-Kommentar behauptet | **S3-Lifecycle-Regel auf dem DigitalOcean-Space verifizieren** ⚠️ |
| P2.5 | `ParameterHandler`-Log-Level auf DEBUG | in Prod auf PII-Leaks in Logs prüfen |

### P3 — Governance/Dokumentation

| # | Maßnahme |
|---|---|
| P3.1 | RoPA (Art. 30) pflegen → [RoPA.md](RoPA.md) |
| P3.2 | DSFA-Schwellenprüfung (Art. 35): KI + große Mengen Finanzdaten → ggf. DSFA erforderlich |
| P3.3 | AVV-Vorlage + elektronische Annahme für Vereine ausrollen → [AVV](AVV-Auftragsverarbeitung.md) |
| P3.4 | Incident-Prozess (Art. 33/34), TOM-Konkretisierung (Backup/Restore, Monitoring) |
| P3.5 | Datenschutz-Kontaktperson intern benennen; DSB-Pflicht abschließend bewerten |

## 5. Entlastende Feststellungen

- Keine Analytics-/Tracking-Bibliotheken im Frontend; keine Werbe-Cookies; nur
  funktionale `localStorage`-Nutzung (Sprache, Sidebar) → kein Consent-Banner nötig.
- Kein Live-Banking (kein PSD2/FinTS) — Bankdaten nur per manuellem Upload.
- Alle Speicherorte außer OpenAI liegen in der EU (Hetzner DE, DigitalOcean FfM,
  All-Inkl DE, Azure West Europe).
- Keine automatisierte Entscheidung mit Rechtswirkung (Art. 22): KI liefert nur Vorschläge.
