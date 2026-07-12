# Der Weg des Gesetzes (Chronologie)

Das GKV-Spargesetz hat einen komplexen parlamentarischen Weg mit vielen Schleifen und Einwänden durchlaufen, bevor es endgültig verabschiedet wurde. 

Das folgende Diagramm zeigt den Ablauf des Gesetzgebungsverfahrens – vom ersten Entwurf bis zum heutigen, finalen Stand.

```mermaid
graph TD
    A["Bundesregierung:<br/>Gesetzentwurf<br/>01.05.2026"] --> B
    
    subgraph BR1 ["1. Durchgang (Bundesrat)"]
        B["Ausschüsse beraten<br/>(Empfehlen 48 Änderungen)"] --> C
        C["Länder stellen eigene Anträge<br/>(z.B. zur Krankenhausfinanzierung)"] --> D
        D["Bundesrat verfasst<br/>offizielle Stellungnahme<br/>12.06.2026"]
    end
    
    D --> E
    
    subgraph BT ["Bundestag"]
        E["Bundestag ignoriert<br/>viele Länder-Kritikpunkte"] --> F
        F["Bundestag verabschiedet<br/>das finale Gesetz<br/>10.07.2026"]
    end
    
    F --> G
    
    subgraph BR2 ["2. Durchgang (Bundesrat)"]
        G["6 Länder fordern<br/>Vermittlungsausschuss"] --> H{"Plenum stimmt ab<br/>10.07.2026"}
        H -->|"Mehrheit lehnt<br/>den Antrag ab"| I
        H -.->|"Antrag angenommen"| VA["Vermittlungsausschuss<br/>*fand nicht statt*"]
    end
    
    I(("📍 WIR SIND HIER<br/><br/>Das Gesetz ist unverändert<br/>und final beschlossen!"))
    
    classDef current fill:#ffcc00,stroke:#d35400,stroke-width:3px,color:#000,font-weight:bold;
    class I current;
```

---

> ℹ️ **Möchten Sie die genauen Originaldokumente zu den jeweiligen Schritten einsehen?**  
> Alle PDFs (wie die Ausschussempfehlungen, die Anträge der Länder und den finalen Gesetzesbeschluss) finden Sie chronologisch geordnet unter **[Original-Dokumente](../Eingangsdokumente/README.md)**.
