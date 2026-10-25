[readme_md.md](https://github.com/user-attachments/files/33927854/readme_md.md)
#  StockVision Enterprise Banking & AI Auto-Trader Engine v5.0

Ein hochmodernes, modulares Web-Dashboard für KI-gestütztes Autotrading, Risiko-Governance, Sandbox-Banking und Echtzeit-Marktanalysen.

![StockVision Enterprise](https://img.shields.io/badge/Version-5.0_Enterprise-2962FF?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Architecture](https://img.shields.io/badge/Architecture-Modular_Single_File-orange?style=for-the-badge)

---

##  Inhaltsverzeichnis

- [Features](#-features)
- [Projektstruktur](#-projektstruktur)
- [Schnellstart](#-schnellstart)
- [Architektur & Module](#-architektur--module)
- [Sicherheitskonzept (Card Sandbox)](#-sicherheitskonzept-card-sandbox)
- [WebSocket & Server Integration](#-websocket--server-integration)
- [Mitwirken & Beitragen](#-mitwirken--beitragen)
- [Lizenz](#-lizenz)

---

##  Features

###  1. Auth & Benutzerverwaltung (Modul `AuthManager`)
* **Session-Verwaltung:** Login / Registrierung mit Verschlüsselungs-Simulation und JWT-Token-Verwaltung.
* **Persistenz:** Automatische Speicherung des Sitzungsstatus in `localStorage`.

###  2. KI Autotrading & Governance Engine (Modul `AutoTrader`)
* **Unantastbare Reserve (Hard Limit):** Stoppt jeglichen Handel automatisch, wenn das Gesamtkapital das eingestellte Mindestlimit erreicht.
* **Dynamische Risikoklassen:** Konservativ, Ausgewogen und Aggressiv mit angepassten TP/SL-Verhältnissen.
* **Dual-KI Bestätigung:** Zweistufige Signalvalidierung vor Positionseröffnung.

###  3. Banking Sandbox & Gateway (Modul `BankingGateway`)
* **Card Isolation Protocol:** Strikte Trennung zwischen Bankkarte und Trading Vault. Die KI hat keinen Direktzugriff auf Karten- oder IBAN-Daten.
* **Transaktions-Ledger:** Vollständige Protokollierung von Ein- und Auszahlungen.

###  4. KI Signal Screener (Modul `AIScreener`)
* **Live-Scanner:** Durchsucht kontinuierlich Assets (Aktien, Crypto, FX) nach Chartmustern.
* **Manuelle Auslösung:** Direkte Handelsausführung aus der Signalübersicht.

###  5. Order Historie & Speicher-Engine (Modul `OrderHistory`)
* **Lückenlose Aufzeichnung:** Speicherung aller geschlossenen Trades (Gewinn/Verlust, Ausstiegsparameter).
* **Persistenter Speicher:** Alle Daten bleiben auch nach dem Neuladen der Seite erhalten.

---

##  Projektstruktur

Für GitHub ist das Projekt so konzipiert, dass das gesamte System nahtlos ohne komplexe Build-Schritte direkt über **GitHub Pages** oder einen Standard-Webserver ausgeführt werden kann:

```text
stockvision-enterprise/
├── index.html              # Haupt-Anwendungsdatei (HTML5 + Tailwind CSS + JS Modules)
├── README.md               # Projektdokumentation für GitHub
├── LICENSE                 # MIT Open-Source Lizenz
└── assets/                 # (Optional) Bilder, Icons und Dokumente
```

---

##  Schnellstart

### 1. Repository klonen
```bash
git clone https://github.com/DEIN-USERNAME/stockvision-enterprise.git
cd stockvision-enterprise
```

### 2. Im Browser öffnen
Da das Projekt in purem HTML5/JavaScript mit Tailwind CDN geschrieben ist, benötigst du keinen schwerfälligen Node.js-Build-Prozess:

* **Direkt:** Öffne `index.html` per Doppelklick in einem modernen Webbrowser (Chrome, Firefox, Edge, Safari).
* **VS Code Live Server:** Rechtsklick auf `index.html` ➔ *Open with Live Server*.

---

##  Architektur & Module

Das Frontend verwendet ein sauberes **JavaScript Enterprise Pattern** mit separaten Modulen:

| Modul | Verantwortung |
| :--- | :--- |
| `StateStore` | Zentraler State-Manager & `localStorage` Syntronisation |
| `AuthManager` | Anmelde- & Registrierungslogik |
| `AutoTrader` | KI-Handelslogik, Risikoprüfung & Positionen-Management |
| `BankingGateway` | Sandbox-Kartenverwaltung & Ledger |
| `AIScreener` | Asset-Scanning & Signalerkennung |
| `WebSocketClient` | Vorbereiteter Handler für Live-Server-Anbindungen |

---

##  Sicherheitskonzept (Card Sandbox)

Das System setzt auf ein zweistufiges Sicherheitsmodell:
1. **Deposit Vault Isolation:** Trades werden ausschließlich mit Beträgen ausgeführt, die aktiv in den Trading Vault geladen wurden.
2. **Hard Reserve Limit:** Ein benutzerdefinierter Not-Aus-Schalter schützt das Restkapital vor weiteren Handelsverlusten.

---

##  WebSocket & Server Integration

Das Dashboard beinhaltet ein integriertes WebSocket-Modul zur einfachen Anbindung an reale Börsen-WebSockets (z. B. Binance, TradingView Webhooks oder Node.js Backends):

```javascript
// Beispiel zur Aktivierung des echten WebSocket-Streams in index.html:
WebSocketClient.connect('wss://dein-backend-server.com/ws/live-feed');
```

---

##  Lizenz

Dieses Projekt ist unter der **MIT-Lizenz** lizensiert.
