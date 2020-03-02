# Methods for investigating the RNA structurome and RNA-RNA interactome

## Kompilieren

Es wird als LaTeX-Engine LuaLaTeX benutzt.  Am Bequemsten ist das Kompilieren
mit dem Wrapper LateXmk für den bereits auch eine Konfigurationsdatei im Repo
ist die automatisch eingelesen wird:
```
$ latexmk -pvc -view=none main.tex
```

## Code Style & Typographie

Die generelle Regel ist, den LaTeX-Code möglichst so aussehen zu lassen, wie
auch der Output aussieht, sprich Freizeilen vor Überschriften, 2 Spaces nach
Satzpunkten, Matheblöcke eingerückt (mit 1 Tab von der Breite von 8 Spaces).
Innerhalb von Matheblöcken ist es aber im Sinne der Übersichtlichkeit sinnvoll
Code zu alignen.  Zusätzlich sollen möglichst 80 CPL eingehalten werden (Kommata,
Punkte im Sinne von Hanging-Punctuation/Microtypographie außen vor).
Für Anführungszeichen soll `\enquote{...}` von `csquotes` benutzt werden.
Bei Wörtern, zwischen denen nicht umgebrochen werden soll (bspw. bei `Abbildung 2`)
wird mit einer `~` ein non-breaking-space eingefügt.
Für die Matheumgebungen sollen die LaTeX-Varianten `\(...\)` und `\[...\]` und nicht
`$...$` oder `$$...$$` benutzt werden (erleichtert die Fehlersuche).
Für häufig wiederkehrende Symbole oder Symbole mit besonderer Bedeutung sollen
Makros definiert werden wie `\Plain` oder `\xor` (`\DeclareMathOperator` und
`\[re]newcommand`).
Für die Pipe (`|`) in der Matheumgebung soll `\mid` benutzt werden, sofern sie als
Operator eingesetzt wird, und für Klammern mit automatischer Größe `\left`,
`\middle` und `\right`, für Auslassungspunkte die spezialisierten Varianten für
Kommata `\dotsc` oder binäre Operatoren `\dotsb`.  Bsp.:

     Dies ist ein \enquote{tolles} Beispiel für Mathe wie \(x+y\) in \LaTeX{},
     und besonderen Makros wie \(\Plain\), als auch Display-Mathe:
     \[
     	M = \left\{ \sum_{i=0}^n \;\middle|\; (1\cdot\dotsb\cdot n) \bmod 2 = 0 \right\}
     \]


Über die Formatierung des Quellcodes hinaus sollten generelle Regeln der
Typographie eingehalten werden, sprich kein Mischen von Symbolik und Text wie
"X hat Grad < 2", sondern "X hat Grad deg(X) < 2".  Zudem sollte inline-mathe
nur für kurze Formeln benutzt werden (sonst funktioniert Blocksatz nicht) und
keine Grenzen bei Integralen, Summen, etc. benutzen um die Lesbarkeit zu erhöhen.
Des weiteren sollen Gedankenstriche als Halbgeviertstriche (`--`) gesetzt werden, 
Abkürzungen spationiert (`d.\,h.`) und `\@` genutzt werden um falschen Erkennungen
von Abkürzungen durch den TeX-Algorithmus vorzubeugen.  Dieser nimmt an, dass ein
Punkt nach einem Großbuchstaben ein Abkürzungspunkt ist und verkürzt somit den
darauffolgenden horizontalen Abstand.  Steht aber ein Großbuchstabe am Ende eines
Satzes, kann man mit `\@` einen unsichtbaren Kleinbuchstaben *vor* dem Punkt einfügen.
Zusätzlich wird `\@` genutzt um gegenteilig nach Kleinbuchstaben als Teil von
Abkürzungen einen langen Satzpunkt zu verhindern, indem *nach* dem Punkt dieses
Zeichen eingefügt wird, also:

    Dies ist ein Satz mit einem Großbuchstaben am ENDE\@.  Dies ist ein Satz
    der eine Abk.\@ enthält, d.\,h.\@ eine, die nicht am Ende des Satzes steht.

Am Ende gilt die LaTeX-Übliche Regel:  Scheint etwas unnötig kompliziert, macht
man es (fast immer) falsch :-)
