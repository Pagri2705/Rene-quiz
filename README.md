# Modern Athlete LAB™ — The 7-Day Reset

Premium, mobile-first 7-Tage-Challenge-Portal (EN/DE) für Modern Athlete LAB™:
Sprachauswahl → Day 0 Welcome + Baseline-Check-in → 7-Tage-Dashboard mit
täglichen Missionen, Punkten, Streaks & Badges → Day-4 Bottleneck Snapshot™ →
Day-7 Personal MAP™ CTA. Dazu ein Coach-Dashboard (`admin.html`) mit
Teilnehmer-Übersicht, Check-in-Verläufen, Hot-Lead-Logik und
WhatsApp-Antwort-Buttons.

Alles statisch (kein Build-Schritt), gehostet auf Vercel, Daten via
Firebase Auth + Firestore.

## Dateien

- `index.html` — Teilnehmer-App (SPA, EN/DE)
- `admin.html` — Coach-Dashboard (Zugang: feste Coach-E-Mail)
- `verify.html` — Zielseite des E-Mail-Bestätigungslinks
- `firestore.rules` — Firestore-Sicherheitsregeln (in der Firebase-Konsole einfügen)
- `storage.rules` — Firebase-Storage-Regeln, falls später Datei-Uploads
  (z. B. Personal MAP™ PDFs unter `/plans/{uid}/...`) dazukommen
- `assets/intro-video.mp4` — bereits als Day-0-Welcome-Video verdrahtet
  (aktuell für EN und DE dieselbe Datei, bis René getrennte Sprachversionen liefert)
- `assets/collage/photo1–10.png` — vorhandene Fotos aus einer früheren
  Session, aktuell **nicht** im neuen Reset-Design verbaut (das Briefing sieht
  keinen Foto-Hintergrund vor) — liegen im Repo bereit, falls sie später
  irgendwo eingesetzt werden sollen (z. B. Instagram-Story-Karten, Day-0-Galerie)

## Offene Platzhalter

1. **Tages-Videos**: In `index.html` das `VIDEOS`-Objekt mit den EN/DE-Video-URLs
   von René füllen (Tag 1–7, Bottleneck, Final). Leere URL = eleganter
   Platzhalter. Day-0-Video ist bereits mit `assets/intro-video.mp4` belegt.
2. **WhatsApp-Nummer**: `COACH_WHATSAPP` in `index.html` setzen
   (internationales Format ohne `+`). Leer = WhatsApp öffnet mit Nachricht
   und freier Kontaktwahl.
3. **Firestore-Regeln**: Nach jedem Update von `firestore.rules` den Inhalt
   in der Firebase-Konsole (Firestore → Regeln) veröffentlichen.

## Rollback

Die vorherige Version (tägliche Check-in-App mit Bestenliste, Challenges,
DE/EN/ZH) liegt unverändert auf dem Branch **`legacy-checkin-v1`**:

```
git checkout legacy-checkin-v1 -- index.html admin.html firestore.rules README.md
```

(oder den Branch komplett auschecken). Die Legacy-Firestore-Collections
bleiben in den aktuellen Regeln erhalten, damit die alte Version sofort
wieder lauffähig ist.
