# VSA Calc

Taschenrechner mit Grund- und wissenschaftlichen Funktionen.
Komplett lokal, werbefrei, ohne Tracking, funktioniert offline.

Die App ist eine einzelne HTML-Datei (`www/index.html`) und wird mit
[Capacitor](https://capacitorjs.com) als Android-App verpackt.

## APK über GitHub bauen (ohne lokale Installation)

1. Neues Repository auf GitHub anlegen und diesen Ordnerinhalt hochladen / pushen.
2. Im Repository den Tab **Actions** öffnen. Der Workflow **Build APK** startet bei jedem Push
   automatisch (oder manuell über **Run workflow**).
3. Nach ca. 3–5 Minuten den Lauf öffnen und unter **Artifacts** `VSA-Calc-APK` herunterladen.
4. ZIP entpacken, `VSA-Calc.apk` aufs Handy kopieren und installieren
   (ggf. „Installation aus unbekannten Quellen“ erlauben).

**Release mit Download-Link:** Tag setzen, z. B. `git tag v1.0.0 && git push --tags`.
Die APK hängt dann automatisch unter **Releases**.

## Lokal bauen (optional)

Voraussetzungen: Node 20, JDK 17, Android SDK.

```bash
npm install
npx cap add android
npx cap sync android
cd android && ./gradlew assembleDebug
# APK: android/app/build/outputs/apk/debug/app-debug.apk
```

## Hinweise

- Die APK ist eine **Debug-APK**: direkt installierbar, aber nicht für den Play Store signiert.
- App ändern: nur `www/index.html` bearbeiten und pushen.
- Name und Paket-ID stehen in `capacitor.config.json` (`de.vsa.calc`).
- App-Icon: liegt in `assets/` (`icon-only.png`, `icon-foreground.png`, `icon-background.png`, je 1024×1024).
  Der Workflow erzeugt daraus beim Build automatisch alle Android-Icon-Größen.
  Zum Austauschen einfach diese drei PNGs ersetzen.
