# TRANSFER.md – Übergabedokument für andere KI-Agenten

Dieses Dokument fasst zusammen, woran in diesem Repository gearbeitet wird, wie es strukturiert ist, was bereits gefunden wurde und worauf beim Weiterarbeiten zu achten ist. Ziel: Ein neuer Agent ohne Vorwissen soll in wenigen Minuten produktiv anschließen können.

## 1. Projektziel

Analyse des **GKV-Beitragssatzstabilisierungsgesetzes** ("GKV-Spargesetz"), das den Bundesrat und Bundestag zwischen Mai und Juli 2026 durchlaufen hat und am 10.07.2026 endgültig verabschiedet wurde. Zwei Arbeitsschritte:

1. **Sortierung** der als Markdown vorliegenden Original-Drucksachen zum Gesetzgebungsverfahren (abgeschlossen).
2. **Inhaltliche Änderungsanalyse**: Abgleich jeder Einzeländerung des final verabschiedeten Gesetzestextes mit dem zuvor geltenden Recht (SGB V und diverse weitere Gesetze/Verordnungen), inklusive Einordnung der Auswirkungen (laufend, Kernarbeit bisher weitgehend abgeschlossen, aber nicht 100 % erschöpfend verifiziert – siehe Abschnitt 5).

## 2. Repo-Struktur

```
/
├── README.md                          Kurzer Einstiegspunkt, verweist hierher und auf Analyse/README.md
├── TRANSFER.md                        Dieses Dokument
├── Eingangsdokumente/                 Rohdaten: 11 Original-Drucksachen als PDF→Markdown-Konvertierung
│   ├── README.md                      Chronologisches Inhaltsverzeichnis mit Ablaufdiagramm des Gesetzgebungsgangs
│   └── <Drucksache>.pdf/
│       ├── markdown.md                Volltext der Drucksache (PRIMÄRE Quelle zum Lesen)
│       └── pages/page-N/markdown.md   Einzelseiten-Rohdaten (normalerweise nicht nötig)
└── Analyse/                           Die eigentliche Änderungsanalyse (13 Dateien)
    ├── README.md                      Gesamtüberblick, Einstiegspunkt für die Analyse
    └── 01-12*.md                      Einzelanalysen, siehe Abschnitt 4
```

**Die maßgebliche Rechtsquelle** ist `Eingangsdokumente/411-26.pdf/markdown.md` (BT-Drs. 411/26) – der am 10.07.2026 vom Bundestag beschlossene, und (da der Bundesrat keinen Vermittlungsausschuss verlangt hat, siehe `411-26(B).pdf`) endgültige Gesetzestext. Alle anderen Drucksachen sind politischer Diskussionsverlauf/Begründungskontext, siehe `Eingangsdokumente/README.md` für die volle Chronologie (1. und 2. Durchgang Bundesrat).

Der Gesetzestext ändert **18 Gesetze/Verordnungen** über die Artikel 1 bis 7c (Artikel 8 regelt nur das Inkrafttreten). Artikel 1 (72 Hauptnummern + mehrere Buchstaben-Unternummern, siehe Abschnitt 5) ändert allein das SGB V und macht den mit Abstand größten Teil aus.

## 3. Inhaltlicher Kern des Gesetzes (Kurzfassung)

