# Die Bestie von Gévaudan — Charakter-Assistent

Ein geführter **Charakter-Creator** als **einzelne HTML-Datei** für ein Horror-Rollenspiel im Stil
von *Savage Worlds*, angesiedelt bei der historischen **Bestie von Gévaudan** (Frankreich, 1764–1767).

Die Seite führt Spieler:innen **Schritt für Schritt** durch die Erschaffung, erklärt dabei die
wichtigsten Regeln (kein Vorwissen nötig) und liefert am Ende einen **Charakterbogen als PDF**.
Alles steckt in `index.html` — **keine Installation, keine Server, offline nutzbar**.

---

## Schnellstart

1. `index.html` in einem Browser öffnen (Doppelklick genügt).
2. Dem Assistenten folgen: Regeln → Setting → Konzept → Attribute → Nachteile → Skills → Talente →
   Persönlichkeit → Beziehungen → Ausrüstung → **Charakterbogen**.
3. Am Ende:
   - **📄 Als PDF speichern** – öffnet den Druckdialog; dort als Ziel „Als PDF speichern" wählen.
   - **💾 Speichern (HTML)** – lädt deinen Charakter als HTML-Datei herunter. Öffnest du sie später,
     kannst du **weiterbearbeiten**. So schickst du deinen Charakter auch an die Spielleitung.
   - **⇩ Als JSON exportieren** – schlankes Austauschformat (z. B. für den Bestien-Baumeister).

> Tipp zum Ausprobieren: Auf der Willkommensseite gibt es **„Beispielcharakter ansehen"**.

## An die Spieler verschicken

Zwei Wege:
- **Datei schicken:** `index.html` (z. B. per E-Mail/Chat) verschicken. Der Fortschritt wird
  automatisch im Browser gespeichert; über **💾 Speichern (HTML)** behält man seinen Charakter.
- **Als Link (GitHub Pages):** Im Repository *Settings → Pages* die Auslieferung aus dem Branch
  aktivieren. Danach ist die Seite unter einer URL erreichbar und du schickst nur den Link.

---

## Spielleitung: der Bestien-Baumeister (`#sl`)

Wird eine Figur **gebissen**, legt die Spielleitung die Werwolf-Ebene über den bestehenden Charakter.
Dafür gibt es einen versteckten SL-Modus:

**Öffne die Seite mit `#sl` am Ende der Adresse**, z. B. `…/index.html#sl`.

Dort kannst du:
- einen Spielercharakter **laden** (aus JSON/gespeicherter HTML, aus dem Browser oder per Einfügen),
- den **Bestieninstinkt** (0–5) setzen — mit Beschreibung jeder Stufe und Schnell-Buttons für
  Auslöser (Blut +1, Vollmond +2 …),
- **Bestienkräfte** vergeben (Klauen, Biss, Regeneration, Nachtsicht …; Vorschläge je Stufe),
- **Silber-Schwäche** und **Bestienkontrolle** verwalten,
- den **kombinierten Bogen** (Mensch + Bestie) als PDF speichern.

> Hinweis: Da alles in *einer* Datei liegt, ist der SL-Modus technisch auch in der Spieler-Datei
> enthalten — er ist nur nicht verlinkt. Wer die Spieler nicht „spoilern" will, teilt den Link ohne
> `#sl` und behält den Modus für sich.

**Biss-Ablauf:** Spieler speichert Charakter (HTML/JSON) → SL öffnet ihn im `#sl`-Modus → Bestie
ergänzen → als PDF/HTML zurückgeben.

---

## Das Regelwerk in Kürze (Hausregeln)

- **Würfelstufen:** d4 → d6 → d8 → d10 → d12.
- **Probe:** Fertigkeits-Würfel + **Wild Die (d6)**, höheres Ergebnis; **Zielwert 4**.
  Je 4 Punkte darüber = eine **Steigerung**.
- **Erschaffung:** alle Attribute starten bei d4, **5 Attribut-Steigerungen**, **12 Fertigkeitspunkte**
  (1 Punkt/Stufe bis zur Höhe des Attributs, darüber 2), **1 Talent** gratis, **3 Bennies**.
- **Nachteile:** bis 1 großer (2 Punkte) + 2 kleine (je 1) — eintauschbar in Attribut (2), Talent (2)
  oder Fertigkeitspunkt (1).
- **Abgeleitet:** Parade = 2 + ½ Nahkampf · Robustheit = 2 + ½ Zähigkeit · Bewegung = 6.
- **Bestieninstinkt (0–5):** je stärker die Bestie, desto mächtiger — und desto schwerer bleibt man
  Mensch. Silber ignoriert die Regeneration der Bestie.

Diese Werte sind bewusst als anpassbare Hausregeln gedacht; die Konstanten stehen gebündelt oben im
`<script>`-Block von `index.html` (`RULES = { … }`).

---

## Technik

- Reines HTML/CSS/JavaScript, **ohne externe Abhängigkeiten** (keine CDNs, keine Fonts von außen).
- Speicherung: `localStorage` (Autosave) + selbst-speichernde HTML (Charakter im
  `#charakter-daten`-Block eingebettet) + JSON-Export/-Import.
- PDF über die Druckfunktion des Browsers (`@media print`), inkl. zweiter Profil-Seite.
- Getestet mit headless Chromium (Regel-Mathematik, Wizard, `#sl`-Modus, Speichern/Laden-Round-Trip).
