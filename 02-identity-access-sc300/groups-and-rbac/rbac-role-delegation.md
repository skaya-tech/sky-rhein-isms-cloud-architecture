# Rollenbasierte Zugriffskontrolle (RBAC) & Rollendelegation

| Dokumenten-ID | Version | Status | Klassifizierung | ISO 27001:2022 Control |
| :--- | :--- | :--- | :--- | :--- |
| ISMS-RBAC-001 | 1.0 | Freigegeben | Intern | A.5.15, A.5.18 |

---

## 1. Zweck & Prinzip der geringsten Rechte (Least Privilege)
Dieses Dokument regelt die administrative Rollenverteilung innerhalb des Microsoft 365 Mandanten `SKYRheinLogistikGmbH.onmicrosoft.com`. Um das Sicherheitsrisiko durch privilegierte Identitäten zu minimieren, werden administrative Befugnisse dezentral und rollenspezifisch vergeben.

## 2. Implementierte Rollenzuweisungen (Status: H1 2026)

| Benutzer / Gruppe | Zugewiesene Rolle | Zuweisungsmethode | Sicherheitsbereich / Zweck |
| :--- | :--- | :--- | :--- |
| **Jan Richter** (`jrichter`) | Rechnungsadministrator (Billing Administrator) | Direkt via M365 Admin Center | Lizenzprüfung, Rechnungsabruf, Finanzberichte |
| **de-role-usermanagement** | Benutzeradministrator (User Administrator) | Rollenfähige Entra-Gruppe | Verwaltung von Benutzerkonten, Gruppen und Passwörtern |
| ↳ **Michael Weber** (`mweber`) | *Geerbt über Gruppe* | Gruppenmitgliedschaft | Dezentrale Benutzerverwaltung (IT-Operations) |
| **Frank Becker** (`fbecker`) | Dienst-Supportadministrator (Service Support Admin) | Direkt via Microsoft Graph PowerShell | Öffnen von Microsoft-Supportanfragen und Dienstüberwachung |

## 3. Technische Nachweise (Audit Evidences)
* **Wiederherstellungsgrenzen:** `06-audit-evidence-pack/technical-screenshots/w03-powershell-group-restore.png`
* **RBAC-PowerShell-Zuweisung:** `06-audit-evidence-pack/technical-screenshots/w03-powershell-rbac-assignment.png`