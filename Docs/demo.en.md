# Overview of “MD Editor”

Native Markdown editor for macOS and iPadOS. This excerpt covers **bold**, *italic*, ~~strikethrough~~, `inline code`, <mark>highlight</mark>, the <kbd>⌘</kbd>+<kbd>K</kbd> keys, a footnote[^1], the formulas $E = mc^2$ and $a^2 + b^2 = c^2$, as well as superscript<sup>2</sup> and subscript<sub>2</sub>. External link: [example.com/docs](https://example.com/docs "Documentation"), wiki link: [[Note]], relative: [notes/other.md](notes/other.md), anchor: [to the “Code” section](#h-kod) and [email](mailto:hi@example.com).

## Lists

- First level
- With a nested list
  - Second level — “circle” bullet
  - Another item
    - Third level — “square” bullet

3. Numbering starts at three
4. Second item
   1. Nested — lowercase Latin letters

### Checklist

- [x] HTML/CSS/JS preview layer built
- [ ] All eight themes checked
- [ ] Printing and export checked

## Code

Inline code: `let preview = MDEditorPreview()`. Below is a block with highlighting of all contract tokens.

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

## Quote and table

> “Typography is what makes text readable, not merely visible.”
>
> > Nested quote to check indentation and the bar.

| Feature | macOS | iOS |
| --- | :---: | ---: |
| WKWebView preview | yes | yes |
| KaTeX and Mermaid offline | yes | yes |
| A wide cell that must go into horizontal scrolling on iPhone | yes | yes |

## KaTeX formulas

Inline formula with dollar delimiters $e^{i\pi} + 1 = 0$ and with parentheses \\( \\int_0^1 x^2\\,dx = \\tfrac13 \\).

$$\frac{n!}{k!(n-k)!} = \binom{n}{k}, \qquad \sum_{i=1}^{n} i = \frac{n(n+1)}{2}$$

Block formula in square brackets: \\[\\nabla \\cdot \\vec{E} = \\frac{\\rho}{\\varepsilon_0}\\]

A formula with an error (should become noticeable but not break the document): $\frac{1}{$

A formula inside code is not rendered: `$x^2$`.

## Mermaid diagrams

```mermaid
graph TD
  A[Source .md] --> B{Parsing}
  B -->|block| C[MarkdownRenderer]
  B -->|inline| D[BaselineInline]
  C --> E[preview.js]
  D --> E
  E --> F[WKWebView]
```

```mermaid
sequenceDiagram
  participant R as Editor
  participant P as Preview
  R->>P: scrollToSourceLine(42)
  P->>R: postMessage({type:"scroll",line:42})
```

```mermaid
graph TD
  A[Diagram error] --> B[
```

## Miscellaneous

---

![Placeholder instead of an image](data:image/svg+xml;charset=utf-8,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%22320%22%20height%3D%22160%22%3E%3Crect%20width%3D%22320%22%20height%3D%22160%22%20rx%3D%2210%22%20fill%3D%22%23c8d4e3%22%20stroke%3D%22%237f95ad%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20x%3D%22160%22%20y%3D%2286%22%20font-family%3D%22sans-serif%22%20font-size%3D%2218%22%20fill%3D%22%233d4a5c%22%20text-anchor%3D%22middle%22%3E%D0%B8%D0%B7%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5%20320%C3%97160%3C%2Ftext%3E%3C%2Fsvg%3E "Image with data-URI")

<details>
<summary>Collapsed block</summary>
The content expands on click.
</details>

[^1]: Footnote with a backlink to the place in the text.
