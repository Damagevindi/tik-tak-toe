# Tik Tak Toe - Firebase Setup für Online Multiplayer

## 🌐 Online Multiplayer aktivieren

### 1. Firebase Config erstellen

Kopiere die Beispiel-Datei:
```bash
cp firebase-config.js.example firebase-config.js
```

Fülle deine Firebase-Werte in `firebase-config.js` ein (aus deiner Firebase Console).

### 2. Sicherheitshinweis

⚠️ **WICHTIG:** Füge `firebase-config.js` zu `.gitignore` hinzu:
```
firebase-config.js
```

Die Config enthält API-Keys, die nicht öffentlich sein sollten.

### 3. Firebase Realtime Database Regeln

Gehe zu Firebase Console → Realtime Database → Rules und setze die Regeln aus `FIREBASE_SECURITY.md`.

## 🎮 Online-Spiel Funktionen

- **Spiel erstellen:** Generiert einen eindeutigen 6-stelligen Code
- **Spiel beitreten:** Code vom Gegner eingeben und loslegen
- **Echtzeit-Sync:** Züge werden sofort synchronisiert
- **Spieleranzeige:** Zeigt beide Spieler mit Symbol (X/O)
- **Verbindungsstatus:** Grün = verbunden, Orange = wartet, Rot = getrennt
- **Disconnect-Handling:** Automatische Erkennung wenn ein Spieler das Spiel verlässt

## 📝 Changelog v2.0.0

- ✨ Online Multiplayer mit Firebase
- ✨ Eindeutige Spiel-Codes (6 Zeichen)
- ✨ Echtzeit-Synchronisation
- ✨ Spielernamen-Eingabe
- ✨ Verbindungsstatus-Anzeige
- ✨ Automatische Bereinigung bei Disconnect
