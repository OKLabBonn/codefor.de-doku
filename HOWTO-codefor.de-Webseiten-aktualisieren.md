# HOWTO: codefor.de Webseiten aktualisieren
*Initial erstellt von [Stefan Wolfrum](https://twitter.com/metawops), [OK Lab Bonn](mailto:info@codeforbonn.de). September 2015.*


## Einleitung / Setup
Hier steht etwas über Git(Hub), was man sich am Rechner installieren muss (Minimum / Maximum; Maximum für wenn man selbst lokal die Seiten bauen lassen will, um das Ergebnis vorab sehen zu können), welches Repository man forken und sich danach klonen muss, wie das codefor.de Repository überhaupt aufgebaut ist, welche Technologien benutzt werden für welche Aufgabe, welches grundsätzliche Format (Markdown, HTML, ...) welche Dateien haben etc.

Es folgen verschiedene *use cases*.

## Neues Projekt hinzufügen

- Im lokalen, geklonten Fork des codefor.de Repositories auf dem eigenen Rechner im Verzeichnis `projekte` eine neue Datei anlegen.
- Name: `yyyy-mm-dd-[cc-]name.html`. Dabei bedeuten
	- **yyyy**: Jahr, vierstellig
	- **mm**: Monat, immer genau zweistellig (ggf. führende 0)
	- **dd**: Tag, immer genau zweistellig (ggf. führende 0)
	- **cc**: [optional] City Code, genau zweistellig, in Anlehnung an Kfz-Kennzeichen, aber mit Ausnahmen, z.B. hat Berlin hier `BE` gewählt
	- **name**: beliebiger Text, der sich auf das Projekt bezieht
- Datei hat zwar die Endung .html, ist aber keine reine HTML Datei. Kann aber auch HTML enthalten, s.u.
- Am besten eine vorhandene Datei als Vorlage nehmen, also kopieren und dann anpassen.
- Die Datei besteht aus zwei Blöcken, jeder Block beginnt mit auf einer eigenen Zeile stehenden drei Minuszeichen `---`.
- Der erste Block enthält key-value artige Einträge, der zweite Block eine verbale Beschreibung des Projektes (hier kann dann auch einfaches HTML z.B. für Fettschrift, harte Zeilenumbrüche etc. benutzt werden)
- Im ersten Block sind die genannten key-value-Paare wie folgt, jeweils auf einer Zeile:
	- `layout: project` – fix
	- `lab: OK Lab Bonn` – fix; wichtig ist hier, dass der Name des OK Labs korrekt geschrieben werden muss. Anhand dieser Information ordnet das nachgelagerte System das Projekt dem richtigen OK Lab zu. (**Offene Frage**, die beantwortet werden muss: woher weiß man, wie das eigene OK Lab korrekt geschrieben wird, damit diese Aggregation funktioniert? Wo sind die korrekten OK Lab Namen zum Nachschlagen aufgelistet?)
	- `imgname: bonn/bilddateiname.png` – Ein Projekt kann ein Bild enthalten. Dieses Bild ist abzulegen im Ordner `assets/projects/bonn/` und kann ein übliches Web-Bilddatei-Format haben. Der Ordner mit dem OK Lab Namen (hier: `bonn`) ist dem Bilddatei-Namen voranzustellen.
	- `title: <Titel>` – Hier steht die Überschrift des Projektes. Sollte nicht all zu lang sein
	- `status: <Status>` – Hier steht der Status des Projekts. Verwendet wurden an der Stelle Begriffe wie "In Progress" oder "Needs help". Ich habe schlicht auch "Fertig" benutzt, wobei hier **offen** ist, auf welche Begriffe man sich schon geeinigt hat, welche man verwenden sollte, damit hier nicht zu viele Stilblüten entstehen und jeder etwas anderes schreibt, aber alle doch das selbe meinen.
	- `links:` – Dies ist ein besonderes keyword, da nach dem Doppelpunkt nicht einfach ein *value* folgt. Stattdessen ein selbsterklärendes Beispiel (sollte man aber vermutlich auch nochmal formal beschreiben):

            links:
            - url: http://bonn-o-mat.de/
              name: Der BONN-O-MAT
            - url: https://github.com/OKLabBonn/bonn-o-mat
              name: BONN-O-MAT Quellcode auf GitHub

	- `collaborators:` – Analog zu `links:` auch hier ein Beispiel (aus Berlin):

			colaborators:
			- name: Tobias Preuss
			  links:
			  - url: https://twitter.com/tbsprs
			    url-name: Twitter
	
			- name: Knut Hühne
			  links:
			  - url: https://github.com/k-nut
			    url-name: GitHub

- Der zweite Block beginnt genau wie der erste mit einer Zeile mit drei Minuszeichen `---` und enthält danach beiliebigen Freitext als Projekt-Beschreibung. Dieser kann einfache HTML tags zur Textauszeichnung enthalten.
- Die Änderungen (sollte ja in der Regel eine .html Datei und eine Bilddatei sein) committen (mit Kommentar) und dann einen Pull-Request dafür stellen.
- Theoretisch könnte man sich den dann selbst genehmigen (mergen), wenn alles fehlerfrei verlief, aber das würde keinem vier-Augen-Prinzip entsprechen und macht nicht sehr viel Sinn. Also: warten, liegen lassen, irgendwann (**wann**?) wird sich ein anderer Verantwortlicher finden und den Pull-Request mergen. **Muss präzisiert werden!**
- Es entsteht dann auf der OK Lab Übersichtsseite unten im Abschnitt "Projekte" eine neue Kachel, die oben das (optionale) Bild enthält und darunter die verschiedenen, eingetragenen Daten. Vom Beschreibungstext werden nur ca. zwei Zeilen ausgegeben, danach eine Ellipse (…). Das Bild und die Überschrift haben den Link zur eigenen Projektseite, wo dann der komplette Beschreibungstext zu lesen ist. Die URL dieser Projektseite ist dann `http://codefor.de/projekte/<Projektdateiname>`.
- **Offen** für mich: wodurch wird die Reihenfolge der Projekte auf der OK Lab Übersichtsseite bestimmt?


## Neuen Termin für ein OK Lab Treffen einstellen
- tbd.

## Beschreibung des eigenen OK Labs anpassen
- Hier auch: Personen mit ihren Accounts und Fotos hinzufügen

