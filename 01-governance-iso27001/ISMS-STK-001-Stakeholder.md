# ISMS-STK-001: Kontext der Organisation & Stakeholder-Matrix

| Dokumenten-ID | Version | Status | Klassifizierung | Geltungsbereich |
| :--- | :--- | :--- | :--- | :--- |
| ISMS-STK-001 | 1.0 | Freigegeben | Intern | SKY-Rhein Logistik GmbH |

---

## 1. Zweck & Kontext (ISO/IEC 27001:2022 Klausel 4.1)
Die **SKY-Rhein Logistik GmbH** betreibt Just-in-Time (JIT) Kontraktlogistik und temperaturgeführte Kühlkettentransporte im Rhein-Ruhr-Gebiet (Standorte: Düsseldorf, Köln, Duisburg) mit einer Flotte von 42 vernetzten Nutzfahrzeugen.
Dieses Dokument bestimmt die externen und internen Themen sowie die Anforderungen interessierter Parteien gemäß ISO/IEC 27001:2022 (Klausel 4.1 und 4.2) und NIS-2 (Sektor Transport/Logistik).

## 2. Stakeholder-Matrix (Klausel 4.2)

| Interessierte Partei | Kategorie | Anforderungen / Erwartungen | Gesetzliche / Vertragliche Basis | Technische Umsetzung (M365 / Entra) |
| :--- | :--- | :--- | :--- | :--- |
| **BSI / NIS-2 Behörden** | Regulatorisch | Meldepflicht von Sicherheitsvorfällen innerhalb von 24h; Nachweis von Risikomanagementmaßnahmen | NIS-2-Umsetzungsgesetz, BSIG | Unified Audit Log (Exchange/Entra) aktiv; Purview Audit Retention; Sentinel Alerting |
| **Automobil-Kunden (OEMs)** | Kunde / Vertrag | Unterbrechungsfreie JIT-Lieferkette; RTO < 2 Stunden; Line-Stop-Pönale (50.000 €/Std.) | SLA-Verträge; VDA ISA / TISAX | Conditional Access; MFA-Pflicht; Device Compliance; Geoblocking |
| **Kühlketten-Pharma-Kunden** | Kunde / Vertrag | Unveränderbare Telemetrie- und Temperaturdatenprotokolle; Schutz sensibler Lieferdaten | GDP (Good Distribution Practice); DIN EN 12830 | Purview Data Loss Prevention (DLP); Sensitivity Labels ("Streng Vertraulich") |
| **Landesbeauftragte für Datenschutz NRW** | Regulatorisch | Schutz personenbezogener Mitarbeiter- und Fahrerdaten; Auftragsverarbeitungskontrolle | DSGVO (Art. 32 TOMs) | Microsoft Purview DLP (PII-Schutz); Verschlüsselung via BitLocker & MAM |
| **Fahrer & Logistikpersonal** | Intern | Reibungslose Authentifizierung auf mobilen Endgeräten; Schutz privater Gerätedaten | Betriebsvereinbarung IT-Nutzung | Intune Mobile Application Management (MAM); Entra Smart Lockout |

## 3. Technische Umsetzung & Nachweisführung (Audit Evidence)
Zur Erfüllung von **Control A.8.15 (Protokollierung)** wurde das Microsoft 365 Unified Audit Logging mandantenweit via PowerShell forciert aktiviert[cite: 1]:
* **Cmdlet:** `Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true`[cite: 1]
* **Verifikationsnachweis:** `06-audit-evidence-pack/technical-screenshots/w01-powershell-auditlog-enabled.png`[cite: 1]
* **Mandant:** `SKYRheinLogistikGmbH.onmicrosoft.com`