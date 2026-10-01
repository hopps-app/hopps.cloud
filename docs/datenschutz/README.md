# Datenschutz-Dokumentation hopps.cloud

Zusammenstellung der Datenschutz-Unterlagen für hopps (Open Project e.V.).
Alle Dokumente sind **Entwürfe, Stand September 2026**, und vor Veröffentlichung/
Verwendung **juristisch zu prüfen**.

| Dokument | Inhalt |
|---|---|
| [Datenschutz-Pruefbericht.md](Datenschutz-Pruefbericht.md) | Befunde der Prüfung + Maßnahmenplan (P1/P2/P3) |
| [RoPA.md](RoPA.md) | Verzeichnis von Verarbeitungstätigkeiten (Art. 30) |
| [AVV-Auftragsverarbeitung.md](AVV-Auftragsverarbeitung.md) | Auftragsverarbeitungsvertrag für Vereine (Art. 28) inkl. TOM |
| [Sub-Prozessoren.md](Sub-Prozessoren.md) | Liste der Unterauftragsverarbeiter (Anlage 2 zum AVV) + AVV-Status |

**Öffentliche Rechtstexte** (nicht hier, sondern im Landing-Page-Repo, kanonisch auf hopps.app):
`landing-page/src/app/impressum/page.tsx` und `.../datenschutz/page.tsx`.
Die App (hopps.cloud) verlinkt per `HOPPS_IMPRINT_URL` / `HOPPS_PRIVACY_URL` dorthin.

## Wichtigste offene To-dos

1. **OpenAI-DPA** und **DigitalOcean-DPA** aktiv abschließen (P1.2).
2. **OpenAI → Azure OpenAI (EU)** umstellen — eigener Arbeitsschritt (P1.1); danach DSE-Abschnitt 9 aktualisieren.
3. **Betroffenenrechte** (Löschung Art. 17 / Export Art. 20) technisch/organisatorisch umsetzen (P1.3).
4. **30-Tage-Löschung** der Bank-CSV auf dem DigitalOcean-Space verifizieren (P2.4).
5. Rechtstexte + AVV **juristisch prüfen** lassen; Datenschutz-Kontaktperson/DSB-Frage klären.
