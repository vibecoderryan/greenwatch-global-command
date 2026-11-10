# GREENWATCH: GLOBAL COMMAND — v0.1 First Expansion

Ein kostenloses, fiktives Weltstrategie- und Radarspiel direkt im Browser. Du beginnst mit einer einzigen Militärbasis in Uruguay, eroberst Territorien und baust ein Netz aus Boden-, Schiffs- und Luftüberwachung auf.

## Spielen

**GitHub Pages (empfohlen):** Lade den vollständigen Inhalt dieses Ordners in ein öffentliches GitHub-Repository hoch. Öffne im Repository **Settings → Pages → Build and deployment → Deploy from a branch**, wähle `main` und `/ (root)` und speichere. Die Adresse lautet danach üblicherweise `https://DEIN-NAME.github.io/REPOSITORY-NAME/`.

**Lokal:** Öffne `index.html` in einem aktuellen Browser. Die Weltkartendaten sind als lokale JavaScript-Datei integriert; es sind weder Internet noch ein Server erforderlich. Alternativ kannst du im Projektordner `python -m http.server 8000` starten und `http://localhost:8000` öffnen.

## Einstieg

1. Im Briefing auf **EINSATZ STARTEN** klicken. In Uruguay steht deine einzige Militärbasis, das Land gehört dir anfangs noch nicht.
2. In **OPERATIONEN** den Infanterieverband **A-01** auswählen (voreingestellt). Als Zielland **Uruguay** ausgewählt lassen und **ANGRIFF** drücken.
3. Die Operation läuft in Echtzeit und dauert 11 Spielsekunden. Du kannst das Spiel mit `10×` beschleunigen.
4. Nach erfolgreicher Eroberung Uruguay sichern und die Armee nach Argentinien verlegen. Zur Unterstützung den Jäger `F-01` auf das Zielland patrouillieren lassen oder eine zweite Armee einsetzen.
5. Unter **BAUEN** neue Einheiten, mobile Radare oder Radarstationen aus Versorgungspunkten kaufen. Mit **RADAR** auf den rustikalen CRT-Bildschirm wechseln. Über **INTEL** lassen sich Kontakte auswählen und identifizieren.
6. Missionsziel: **3 Länder kontrollieren** und das Hauptquartier intakt halten. Danach lässt sich das Spiel im Endlosmodus fortsetzen.

## Bedienung

| Aktion | Steuerung |
|---|---|
| Zielland wählen | Land auf der Weltkarte anklicken |
| Einheit wählen | Eintrag in der rechten Einheitenliste anklicken |
| Auftrag geben | Einheit + Zielland auswählen, dann „Angriff/Verlegen“ |
| Karte verschieben | Linke Maustaste ziehen / Touch ziehen |
| Zoom | Mausrad, `+` / `−`, Schaltflächen unten rechts |
| Startbasis / Weltansicht | `⌖` / `◫` |
| Pause | Leertaste oder Pausenschalter |
| Spielgeschwindigkeit | `1×`, `3×`, `10×` |
| Kontakt identifizieren | Radar öffnen → Dreieck anklicken → INTEL → Identifizieren |
| Speichern | Schaltfläche oben rechts; zusätzlich automatische lokale Sicherung |
| Neustart | Schaltfläche `↻` oben rechts |

## Spielmechaniken

- **177 geografische Länder und Gebiete** mit realen, vereinfachten Grenzen (Natural Earth, 1:110m). Echte Weltgeografie, aber **fiktive Konflikte und Fraktionen**.
- **Army:** Angriffe auf das eigene Startland oder benachbarte Länder. Erreicht der Angriff nicht die Verteidigungsstärke, wird die Verteidigung des Ziels für einen späteren Angriff geschwächt.
- **Air Force:** Patrouillen mit bis zu 2.100 km Einsatzreichweite, +3 Unterstützung bei Landangriffen im Zielgebiet und Abfangmanöver gegen ausgewählte Radarkontakte.
- **Navy:** Patrouille in Küstenländern; +2 Unterstützung für eine Landung bzw. einen Angriff auf ein Küstenland.
- **Radar:** Basisradar (750 km), stationäres Radar (1.050 km), mobiles Radar (470 km), Schiffsradar (280 km). Die Sensoren erkennen Luftkontakte in ihrer Reichweite; sie decken nicht automatisch sämtliche Bodentruppen auf.
- **Fog of War:** Geografische Umrisse sind bekannt. Aktuelle Eigentümer- und Verteidigungsdaten werden nur bei eigener Bodenaufklärung angezeigt. Nicht überwachte Gebiete bleiben dunkel.
- **Wirtschaft:** Basis liefert 10 VP/Minute, kontrollierte Länder jeweils 9 VP/Minute. Eroberungen geben einen Bonus von 20 VP.
- **KI:** Zwei nichtspielbare Fraktionen expandieren von ihren Startgebieten aus. Deren Expansion erfolgt unabhängig von deinem Sichtbereich.
- **Gewinn:** Kontrolle über mindestens drei Länder (+1.000 Punkte). **Verlust:** HQ-Integrität erreicht 0 %.
- **Speichern:** Browser-`localStorage`; der Spielstand verbleibt auf dem Gerät und wird nicht an einen Server gesendet.

## Projektdateien

```text
index.html             – Oberfläche und Spielbereiche
style.css              – klassisches Radar-/Kommandodesign
js/game.js             – sämtliche Spielmechaniken, KI, Rendering, Speicherstand
data/world-data.js     – vereinfachte reale Länderpolygone, offline nutzbar
.nojekyll              – verhindert GitHub-Pages-Jekyll-Verarbeitung
LICENSE                – MIT-Lizenz für den Spielcode
README.md              – diese Anleitung
```

## Datenquellen und Lizenz

Die Weltkarte stammt aus dem öffentlichen Datensatz **Natural Earth 1:110m Admin-0 Countries**, lokal verfügbar über die `naturalearth_lowres`-Testdaten von `pyogrio`. Die Geometrien wurden für kleine Ladezeiten vereinfacht und nur auf Ländername, Code, Kontinent, Bevölkerung, Nachbarn, Küstenkennzeichen und Koordinaten reduziert. Natural Earth stellt diese Geodaten unter **Public-Domain-Bedingungen** bereit: https://www.naturalearthdata.com/about/terms-of-use/ . Die vereinfachten Grenzen sind für Gameplay gedacht, nicht zur rechtlichen Festlegung von Staatsgrenzen.

Der selbst geschriebene Code ist unter der MIT-Lizenz freigegeben; siehe `LICENSE`.

## Prototypgrenzen

- Globale Länder werden als **einzelne Territorien** dargestellt, keine innerstaatlichen Provinzen.
- Kämpfe sind bewusst abstrahiert; keine Einzeltruppen-Physik, echte Waffendaten oder realen militärischen Szenarien.
- Die Radarflugbewegungen sind simuliert und keine Live-Flugdaten.
- Einheiten bewegen sich auf Landesebene in Echtzeit; See- und Luftwege sind vereinfacht.
- Keine Diplomatie, Lieferketten, Forschung oder Multiplayer in v0.1.

## Fehlerbehebung

- **Karte leer?** Prüfen, dass `data/world-data.js` neben `index.html` im Unterordner `data` liegt. Browser-Konsole auf Fehlermeldungen untersuchen.
- **GitHub-Seite 404?** Repository öffentlich und Pages-Quelle `main` + `/ (root)` einstellen. Veröffentlichung kann einige Minuten dauern.
- **Spielstand zurücksetzen:** Oben rechts `↻` anklicken, um einen neuen Spielstand zu starten.