- **Einnahmen der GKV werden gestärkt:** neuer Beitragszuschlag für familienversicherte Ehegatten (§ 242b SGB V, neu), höhere Beitragsbemessungsgrenze, höhere fiktive Bürgergeld-Bemessung, dynamisierter Minijob-Arbeitgeberbeitrag.
- **Ausgaben werden gebremst:** gekürzter Bundeszuschuss (§ 221), **Halbierung der Tarifrefinanzierung** in Krankenhäusern/Psychiatrie/häuslicher Pflege, dauerhafter Arzneimittel-Herstellerabschlag, neues Rabattvertragsinstrument, gekürzter Zahnersatz, höhere Zuzahlungen, Ausschluss von Homöopathie/Anthroposophie aus dem GKV-Katalog.
- **Strukturneuerung:** "Teilarbeitsunfähigkeit"/"teilweises Krankengeld" (§ 44c SGB V, neu) mit Folgeänderungen durch fast das gesamte Sozialrecht.
- **Psychotherapie (politisch und für den Nutzer persönlich besonders relevant, siehe Abschnitt 6):** ersatzlose Streichung der gesetzlichen Angemessenheitsprüfung für Psychotherapeuten-Honorare (§ 87 Abs. 2c SGB V) sowie Rückführung der Erwachsenenpsychotherapie in die budgetierte Gesamtvergütung.
- **Pflegepersonal im Krankenhaus:** mehrfache, sich gegenseitig verstärkende Deregulierung – Aufhebung der Pflegepersonalbemessungsverordnung, Ausdünnung der §§ 137k-n SGB V zu einer Generalklausel, Wegfall der Wirtschaftlichkeitsvermutung für tariflich bezahlte Pflegegehälter (§ 6a KHEntgG).
- **Politischer Streitpunkt:** Mehrere Länder kritisierten vor allem die Tarifrefinanzierungs-Kürzung und die unzureichende Bundesfinanzierung versicherungsfremder Leistungen; der Bundestag hat diese Kritik im finalen Text **nicht** übernommen. Sechs Länder beantragten deshalb den Vermittlungsausschuss (411-1-26.pdf), der Bundesrat lehnte das aber ab – das Gesetz ist damit final.

Details, Paragraph für Paragraph, in den Einzeldateien (Abschnitt 4).

## 4. Die 13 Dateien in `Analyse/` im Überblick

| # | Datei | Inhalt |
|---|---|---|
| — | `README.md` | Gesamtüberblick, Einnahmen/Ausgaben-Bilanz, Einordnung der Bundesrats-Kritik, Inkrafttreten-Fahrplan |
| 1 | `01-sgb5-leistungsrecht-teil1.md` | Art. 1 Nr. 1–15 + 12a (§§ 2–36 SGB V): Therapierichtungen, Familienversicherung, Verwaltungsausgaben |
| 2 | `02-sgb5-versorgung-verguetung-teil2.md` | Art. 1 Nr. 17–38 (§§ 44c–92b SGB V): Teilarbeitsunfähigkeit, Zahnersatz, vertragsärztliche Vergütung |
| 3 | `03-sgb5-wirtschaftlichkeit-arzneimittel-teil3.md` | Art. 1 Nr. 39–56 (§§ 106b–134a SGB V): Tarifschutz-Kürzungen, Arzneimittelrabatte |
| 4 | `04-sgb5-finanzen-sonstiges-teil4.md` | Art. 1 Nr. 57–72 (§§ 140a–430 SGB V + Anlage 1): Bundeszuschuss, § 242b, Abrechnungsprüfung |
| 5 | `05-sgb-folgeaenderungen-teilarbeitsunfaehigkeit.md` | Art. 1a, 2, 2a–2d (SGB III/IV/VI/IX/XI/XII): Ausstrahlung der Teilarbeitsunfähigkeit |
| 6 | `06-krankenhausfinanzierung.md` | Art. 3–5 (KHEntgG, KHG, BPflV): Tarifrefinanzierung – politisch brisantester Teil |
| 7 | `07-verordnungen.md` | Art. 6–6c (RSAV, MePMV, GebO BMG, PflBemV) |
| 8 | `08-landwirtschaft-kuenstlersozialversicherung.md` | Art. 7–7c (KVLG 1989, AAG, ALG, KSVG) |
| 9 | `09-auswirkungen-auf-pkv-versicherte.md` | Querschnittsanalyse: warum auch PKV-Versicherte über gemeinsame Versorgungsinfrastruktur betroffen sind |
| 10 | `10-psychiatrie-psychotherapie-gesellschaftliche-folgen.md` | Querschnittsanalyse: Kürzungen bei Psychiatrie/Psychotherapie, gesellschaftliche/transgenerationale Folgen |
| 11 | `11-psychotherapie-honorar-angemessenheitspruefung.md` | **Wichtige Korrektur** zu Art. 1 Nr. 31 (§ 87 Abs. 2c SGB V) – siehe Abschnitt 5 |
| 12 | `12-fehlende-nummern-56a-56e.md` | **Wichtiger Nachtrag**: 6 komplett fehlende Änderungspunkte – siehe Abschnitt 5 |

