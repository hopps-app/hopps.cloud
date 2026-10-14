# Unterauftragsverarbeiter (Sub-Prozessoren) von hopps

> **Stand: September 2026.** Anlage 2 zum [AVV](AVV-Auftragsverarbeitung.md) und
> Grundlage der öffentlichen Angaben in der Datenschutzerklärung. Bei Änderungen:
> Kunden mit ≥ 1 Monat Vorlauf informieren (§ 5 AVV) und diese Datei sowie die
> Datenschutzerklärung aktualisieren.

| # | Dienstleister | Sitz | Zweck | Ort der Verarbeitung | Garantie bei Drittland |
|---|---|---|---|---|---|
| 1 | Hetzner Online GmbH | Deutschland | Hosting, Serverbetrieb (Cluster) | Deutschland (EU) | – (EU) |
| 2 | DigitalOcean, LLC | USA | Objektspeicher „Spaces" für Belege/Uploads/Bank-CSV | Frankfurt a. M. (EU) | AVV + EU-Standardvertragsklauseln |
| 3 | ALL-INKL.COM – Neue Medien Münnich | Deutschland | E-Mail-Versand (SMTP): Einladungen, Passwort-Links | Deutschland (EU) | – (EU) |
| 4 | Microsoft Corporation / Microsoft Ireland | USA / Irland | KI-Belegerkennung (Azure AI Document Intelligence) | EU-Region „West Europe" | Microsoft DPA + EU-SCC |
| 5 | OpenAI, L.L.C. | USA | KI-Verschlagwortung von Belegen (gpt-4o-mini) | USA | OpenAI DPA + EU-SCC — **Umstellung auf Azure OpenAI (EU) geplant** |

## Status der Auftragsverarbeitungsverträge (intern)

| Dienstleister | AVV/DPA | Status | Aktion |
|---|---|---|---|
| Hetzner | Hetzner AVV | **prüfen/abschließen** | im Kundenkonto beauftragen/bestätigen |
| DigitalOcean | DigitalOcean DPA | **prüfen/abschließen** ⚠️ | DPA im Portal aktiv annehmen |
| ALL-INKL | AVV | **prüfen/abschließen** | AVV anfordern |
| Microsoft | Products & Services DPA | gilt automatisch über Azure-Vertrag | ablegen; ggf. EU Data Boundary aktivieren |
| OpenAI | OpenAI DPA | **offen** ⚠️ | DPA-Formular aktiv annehmen; Zero-Data-Retention prüfen — oder durch Migration auf Azure OpenAI ablösen |

## Anmerkungen

- Nach Umstellung der Verschlagwortung auf **Azure OpenAI (EU)** entfällt Zeile 5;
  der OpenAI-DPA wird nicht mehr benötigt, da Microsofts DPA greift (Zeile 4).
- Der Objektspeicher (Zeile 2) liegt physisch in der EU; die Einordnung als Drittland
  ergibt sich allein aus dem US-Sitz des Anbieters → SCC als Absicherung.
