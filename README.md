# seminar-paper-latex

LaTeX-Template für Seminararbeiten, formatiert für maximale Annäherung an Microsoft Word mit klassischer Times-New-Roman-Konfiguration.

## Kompiler

Das Template benötigt **XeLaTeX**, damit Times New Roman direkt als Systemschrift über `fontspec` geladen werden kann.

```
% !TEX TS-program = xelatex
```

## Formatierung

| Eigenschaft | Wert |
|---|---|
| Schriftart | Times New Roman, 12pt, schwarz |
| Zeilenabstand | 1,5 Zeilen (`\setstretch{1.5}` → 21,75pt Baseline; Word: 21,6pt → Δ +0,15pt/Zeile) |
| Seitenränder | 2,54 cm rundum (Word „Normal") |
| Absatzabstand | 8pt nach Absatz, 0pt davor, keine Einrückung |
| Überschriften | h1: 16pt, h2: 14pt, h3: 13pt – alle fett, schwarz |
| Fußnoten | 10pt, einzeilig |
| Seitenzahlen | Unten zentriert, 12pt, keine auf dem Deckblatt |
| Ausrichtung | Blocksatz mit deutscher Silbentrennung |
| Links/Hyperlinks | Alle schwarz, keine farbigen Rahmen |

## Referenzen

Als Bibliographiebackend wird **Biber** verwendet (nicht bibtex).

Unter `\addbibresource{.../.bib}` muss die jeweilige .bib-Datei mit der Literaturliste angegeben werden.

### Kurzzitate

Es wurde eine Funktion für „Kurzzitate" erstellt, z.B. für Aristoteles oder Wittgenstein. Im Text wird `\shortcite` verwendet. In der .bib-Datei muss dafür ein Attribut angegeben werden:

```bibtex
shorthand = {Arist. De an.}
```

### Zitierweise

- Normales Zitat: `\parencite[Seite(n)]{cite-key}`
- Kurzzitat: `\shortcite[Stelle]{cite-key}`
- Blockzitat:
  ```latex
  \begin{displayquote}
      \enquote{Inhalt} % direktes Zitat
  \end{displayquote}
  ```

Das Literaturverzeichnis wird automatisch auf Basis der zitierten Literatur erstellt.

## Dateistruktur

```
seminararbeit.tex      Hauptdatei
settings/
├── packages.tex       Alle Paket- und Formateinstellungen
└── cover.tex          Deckblatt & Inhaltsverzeichnis
```

## Bekannte Abweichungen von Word

| Abweichung | Ursache | Größenordnung |
|---|---|---|
| Zeilenumbrüche | Word: Greedy; LaTeX: Knuth-Plass (optimal) | Unterschiedliche Umbruchstellen |
| Baseline-Abstand | Word: 21,6pt; LaTeX: 21,75pt | +0,15pt (≈ 0,05mm) pro Zeile |
| Silbentrennung | Word: standardmäßig aus; hier: aktiv | Bewusste Abweichung |
| Schriftmetriken | Unterschiedliche Rendering-Engines | Minimale Laufweitenunterschiede |
| Fußnotentrennlinie | LaTeX: ~⅓ Spaltenbreite; Word: ~5 cm | Kann ~1 cm abweichen |
