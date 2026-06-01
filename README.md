# 3-Tier Todo-Anwendung auf OpenShift

Dieses Repository enthält die vollständige Infrastruktur-Konfiguration (Infrastructure as Code) für eine klassische 3-Schichten-Anwendung (Frontend, Backend, Datenbank) auf OpenShift.

## 📐 Architektur-Übersicht

Die Anwendung ist streng nach Abhängigkeiten von unten nach oben (Bottom-Up) aufgebaut:

1. **Persistent Volume Claim (PVC):** Sichert den permanenten Speicher für die Datenbank.
2. **PostgreSQL-Datenbank:** Nutzt das PVC und stellt den Datenspeicher bereit.
3. **Node.js-Backend:** Verarbeitet die Logik und kommuniziert intern mit der Datenbank.
4. **Nginx-Frontend & Route:** Liefert die Benutzeroberfläche aus und öffnet die App über eine Route nach außen.

---

## 📂 Ordnerstruktur

```text
.
└── k8s/
    ├── 01-pvc.yaml            # Schritt 1: Speicheranforderung
    ├── 02-database.yaml       # Schritt 2: PostgreSQL Deployment & Service
    ├── 03-backend.yaml        # Schritt 3: Node.js API Deployment & Service
    └── 04-frontend.yaml       # Schritt 4: Nginx Webserver & OpenShift Route
