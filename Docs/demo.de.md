# Überblick über „MD Editor“

Nativer Markdown-Editor für macOS und iPadOS. Dieser Ausschnitt deckt **Fettschrift**, *Kursivschrift*, ~~durchgestrichenen Text~~, `Inline-Code`, <mark>Hervorhebung</mark>, die Tasten <kbd>⌘</kbd>+<kbd>K</kbd>, eine Fußnote[^1], die Formeln $E = mc^2$ und $a^2 + b^2 = c^2$ sowie oberen<sup>2</sup> und unteren<sub>2</sub> Index ab. Externer Link: [example.com/docs](https://example.com/docs "Dokumentation"), Wiki-Link: [[Notiz]], relativ: [notes/other.md](notes/other.md), Anker: [zum Abschnitt „Code“](#h-kod) und [E-Mail](mailto:hi@example.com).

## Listen

- Erste Ebene
- Mit einer verschachtelten Liste
  - Zweite Ebene — Aufzählungszeichen „Kreis“
  - Noch ein Punkt
    - Dritte Ebene — Aufzählungszeichen „Quadrat“

3. Die Nummerierung beginnt bei drei
4. Zweiter Punkt
   1. Verschachtelt — lateinische Kleinbuchstaben

### Checkliste

- [x] HTML/CSS/JS-Schicht der Vorschau erstellt
- [ ] Alle acht Themes geprüft
- [ ] Druck und Export geprüft

## Code

Inline-Code: `let preview = MDEditorPreview()`. Unten ein Block mit Hervorhebung aller Tokens des Vertrags.

```swift
// Синхронизация предпросмотра со строкой исходника
final class PreviewCoordinator: NSObject {
    private var activeLine: Int = 0
    func scrollToSourceLine(_ line: Int) {
        webView.evaluateJavaScript("MDEditorPreview.scrollToSourceLine(\(line))") + 1
    }
}
```

```diff
@@ -12,7 +12,9 @@
+let width = appearance.contentWidth
-let width = 760
 apply(width)
```

```
Блок без языка — подписи в углу быть не должно.
Очень длинная строка для проверки горизонтальной прокрутки: 0123456789 0123456789 0123456789 0123456789 0123456789 0123456789 0123456789 0123456789 0123456789 0123456789 0123456789 0123456789
```

## Zitat und Tabelle

> „Typografie ist das, was einen Text lesbar macht und nicht nur sichtbar.“
>
> > Verschachteltes Zitat zur Prüfung von Einzug und Linie.

| Funktion | macOS | iOS |
| --- | :---: | ---: |
| WKWebView-Vorschau | ja | ja |
| KaTeX und Mermaid offline | ja | ja |
| Breite Zelle, die auf dem iPhone in horizontales Scrollen übergehen muss | ja | ja |

## KaTeX-Formeln

Inline-Formel mit Dollar-Begrenzern $e^{i\pi} + 1 = 0$ und mit runden Klammern \\( \\int_0^1 x^2\\,dx = \\tfrac13 \\).

$$\frac{n!}{k!(n-k)!} = \binom{n}{k}, \qquad \sum_{i=1}^{n} i = \frac{n(n+1)}{2}$$

Blockformel in eckigen Klammern: \\[\\nabla \\cdot \\vec{E} = \\frac{\\rho}{\\varepsilon_0}\\]

Fehlerhafte Formel (sollte sichtbar werden, aber das Dokument nicht zerstören): $\frac{1}{$

Eine Formel innerhalb von Code wird nicht gerendert: `$x^2$`.

## Mermaid-Diagramme

```mermaid
graph TD
  A[Quelldatei .md] --> B{Analyse}
  B -->|Block| C[MarkdownRenderer]
  B -->|Inline| D[BaselineInline]
  C --> E[preview.js]
  D --> E
  E --> F[WKWebView]
```

```mermaid
sequenceDiagram
  participant R as Editor
  participant P as Vorschau
  R->>P: scrollToSourceLine(42)
  P->>R: postMessage({type:"scroll",line:42})
```

```mermaid
graph TD
  A[Diagrammfehler] --> B[
```

## Verschiedenes

---

![Platzhalterbild](data:image/svg+xml;charset=utf-8,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%22320%22%20height%3D%22160%22%3E%3Crect%20width%3D%22320%22%20height%3D%22160%22%20rx%3D%2210%22%20fill%3D%22%23c8d4e3%22%20stroke%3D%22%237f95ad%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20x%3D%22160%22%20y%3D%2286%22%20font-family%3D%22sans-serif%22%20font-size%3D%2218%22%20fill%3D%22%233d4a5c%22%20text-anchor%3D%22middle%22%3E%D0%B8%D0%B7%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5%20320%C3%97160%3C%2Ftext%3E%3C%2Fsvg%3E "Bild mit data-URI")

<details>
<summary>Eingeklappter Block</summary>
Der Inhalt wird per Klick aufgeklappt.
</details>

[^1]: Fußnote mit Rückverweis auf die Stelle im Text.