Jede Datei folgt (bei den nummerierten Gesetzesanalysen 01–08) dem Schema: Überblick → je Einzeländerung **Bisherige Rechtslage / Neue Regelung / Auswirkung**. Korrekturen aus dem Nachaudit sind im Fließtext mit `**Korrektur/Ergänzung:**` markiert – nichts wurde stillschweigend überschrieben, das ist absichtlich so, um Nachvollziehbarkeit zu erhalten.

## 5. Kritische Lektionen aus dem bisherigen Arbeitsprozess (UNBEDINGT LESEN)

Die erste Analyserunde (8 parallele Agenten) enthielt echte Fehler. Ein Nutzer-Hinweis ("Ich meine gesehen zu haben, dass Psychotherapie über GKV quasi ums Überleben kämpft") deckte auf, dass die automatisierte Analyse einen wichtigen Punkt übersehen hatte. Die Ursachenanalyse ergab **zwei systematische Fehlertypen**, die bei künftiger Arbeit an diesem oder ähnlichen Gesetzestexten aktiv vermieden werden müssen:

**Fehlertyp A – Satzverschiebung durch mehrstufige Änderungen:** Wenn eine Nummer mehrere Teiländerungen (Buchstabe a, b, c bzw. aa, bb, cc) an derselben Norm vornimmt, verschieben frühere Teiländerungen (z. B. Zusammenlegen zweier Sätze) die Zählung aller nachfolgenden Sätze. Das Gesetz markiert das teils explizit ("neuer Satz X", "neue Sätze X bis Y"), teils implizit. Eine spätere Teiländerung, die sich auf "Sätze 7 bis 9" bezieht, kann dadurch einen ganz anderen (und inhaltlich wichtigeren) Satz treffen, als die ursprüngliche, unverschobene Nummerierung suggeriert. **Konkret passiert bei § 87 Abs. 2c SGB V:** Die dortige Streichung "neue Sätze 7 bis 9" traf durch eine vorherige Satzverschmelzung nicht nur einen (unwichtigen) Kurzzeittherapie-Zuschlag, sondern auch die zentrale gesetzliche **Angemessenheitsprüfung für Psychotherapeuten-Honorare** – von der ersten (paraphrasierenden, nicht satzgenauen) Analyse übersehen. Korrigiert in Datei 02 und ausführlich dokumentiert in Datei 11.
→ **Gegenmaßnahme:** Bei "Sätze X bis Y werden ersetzt/gestrichen"-Konstruktionen mit vorgelagerten Teiländerungen im selben Absatz: Primärquelle (gesetze-im-internet.de) satzgenau, durchnummeriert abrufen – NICHT nur paraphrasieren lassen. Grep nach `"neue[nr]? Sätze?"` im Gesetzestext findet die vom Gesetz selbst markierten Risikostellen günstig vorab.

**Fehlertyp B – Fehlende Buchstaben-Unternummern:** Das Gesetz nummeriert manche Änderungen zusätzlich mit Buchstaben zwischen den Hauptnummern (z. B. "56a", "56b", "56c", "56d", "56e" zwischen Nr. 56 und Nr. 57; auch "12a", "65a", "67a", "0a" kommen vor). Die ursprüngliche Aufteilung der Analysearbeit auf parallele Agenten orientierte sich an Zeilenbereichen/Zahlenbereichen ("Nr. 39–56") und hat dabei 6 von 9 Unternummern (12a, 56a–56e) komplett übersehen – darunter eine bedeutsame, bislang unerwähnte Deregulierung der Pflegepersonalbemessung im Krankenhaus (§§ 137k–137n SGB V werden zu einer vagen Generalklausel zusammengelegt). Nachgetragen in Datei 01 (12a) und der neuen Datei 12 (56a–56e).
→ **Gegenmaßnahme:** Vor jeder Aufteilung der Arbeit per `grep -noE '^[0-9]+[a-z]\. '` im gesamten Gesetzestext nach Buchstaben-Unternummern suchen und diese explizit den Arbeitsaufträgen zuordnen, statt sich auf reine Zahlenbereiche zu verlassen.

