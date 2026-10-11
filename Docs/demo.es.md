# Visión general de «MD Editor»

Editor nativo de Markdown para macOS y iPadOS. Este fragmento cubre **negrita**, *cursiva*, ~~tachado~~, `código en línea`, <mark>resaltado</mark>, las teclas <kbd>⌘</kbd>+<kbd>K</kbd>, una nota al pie[^1], las fórmulas $E = mc^2$ y $a^2 + b^2 = c^2$, así como superíndice<sup>2</sup> y subíndice<sub>2</sub>. Enlace externo: [example.com/docs](https://example.com/docs "Documentación"), enlace wiki: [[Nota]], relativo: [notes/other.md](notes/other.md), ancla: [a la sección «Código»](#h-kod) y [correo](mailto:hi@example.com).

## Listas

- Primer nivel
- Con una lista anidada
  - Segundo nivel: viñeta «círculo»
  - Otro elemento
    - Tercer nivel: viñeta «cuadrado»

3. La numeración empieza en tres
4. Segundo elemento
   1. Anidado: letras latinas minúsculas

### Lista de tareas

- [x] Capa de vista previa HTML/CSS/JS ensamblada
- [ ] Verificados los ocho temas
- [ ] Verificadas la impresión y la exportación

## Código

Código en línea: `let preview = MDEditorPreview()`. Abajo, un bloque con resaltado de todos los tokens del contrato.

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

## Cita y tabla

> «La tipografía es lo que hace que el texto sea legible, y no solo visible.»
>
> > Cita anidada para comprobar la sangría y la barra.

| Función | macOS | iOS |
| --- | :---: | ---: |
| Vista previa con WKWebView | sí | sí |
| KaTeX y Mermaid sin conexión | sí | sí |
| Celda ancha que debe desplazarse horizontalmente en el iPhone | sí | sí |

## Fórmulas de KaTeX

Fórmula en línea con delimitadores de dólar $e^{i\pi} + 1 = 0$ y con paréntesis \\( \\int_0^1 x^2\\,dx = \\tfrac13 \\).

$$\frac{n!}{k!(n-k)!} = \binom{n}{k}, \qquad \sum_{i=1}^{n} i = \frac{n(n+1)}{2}$$

Fórmula en bloque entre corchetes: \\[\\nabla \\cdot \\vec{E} = \\frac{\\rho}{\\varepsilon_0}\\]

Fórmula con error (debe destacarse, pero sin romper el documento): $\\frac{1}{$

La fórmula dentro del código no se renderiza: `$x^2$`.

## Diagramas de Mermaid

```mermaid
graph TD
  A[Исходник .md] --> B{Разбор}
  B -->|блок| C[MarkdownRenderer]
  B -->|инлайн| D[BaselineInline]
  C --> E[preview.js]
  D --> E
  E --> F[WKWebView]
```

```mermaid
sequenceDiagram
  participant R as Редактор
  participant P as Предпросмотр
  R->>P: scrollToSourceLine(42)
  P->>R: postMessage({type:"scroll",line:42})
```

```mermaid
graph TD
  A[Ошибка диаграммы] --> B[
```

## Varios

---

![Marcador de posición en lugar de imagen](data:image/svg+xml;charset=utf-8,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%22320%22%20height%3D%22160%22%3E%3Crect%20width%3D%22320%22%20height%3D%22160%22%20rx%3D%2210%22%20fill%3D%22%23c8d4e3%22%20stroke%3D%22%237f95ad%22%20stroke-width%3D%222%22%2F%3E%3Ctext%20x%3D%22160%22%20y%3D%2286%22%20font-family%3D%22sans-serif%22%20font-size%3D%2218%22%20fill%3D%22%233d4a5c%22%20text-anchor%3D%22middle%22%3E%D0%B8%D0%B7%D0%BE%D0%B1%D1%80%D0%B0%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5%20320%C3%97160%3C%2Ftext%3E%3C%2Fsvg%3E "Imagen con data-URI")

<details>
<summary>Bloque plegado</summary>
El contenido se despliega al hacer clic.
</details>

[^1]: Nota al pie con un enlace de vuelta al lugar del texto.
