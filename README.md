# TAFEL digital

**Tiefenentspannter Arbeitsfluss für engagierte Lehrkräfte**

<img width="643" height="643" alt="logo" src="https://github.com/user-attachments/assets/9fb2c881-04e1-4de1-a6f9-e35c12ec2c2a" />

TAFEL ist eine Desktop-Anwendung für Lehrkräfte. Sie vereint Klassen, Noten,
Stundenpläne, Coaching-Notizen, Sitzpläne und KI-gestützte
Lernentwicklungsberichte an einem Ort.

---

## Local-First – Ihre Daten bleiben auf Ihrem Gerät

TAFEL folgt einem einfachen Grundsatz: **Schülerdaten gehören der Lehrkraft,
nicht irgendwelchen digitalen Anbietern.**

- **Alles läuft lokal.** Die App, ihre Datenbank und sogar das KI-Modell laufen
  auf Ihrem eigenen Computer. Es gibt keinen TAFEL-Server, kein Login, kein Konto.
- **Es werden keine Daten an mich übertragen – niemals.** Der Entwickler erhält,
  verarbeitet oder speichert keine Ihrer Daten. Es gibt **keine Telemetrie,
  keine Analyse, kein Nutzungs-Tracking, kein „Nach-Hause-Telefonieren“**. Auf Wunsch kann manuell ein Fehlerbericht verschickt werden - TAFEL funktioniert vollständig offline.
- **Alle Schülerdaten sind verschlüsselt gespeichert.** Namen und persönliche
  Angaben werden verschlüsselt (AES-256-GCM), bevor sie auf die Festplatte
  geschrieben werden – mit einem Schlüssel, der aus Ihrem Passwort abgeleitet
  wird. Ohne Ihr Passwort ist die Datenbank nicht lesbar.
- **Auch die KI läuft auf Ihrem Gerät.** Lernberichte werden von einem
  Sprachmodell erstellt, das lokal über [Ollama](https://ollama.com) läuft –
  es werden keine Schülerdaten an OpenAI, Google oder einen anderen
  Online-Dienst gesendet. Somit bleibt die Software datenschutzkonform.

Kurz gesagt: TAFEL ist ein normales Desktop-Programm, das Ihre Klassendaten auf 
Ihrem Laptop verwaltet – wie eine Datenbank oder die klassischen Exceltabellen, 
nur mit Verschlüsselung und einem eingebauten, datenschutzkonformen Assistenten.

---

## Funktionen

- **Klassen** – Klassen und Schüler verwalten, mit CSV- / WebUntis-Import
- **Noten** – Leistungen, gewichtete Notenkategorien, kompetenzorientierte Bewertung
- **Stundenplan** – Wochenplan mit WebUntis- / iCal-Import und Fachfarben
- **Kalender** – Monatskalender mit Terminen, iCal-Export und CalDAV- / Ferien-Import
- **Coaching** – ein privates, verschlüsseltes Gesprächsprotokoll pro Schüler
- **Lernentwicklungsberichte** – KI-basierte Berichte auf Basis der erreichten Punkte pro Kompetenzbereich, Export als PDF / DOCX
- **Tafel** – eine interaktive Tafel: Uhr, Timer, Namensauswahl, Lärmampel, QR-Codes
- **Sitzplan** – ein schlauer Sitzplan-Editor der Schüler nach Regeln automatisch auf die für sie besten Plätze plaziert
- **Werkzeuge** – Gruppengenerator, Arbeitszeiterfassung, Elternbrief-Generator
- **KI-Chat** – ein lokaler KI-Chat-Assistent, nur für die aktuelle Sitzung gespeichert
- **Barrierefreiheit** – Themes für verschiedene Farbwahrnehmungsschwächen und voller Support für Screenreader

---

## Technik (einfach erklärt)

TAFEL ist eine klassische Desktop-Anwendung. Für den Betrieb ist keinerlei
Internetverbindung nötig.

| Bereich | Was verwendet wird | Was das bedeutet |
| --- | --- | --- |
| **Sprache** | Java 21 | Eine ausgereifte, plattformübergreifende Programmiersprache. Die gesamte App ist ein einziges Programm. |
| **Oberfläche** | JavaFX 21 | Das Toolkit, das die Fenster, Schaltflächen und Ansichten zeichnet, die Sie sehen. |
| **Datenbank** | SQLite | Eine einzelne Datenbank-*Datei* auf Ihrer Festplatte (`~/.tafel/tafel.db`) – kein Datenbankserver nötig. |
| **Verschlüsselung** | AES-256-GCM + PBKDF2 | Etablierte Standardverschlüsselung. Sensible Daten werden mit einem aus Ihrem Passwort erzeugten Schlüssel verschlüsselt. |
| **Lokale KI** | Ollama + Google Gemma | Das KI-Modell läuft auf *Ihrem* Computer. TAFEL startet es, kommuniziert lokal damit und beendet es wieder. |
| **Dokumente** | PDFBox + openhtmltopdf | Erzeugt aus Berichten und Sitzplänen PDF-Dateien. |
| **Import / Codes** | Jackson, Commons CSV, ZXing | Liest WebUntis-/JSON- und CSV-Daten; erzeugt QR-Codes für die Tafel. |
| **Protokollierung** | SLF4J + Logback | Führt ein lokales Diagnose-Protokoll (`~/.tafel/logs/`) – ausschließlich auf Ihrem Gerät. |

Alles wird in einer einzigen, in sich geschlossenen Anwendung ausgeliefert.
Endnutzer installieren und starten sie einfach – kein separater Datenbank-,
Web- oder KI-Server muss eingerichtet werden.

---

## Lizenzhinweise / Third-Party AI Model Licensing

Dieses Projekt verwendet Google Gemma 4, das unter der Apache License 2.0
bereitgestellt wird.

- Gemma 4 ist nicht in dieser Software enthalten. Es wird vom Nutzer lokal über Ollama heruntergeladen.
