<div align="center">

# QR Code Generator

### Portable QR-Code-Erstellung für Windows

Erstelle QR-Codes aus Texten, Links und beliebigen kopierbaren Inhalten –
ohne Installer, ohne Administrationsrechte und direkt aus einem Ordner.

<br>

**[Schnellstart](#schnellstart)** ·
**[Funktionen](#funktionen)** ·
**[Fehlerbehebung](#fehlerbehebung)** ·
**[Lizenz](#lizenz)**

</div>

> **Kurz gesagt:** Ordner entpacken, `run-portable.bat` starten, Inhalt
> eingeben und QR-Code erzeugen.

---

## Überblick

Der QR Code Generator ist eine portable JavaFX-Desktop-Anwendung für
Windows. Das vollständige Paket bringt die benötigte JavaFX-Laufzeit bereits
mit. Dadurch bleibt die Anwendung unabhängig von einer global installierten
JavaFX-Version und kann auf kompatiblen Rechnern aus jedem beliebigen
Verzeichnis gestartet werden.

### Was diese Version auszeichnet

| Eigenschaft | Details |
|---|---|
| **Portable** | Kein Installer und keine Einträge in der Windows-Registry |
| **Einfach** | Start über eine einzige Batch-Datei |
| **Offline-fähig** | Für die QR-Code-Erstellung ist keine Internetverbindung erforderlich |
| **Flexibel** | Texte, URLs und andere Zeichenfolgen als QR-Inhalt |
| **Modern** | JavaFX-Oberfläche mit hellem und dunklem Styling |
| **Sicher verteilbar** | JAR, Startskript und Laufzeit liegen gemeinsam im Paket |

## Funktionen

- QR-Codes aus frei eingegebenem Inhalt erzeugen
- URLs, Klartext und andere kopierbare Zeichenfolgen verwenden
- Ergebnis direkt in der Desktop-Anwendung prüfen
- Helles und dunkles Erscheinungsbild der Oberfläche
- Offline-Nutzung nach dem Entpacken
- Keine Installation und keine Administratorrechte erforderlich
- Mitgelieferte JavaFX-Laufzeit für eine reproduzierbare Ausführung

> **Wichtig:** Der QR-Code enthält exakt den eingegebenen Inhalt. Prüfe
> insbesondere URLs und längere Texte vor der Weitergabe mit einem
> QR-Code-Scanner.

## Voraussetzungen

- Windows
- Java **17 oder neuer**
- Java muss im `PATH` verfügbar sein
- Empfohlen: Java 25

JavaFX muss nicht separat installiert werden. Die benötigten Dateien befinden
sich im Ordner `javafx-sdk-27`.

Java prüfen:

```bat
java -version
```

Wird eine Versionsnummer ausgegeben, kann die Anwendung in der Regel
gestartet werden.

## Schnellstart

### 1. Paket vollständig entpacken

Entpacke das ZIP-Archiv vollständig. Starte die Anwendung nicht direkt aus
dem Archiv und verändere die Ordnerstruktur nicht.

### 2. Struktur prüfen

Im Hauptordner müssen mindestens diese Pfade vorhanden sein:

```text
javafx-sdk-27\lib\
target\qr-code-generator-1.0.0-all.jar
run-portable.bat
```

### 3. Anwendung starten

Doppelklicke auf `run-portable.bat`.

### 4. QR-Code erstellen

1. Gewünschten Inhalt in das Eingabefeld eintragen.
2. QR-Code mit der vorgesehenen Schaltfläche erzeugen.
3. Das Ergebnis prüfen und anschließend mit einem Smartphone oder Scanner
   testen.

```mermaid
flowchart LR
    A[Anwendung starten] --> B[Text oder URL eingeben]
    B --> C[QR-Code erzeugen]
    C --> D[Mit Scanner prüfen]
    D --> E[Verwenden oder weitergeben]
```

## Start per Eingabeaufforderung

Für Diagnosezwecke kann die Batch-Datei aus einer Eingabeaufforderung
gestartet werden:

```bat
cd /d C:\Pfad\zu\QRCodeGenerator-Portable
run-portable.bat
```

Das Skript führt intern diesen Startbefehl aus:

```bat
java --module-path javafx-sdk-27\lib --add-modules javafx.controls,javafx.fxml -jar target\qr-code-generator-1.0.0-all.jar
```

Das `pause` am Ende des Skripts hält das Fenster offen, damit mögliche
Fehlermeldungen gelesen werden können.

## Paketstruktur

```text
QRCodeGenerator-Portable\
├─ run-portable.bat                  Startskript
├─ README.md                         Diese Dokumentation
├─ README-portable.txt               Kurzanleitung
├─ LICENSE                           MIT-Lizenz
├─ javafx-sdk-27\                    Mitgelieferte JavaFX-Laufzeit
│  ├─ bin\
│  └─ lib\
└─ target\
   ├─ classes\
   └─ qr-code-generator-1.0.0-all.jar Ausführbare Komplettversion
```

> **Hinweis zum Programmsymbol:** Die Datei `target\classes\icon.ico` ist
> ein Windows-Icon und kein Webbild. Sie wird deshalb absichtlich nicht als
> Markdown-Bild eingebunden. So wird verhindert, dass Binärdaten als
> unlesbarer Zeichensalat dargestellt werden.

## Fehlerbehebung

### „java is not recognized“ oder Java wird nicht gefunden

Java ist nicht installiert oder nicht im `PATH` eingetragen.

1. Java 17 oder neuer installieren.
2. Ein neues Eingabeaufforderungsfenster öffnen.
3. `java -version` ausführen.
4. `run-portable.bat` erneut starten.

### JavaFX oder das JAR wird nicht gefunden

Prüfe, ob die Anwendung aus dem Hauptordner gestartet wird und diese Pfade
exakt existieren:

```text
javafx-sdk-27\lib
target\qr-code-generator-1.0.0-all.jar
```

Entpacke das ZIP-Archiv erneut, falls Dateien fehlen. Die Datei oder Ordner
innerhalb des Pakets dürfen nicht umbenannt oder verschoben werden.

### Das Fenster schließt sich sofort

Starte `run-portable.bat` aus einer Eingabeaufforderung und kopiere die
vollständige Ausgabe. So bleibt die Fehlermeldung sichtbar und kann
zuverlässig ausgewertet werden.

### Windows zeigt eine Sicherheitswarnung

Das kann bei Dateien aus dem Internet oder aus einem ZIP-Download passieren.
Verwende nur ein vertrauenswürdiges Paket und prüfe gegebenenfalls die
Eigenschaften der ZIP-Datei. Die Anwendung benötigt für den normalen Start
keine Administratorrechte.

## Weitergabe und Backup

Für eine funktionierende portable Kopie müssen diese Bestandteile gemeinsam
erhalten bleiben:

- `run-portable.bat`
- `target\qr-code-generator-1.0.0-all.jar`
- der vollständige Ordner `javafx-sdk-27`

Am einfachsten ist es, den gesamten Hauptordner erneut als ZIP-Archiv zu
packen. Einzelne DLLs oder JAR-Dateien aus `javafx-sdk-27` dürfen nicht
weggelassen werden.

## Technologie

- Java
- JavaFX 27
- ZXing als QR-Code-Bibliothek im gebündelten JAR

## Lizenz

Dieses Projekt steht unter der [MIT-Lizenz](LICENSE).

---

<div align="center">

**QR Code Generator · Portable · Windows**

</div>
