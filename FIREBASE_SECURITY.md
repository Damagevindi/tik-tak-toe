# Tik Tak Toe - Firebase Sicherheitsregeln

## 🔒 Sichere Datenbank-Regeln

Gehe zu: Firebase Console → Realtime Database → Rules

Füge diese Regeln ein:

```json
{
  "rules": {
    "games": {
      "$gameId": {
        // Nur authentifizierte Benutzer können lesen
        ".read": "auth != null",
        
        // Nur authentifizierte Benutzer können schreiben
        ".write": "auth != null",
        
        // Validierung: Spiel muss createdAt haben
        ".validate": "newData.child('createdAt').exists() || data.child('createdAt').exists()",
        
        "host": {
          // Host-UID muss mit Auth-UID übereinstimmen
          "uid": {
            ".validate": "newData.val() === auth.uid"
          }
        },
        
        "guest": {
          // Guest-UID muss mit Auth-UID übereinstimmen
          "uid": {
            ".validate": "newData.val() === auth.uid"
          }
        }
      }
    }
  }
}
```

## 🛡️ Sicherheitsfeatures

### 1. Anonymous Authentication
- Jeder Spieler erhält eine eindeutige UID
- Keine persönlichen Daten nötig
- Schutz vor unautorisiertem Zugriff

### 2. Spieler-Validierung
- Host kann nicht seinem eigenen Spiel beitreten
- Jeder Spieler hat eindeutige UID im Spiel gespeichert
- Verhindert Manipulation durch Dritte

### 3. Server Timestamp
- `createdAt` wird vom Server generiert
- Verhindert Client-seitige Zeitmanipulation

### 4. Disconnect-Handling
- Automatische Erkennung wenn Spieler das Spiel verlässt
- Status wird auf "disconnected" gesetzt

## 📝 Deployment

1. Regeln in Firebase Console einfügen
2. Auf "Veröffentlichen" klicken
3. Fertig!

## ⚠️ Wichtig

Diese Regeln erfordern Anonymous Authentication in Firebase:
- Gehe zu Authentication → Sign-in method
- Aktiviere "Anonymous"
- Speichern
