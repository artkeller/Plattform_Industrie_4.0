# Compliance-Dokumentation für ZTA+KI 2026

## Zusammenfassung

Dieses Verzeichnis `/ZTA+KI_2026/Compliance/V2` enthält die **erweiterte, QA-gesicherte und auditfähigere Version 2** der Compliance-Dokumente für eine Zero Trust Architektur (ZTA) mit KI-Assistenz im Industrie-4.0-Kontext. 

Im Vergleich zur V1 (im Parent-Ordner) wurden die Inhalte stark operationalisiert: vollständige Sätze statt Stichpunkte, Evidenz-Nachweis-Spalten, detaillierte Rollen/RACI, Risiko-Matrizen, KPIs, Lifecycle-Abdeckung, Review-Prozesse und ein separates SoA-Dokument mit Mapping aller 38 ISO/IEC 42001 Annex-A-Controls. 

Die Dokumente sind für C-Level, Legal, CISO, Auditoren und Implementierer konzipiert und gewährleisten höhere Konformität mit EU AI Act, ISO/IEC 42001, NIST SP 800-207, IEC 62443 und ISO 27001. V2 dient als zertifizierbare Vorlage (nahe 10/10 Audit-Reife).

## File-Struktur

Die Dateien sind thematisch gegliedert:

- **Compliance / Governance**  
  - [Data-_und_AI-Governance.md](Data-_und_AI-Governance.md)

- **Policies**  
  - [Policy.md](Policy.md)

- **Modules ZTA 1–3**  
  - [Modul_ZTA_Teil_1.md](Modul_ZTA_Teil_1.md)  
  - [Modul_ZTA_Teil_2.md](Modul_ZTA_Teil_2.md)  
  - [Modul_ZTA_Teil_3.md](Modul_ZTA_Teil_3.md)

- **SoA (Statement of Applicability)**  
  - [SoA.md](SoA.md)

## Erklärung der einzelnen Files

### Data-_und_AI-Governance.md
Dieses Dokument stellt das erweiterte Data- und AI-Governance-Rahmenwerk dar (V2). Es richtet sich primär an Geschäftsführung, C-Level und Legal. Es umfasst Rahmenbedingungen (§1), Ziele (§2), Klassifizierung von KI-Systemen (§3), Rollen & RACI-Matrix (§4), menschliche Aufsicht mit Eskalationstriggers (§5), Risikomanagement mit Beispiel-Matrix (§6), vollständiges Controls-Mapping / SoA (§7), Monitoring/KPIs/Review (§8) sowie Anhänge. 

Im Vergleich zu V1 wurde es um formale RACI, Risiko-Matrix, KPIs, Review-Zyklus und detailliertes SoA-Mapping erweitert, um ISO 42001 Stage-1/2-Readiness zu erreichen.

### Policy.md
Dieses Dokument enthält die erweiterte Policy zum Einsatz von ZTA und KI in Industrie 4.0 (V2). Zielgruppe sind Fachabteilungen, OT-Security und CISO. Struktur: Rahmenbedingungen, Ziele/Grundsätze, Motivation, Zugriffssteuerung (Tabelle), Integrität/Datenprovenienz (Tabelle), Nachvollziehbarkeit/Transparenz (Tabelle), Sicherheit/Monitoring (Tabelle), Review/Aktualisierung mit KPIs (Tabelle). 

Ergänzungen zu V1: Tabellen mit vollständigen Sätzen, ZTA-Pillar-Mapping, Incident-Response-Abschnitt, KPIs und Lifecycle-Integration für höhere Operationalisierbarkeit.

### Modul_ZTA_Teil_1.md
Der erweiterte generische Anforderungskatalog für ZTA+KI (V2). Zielgruppe: Techniker, Evaluatoren, Auditoren. Enthält Risikoklassifizierung/Security Levels, Tabelle mit Anforderungen ZTA-01 bis ZTA-15 (erweitert um Automation, Resilienz, Analytics), Lifecycle-View, vollständiges SoA-Mapping (Annex A + IEC SRs) sowie Evidenz-Spalte. 

Im Vergleich zu V1 deutlich erweitert (mehr IDs, Evidenz, Mapping-Tiefe, Changelog).

### Modul_ZTA_Teil_2.md
Exemplarische Prüfschritte zur Verifizierung der Dynamischen Richtlinienanpassung – ausschließlich für Anforderung ZTA-01 (V2). Tabelle mit Prüfschritten (ZTA-01-001 bis -007), Beschreibung, erwartetem Ergebnis, Status, Referenz und neuer Evidenz-Spalte. Scope-Hinweis: Nur ZTA-01; weitere Anforderungen fehlen noch und müssen analog ergänzt werden.

### Modul_ZTA_Teil_3.md
Detaillierte attributbasierte Verifikation der Kontextdatenerfassung – ausschließlich für Prüfschritt ZTA-01-001 (V2). Tabelle mit Verifikationspunkten (ZTA-01-001-01 bis -07) für User-Identität, Geräteintegrität, Netzwerk, OT-Prozesszustand, Verhalten usw., inkl. Evidenz-Spalte. Scope-Hinweis: Nur ZTA-01-001; weitere Prüfschritte und Anforderungen fehlen und müssen ergänzt werden.



