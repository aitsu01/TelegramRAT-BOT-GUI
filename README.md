# TelegramRAT-BOT-GUI

# Telegram-RAT (Educational Project)

> **Studio di un Remote Access Trojan (RAT) basato su Telegram Bot**

## 📖 Panoramica

Questo progetto mostra l'implementazione di un **server C2** in Python con GUI e di un **client in C++**, che comunicano tramite un bot Telegram dedicato. Lo scopo è puramente **educazionale**: comprendere le tecniche di C2 e sfruttamento senza necessità di port forwarding o VPN.

Invece di pubblicare il codice sorgente su GitHub, verrà fornito un **video dimostrativo** e **screenshot** per motivi di sicurezza e riservatezza.

## 🎯 Motivazione

* Analizzare come un bot Telegram possa fungere da canale C2 (MITRE T1071.001) senza aprire porte in ingresso.
* Sperimentare l’ottimizzazione di un client performance-critical in C++ (uso di WinHTTP, GDI+, Media Foundation, threading).
* Creare una dashboard GUI in Python per controllare sessioni multiple in modo user-friendly.

## 🏗️ Architettura

```
[Client C++]  ↔  Telegram Bot API  ↔  [Server Python GUI]
       ↑                                     ↓
    Sistema remoto                     Dashboard Tkinter
```

1. **Client C++**: invia heartbeat, comandi e media via HTTPS/WebSocket con WinHTTP.
2. **Bot Telegram**: smista i messaggi dal client al server e viceversa.
3. **Server Python**: raccoglie input, mostra log, snapshot, file explorer e invia comandi.

## ✨ Caratteristiche principali

* **Heartbeat automatico** per monitorare lo stato `online/offline`
* **Comandi rapidi**: `/ping`, `/exec`, `/shell`, `/screenshot`, `/clipboard`, `/recordmic`, `/listfiles`, `/upload`, `/download`
* **Visualizzazione live** di screenshot e webcam nella GUI Python
* **Upload/Download** di file tra server e client
* **Registrazione audio** e invio di file multimediali via Telegram
* **Uso di librerie native Windows**: WinHTTP, Media Foundation, GDI+, WIC

## 📽️ Video Dimostrativo & Screenshot

Per vederne il funzionamento, guarda il video su YouTube e consulta le immagini nel documento `docs/screenshots`.

* **Video demo**:

  ![Screenshot2](https://github.com/user-attachments/assets/c47f8454-86f1-4cf4-b4a9-abcdf3c1ff38)


https://github.com/user-attachments/assets/e5a2565b-976b-4019-bc75-9378a94a2bc5




https://github.com/user-attachments/assets/e13eea0e-4028-4ea7-89b6-1b333c0ec7f6




* **Screenshot**: `docs/screenshots/webcam.png`, `docs/screenshots/gui_overview.png`

## ⚙️ Requisiti e Installazione

### Server (Python)

* Python 3.8+
* `pip install -r requirements.txt`

  ```text
  telethon
  pillow
  plyer
  requests
  ```
* Configura il bot Telegram: imposta `API_ID`, `API_HASH` e `BOT_TOKEN` nel file `server/config.py`.
* Avvia:

  ```bash
  ```

docker run --rm -v "\$PWD/logs":/app/logs python:3.10-slim bash -c "pip install -r requirements.txt && python server.py"

```

### Client (C++)
- Windows 10 SDK, Visual Studio 2022
- Abilita librerie: `mfplat.lib`, `mfreadwrite.lib`, `windowscodecs.lib`, `ws2_32.lib`, etc.
- Apri la soluzione `TelegramRAT.sln` e compila in Release x64


## 🔒 Disclaimer di Sicurezza
- **Solo per uso in laboratorio controllato**.  
- Non utilizzare in ambienti di produzione o su macchine non autorizzate.  
- Scopo didattico: comprendere tecniche offensive e implementazioni C2.


## 🛠️ Uso
1. Avvia il **server Python** e attendi che si connetta il primo client.
2. Esegui l’eseguibile **C++** su una macchina Windows di test.
3. Nella GUI comparirà una scheda per ogni client con stato online.
4. Digita comandi o usa i pulsanti per interagire con il client remoto.


## 🔮 Sviluppi Futuri
- Persistenza automatica (es. registro Windows)
- Cifratura del canale C2
- Autenticazione a doppio fattore
- Supporto multiplatform (client Linux/macOS)




---
_Esclusivamente uso educativo. Non distribuire senza autorizzazione._

```
