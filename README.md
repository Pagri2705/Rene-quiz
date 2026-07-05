# Rene Quiz — Daily Check-in

Eigenständiger Prototyp des täglichen Check-ins (Modern Athlete Lab Design):
15-Fragen-Flow mit bedingten Folgefragen, Drei-Säulen-Scoring (Ernährung /
Training / Recovery), regelbasierten Insights und Coach-Dashboard mit
7-Tage-Trends.

Alles in einer Datei, kein Build-Schritt, kein Backend.

## Öffnen

`index.html` direkt im Browser öffnen — fertig.

## Firebase-Setup (Auth + Firestore)

Der Check-in-Flow braucht ein Firebase-Projekt für Login und das Speichern der
täglichen Check-ins:

1. Projekt in der [Firebase Console](https://console.firebase.google.com/) anlegen.
2. **Authentication** → Sign-in-Methode **E-Mail/Passwort** aktivieren.
3. **Firestore Database** anlegen (Produktionsmodus).
4. Die Regeln aus [firestore.rules](firestore.rules) in der Console unter
   Firestore → Regeln einfügen und veröffentlichen.
5. Unter Projekteinstellungen → "Your apps" eine Web-App registrieren und die
   Config-Werte kopieren.
6. In `index.html` das Objekt `firebaseConfig` (im `<script type="module">`)
   mit den echten Werten ersetzen.

Kein Build-Schritt nötig — das Firebase SDK wird als ES-Modul direkt von
Googles CDN geladen, die Datei bleibt deploybar (z. B. auf Vercel) wie sie ist.

Jeder Nutzer sieht nur seine eigenen Check-ins (Firestore-Regeln greifen über
`uid`). Das Coach-Dashboard zeigt weiterhin Demo-Daten — eine echte
Mehr-Klienten-Ansicht für Coaches erfordert zusätzliche Rollen/Regeln und ist
noch nicht umgesetzt.
