# Kalibrierungs Guide
Eine Anleitung zur Kalibrierung des Filaments für jeden Drucker mittels der Kalibrierungsmöglichkeiten im OrcaSlicer.
## 1. Volumetric Speed ermitteln
### Im OrcaSlicer
 - "Kalibrieren" --> "more" --> "Maximale Flussrate"
 - Im Popup Fenster die Werte anpassen.
    - Phaetus Rapido HF: 
        - von: 28
        - bis: 50
        - Rate: 0,5
    - Phaetus Rapido UHF:
        - von: 30
        - bis: 60
        - Rate: 0,5
    - Goliath:
        - von: 50
        - bis: 80
        - Rate: 0,5
- An Drucker senden
Den Druck beobachten bis die Schichten nicht mehr gut aussehen und dann den Druck abbrechen.

### Nach dem Druck
Mit einem Messchieber vom Boden aus, bis kurz bevor der Druck nicht mehr gut aussieht, messen. Danach wird folgende Formel angewand um die neue Flowrate einzustellen:

$$ Flowrate = Anfangswert + Messwert \times Rate $$

Diese Flowrate wird im Filament hinterlegt und gespeichert.

## 2. Flowrate
### Erster Durchlauf
#### Im OrcaSlicer 
 - "Kalibrieren" --> "Flow Rate" --> "Durchgang 1"
Druck starten und warten bis dieser fertig ist.

#### Nach dem Druck
Alle Pattern ansehen und entscheiden, wo die Flussrate am besten ist und liest den Modifier ab

$$ FlowRatio_neu = FlowRatio_alt \times \cfrac{105 + Modifier}{100} $$

Diesen Wert bei "Flussverhältnis" eingeben und das Profil speichern.

### Zweiter Durchlauf
#### Im OrcaSlicer 
 - "Kalibrieren" --> "Flow Rate" --> "Durchgang 2"
Druck starten und warten bis dieser fertig ist.

#### Nach dem Druck
Alle Pattern ansehen und entscheiden, wo die Flussrate am besten ist und liest den Modifier ab

$$ FlowRatio_neu = FlowRatio_alt \times \cfrac{100 + Modifier}{100} $$

Diesen Wert bei "Flussverhältnis" eingeben und das Profil speichern.

## Pressure Advance
### Im OrcaSlicer 
 - "Kalibrieren" --> "Pressure Advance"
 - Im Popup:
    - Bei Direct Extruder:
        - Extruder Typ: Direct Exruder
        - Method: PA Line
        - Start PA: 0
        - Ende PA: 0.1
        - PA Schritte: 0.002
    - Bei Bowden:
        - Extruder Typ: Bowden
        - Method: PA Line
        - Start PA: 0
        - Ende PA: 1
        - PA Schritte: 0.02
Druck starten und warten bis dieser fertig ist.

### Nach dem Druck
Das Patter ansehen und die Schnittschellen bei den Geschwindigkeitsänderungsmarken überprüfen. Es wird der Wert gewählt, bei dem die Linie gleichmäßig über die gesamte Länge ist.
Diesen Wert im Filament unter "Pressure Advance" eintragen und speichern.

## Retraction
### Im OrcaSlicer 
 - "Kalibrieren" --> "Retraction"
 - Im Popup: 
    - Start Retraction-Länge: 0
    - Ende Retraction-Länge: 5
    - Schrittweite: 0.1
Den Druck starten und beobachten. Wenn das Ergebnis gut aussieht und mehrere Schichten kein Stringing zusehen ist, kann der Druck abgebrochen werden.

### Nach dem Druck
Den Druck messen, wo das Stringing nicht mehr vorhanden ist und mit der Formel den neuen Wert errechnen:

$$ new_retraction = start_retraction + Messwert \times Schrittweite $$

## Der Drucker sollte nun auf das Filament abestimmt sein ;)