```mermaid

graph LR
    %% === Hauptknoten ===
    Katalog[Anforderungskatalog<br>Modul ZTA Teil 1]:::haupt

    %% === Haupt-Anforderungen ===
    subgraph "Hauptanforderungen"
        ZTA01((ZTA-01<br>Dynam. Richtlinien)):::aktuell
        ZTA02[ZTA-02<br>Identität & Zugriff]:::normal
        ZTA03[ZTA-03<br>Datenprovenienz]:::normal
        ZTA04[ZTA-04<br>Audit & Explain]:::normal
        ZTA05[ZTA-05<br>Human Oversight]:::normal
        ZTA06[ZTA-06<br>Micro-Segmentation]:::normal
        ZTA07[ZTA-07<br>Monitoring & Response]:::normal
        ZTA08[ZTA-08<br>Lifecycle Mgmt]:::normal
        ZTA09[ZTA-09<br>Sichere Kommunikation]:::normal
        ZTA10[ZTA-10<br>Just-in-Time Access]:::normal
        ZTA11[ZTA-11<br>Continuous Posture]:::normal
        ZTA12[ZTA-12<br>Automation & Orchest]:::normal
        ZTA13[ZTA-13<br>Daten-Schutz-Kern]:::normal
        ZTA14[ZTA-14<br>Sichtbarkeit & Analytics]:::normal
        ZTA15[ZTA-15<br>Resilienz & Recovery]:::normal
    end

    %% === Prüfschritte ZTA-01 ===
    subgraph "Prüfschritte ZTA-01"
        PS001((ZTA-01-001<br>Kontext-Erfassung)):::aktuell
        PS002[ZTA-01-002<br>Änderungstest]:::normal
        PS003[ZTA-01-003<br>Logs & Nachvollziehbarkeit]:::normal
        PS004[ZTA-01-004<br>Fail-safe Deny]:::normal
        PS005[ZTA-01-005<br>Performance unter Last]:::normal
        PS006[ZTA-01-006<br>KI-Anomalie-Integration]:::normal
        PS007[ZTA-01-007<br>End-to-End-Trace]:::normal
    end

    %% === Granulare Verifikationspunkte ===
    subgraph "Verifikationspunkte ZTA-01-001"
        VP01((ZTA-01-001-01<br>User-Identität)):::detail
        VP02((ZTA-01-001-02<br>Geräteintegrität)):::detail
        VP03((ZTA-01-001-03<br>Netzwerkkontext)):::detail
        VP04((ZTA-01-001-04<br>OT-Prozesszustand)):::detail
        VP05((ZTA-01-001-05<br>Verhaltensmuster / KI)):::detail
        VP06((ZTA-01-001-06<br>Daten-Integrität & TLS)):::detail
        VP07((ZTA-01-001-07<br>Vollständigkeit & Fail)):::detail
    end

    %% === Verbindungen ===
    Katalog --> ZTA01 & ZTA02 & ZTA03 & ZTA04 & ZTA05 & ZTA06 & ZTA07 & ZTA08 & ZTA09 & ZTA10 & ZTA11 & ZTA12 & ZTA13 & ZTA14 & ZTA15

    ZTA01 --> PS001 & PS002 & PS003 & PS004 & PS005 & PS006 & PS007

    PS001 --> VP01 & VP02 & VP03 & VP04 & VP05 & VP06 & VP07

    %% === Interaktive Klicks (öffnen Links in neuem Tab) ===
    click ZTA01 "https://github.com/artkeller/Plattform_Industrie_4.0/blob/main/ZTA%2BKI_2026/Compliance/V2/Modul_ZTA_Teil_1.md#zta-01" "ZTA-01 Details" _blank
    click PS001 "https://github.com/artkeller/Plattform_Industrie_4.0/blob/main/ZTA%2BKI_2026/Compliance/V2/Modul_ZTA_Teil_2.md#zta-01-001" "Prüfschritt ZTA-01-001" _blank
    click VP01 "https://github.com/artkeller/Plattform_Industrie_4.0/blob/main/ZTA%2BKI_2026/Compliance/V2/Modul_ZTA_Teil_3.md#zta-01-001-01" "User-Identität" _blank

    %% === Styling ===
    classDef haupt fill:#1e3a8a,stroke:#60a5fa,stroke-width:3px,color:#fff,font-weight:bold
    classDef aktuell fill:#b91c1c,stroke:#fecaca,stroke-width:3px,color:#fff
    classDef normal fill:#334155,stroke:#94a3b8,color:#e2e8f0
    classDef detail fill:#065f46,stroke:#6ee7b7,color:#fff
```

### SoA.md
Das eigenständige **Statement of Applicability** (V2) mit granularer Auflistung aller 38 Controls aus ISO/IEC 42001 Annex A sowie relevanter IEC 62443 SRs. Tabelle mit Control-ID, Titel/Beschreibung, Anwendung, Umsetzung/Referenz, Verantwortlichem, Status und Evidenz/Nachweis. 

Dieses Dokument fasst das Mapping zentral zusammen und dient als Kernstück für ISO-42001-Zertifizierung oder EU-AI-Act-Conformity-Assessment.
