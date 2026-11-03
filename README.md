# VSA Calc

Taschenrechner mit Grund- und wissenschaftlichen Funktionen.
Komplett lokal, werbefrei, ohne Tracking, funktioniert offline.
Herausgeber: Dennis Töppler, Vaultic Sanctuary Applications (VSA).

Die App ist eine einzelne HTML-Datei (`www/index.html`) und wird mit
[Capacitor](https://capacitorjs.com) als Android-App verpackt.

## APK über GitHub bauen

1. Dateien ins Repository hochladen. Den versteckten Ordner `.github` legst du über
   **Add file → Create new file** an (Dateiname `.github/workflows/build-apk.yml` tippen).
2. Jeder Push startet unter **Actions** den Workflow **Build APK**.
3. Nach ca. 3–5 Minuten liegt die fertige `VSA-Calc.apk` unter **Releases** (rechts auf der Repo-Startseite)
   und als Artifact im Actions-Lauf.

## Updates

Die APK ist eine Debug-APK. Der Workflow zählt die Versionsnummer bei jedem Build hoch
(`1.0.<Build-Nr.>`, steht auch auf dem Startscreen). Da der Debug-Schlüssel bei jedem Build neu
entsteht, lässt sich eine neue APK nicht über die alte installieren: erst deinstallieren, dann installieren.
Für echte Updates braucht es einen festen Signierschlüssel, der lässt sich bei Bedarf nachrüsten.

## Lokal bauen (optional)

Voraussetzungen: Node 20, JDK 17, Android SDK.

```bash
npm install
npx cap add android
npx cap sync android
cd android && ./gradlew assembleDebug
```

## Hinweise

- App ändern: `www/index.html` bearbeiten und pushen.
- Name und Paket-ID: `capacitor.config.json`.
- Icon und natives Startbild: `assets/` (`icon-*.png`, `splash*.png`), wird beim Build automatisch eingebunden.
- Startscreen: steht in `www/index.html` (Element `#splash`), 2,6 Sekunden oder per Tippen schließbar.