**Verifikationsstand nach Nachaudit (Stand: aktuellster Bearbeitungsstand dieses Repos):**
- Fehlertyp A wurde für das **gesamte** Gesetz (alle Artikel) per Grep abgesucht; außer dem § 87-Fall wurde keine weitere Instanz gefunden (bei den anderen 6 Fundstellen war die Analyse bereits korrekt).
- Fehlertyp B wurde für das **gesamte** Gesetz abgesucht und vollständig behoben (alle 9 Unternummern erfasst).
- Zusätzlich wurde in einem gezielten, kosteneffizienten Nachaudit (3 Agenten statt erneut 8, mit Anweisung zu selektivem statt erschöpfendem WebFetch) jede Analyse-Datei noch einmal gegengelesen. Dabei wurden weitere, kleinere Korrekturen gefunden (u. a. bei § 87a, § 92b, § 170 SGB VI, und – am gewichtigsten – bei § 6a/§ 9/§ 6c KHEntgG und § 3 BPflV im Krankenhausfinanzierungsteil, siehe Datei 06).
- **Nicht** erfolgt ist eine erschöpfende, satzgenaue Vollverifikation jeder einzelnen der ~90 Änderungen gegen die Primärquelle (das wäre sehr teuer). Die Analysen 04, 07, 08 wurden im Nachaudit als vollständig fehlerfrei bestätigt; bei 01, 02, 03, 05, 06 wurden zusätzliche Korrekturen gefunden und eingearbeitet – ein Restrisiko weiterer, noch unentdeckter Fehler desselben Typs (v. a. Typ A bei komplexen mehrstufigen Normen) ist nicht auszuschließen, aber nach zwei Audit-Runden gering.

## 6. Arbeitskontext / Präferenzen des Nutzers

- **Budgetbewusstsein:** Der Nutzer arbeitet mit einem knappen Kostenbudget für diese Session und hat mehrfach um Sparsamkeit bei Subagenten gebeten. **Vor dem Start mehrerer paralleler Agenten immer zuerst prüfen, ob eine günstige, gezielte Grep/Read-Vorprüfung denselben Erkenntnisgewinn liefert.** Wenn Agenten nötig sind: klar abgegrenzte, wenige (2–3) Agenten mit expliziter Anweisung zu selektivem statt erschöpfendem Tool-Einsatz einsetzen, wie im Nachaudit erfolgreich praktiziert.
- **Psychotherapie ist dem Nutzer persönlich wichtig** (explizit so geäußert, nicht nur fachlich). Bei allem, was psychiatrische/psychotherapeutische Versorgung betrifft, besonders sorgfältig arbeiten und aktiv nach Details suchen, auch ohne explizite Nachfrage. Siehe Dateien 10 und 11 für den bisherigen Stand zu diesem Thema.
- **Sprache:** Alle Analysen und Kommunikation auf Deutsch, mit korrekter Rechtschreibung inkl. aller Umlaute/Sonderzeichen.
- **Arbeitsweise:** Der Nutzer schätzt transparente Kennzeichnung von Korrekturen (nicht stillschweigend überschreiben), ehrliche Benennung von Unsicherheiten/Quellentiefe, und knappe, klare Statusupdates statt langer Erklärtexte.

## 7. Mögliche nächste Schritte

Nicht begonnen bzw. offen, falls gewünscht:
- Weitere Vertiefung einzelner Themen (z. B. eigene Analyse zu Arzneimittelpreisen/§ 130-Komplex, oder zur Anlage 1/§ 135e-Leistungsgruppenkatalog, der bisher nur qualitativ behandelt wurde).
- Eine für Laien verständliche Zusammenfassung/Artifact als separates Kommunikationsformat (bisher sind alle Analysen als Markdown für Fachpublikum geschrieben).
- Bei Bedarf: dritte Audit-Runde mit noch engerem Fokus, falls neue Verdachtsmomente auftauchen (nach demselben kosteneffizienten Muster wie in Abschnitt 5/6 beschrieben – erst günstig grep/lesen, dann gezielt wenige Agenten).
