#### Handhabung NP-schwerer Algorithmen


Vertex Cover: alle Kanten eines Graphen sind abgedeckt, durch Knoten des VC 
Independet Set: alle Knoten des IS sind paarweise nicht adjazent
Dominating Set: für alle Knoten des Graphens gilt, der Knoten ist in DS oder sein Nachbar 

Sei G und X ein VC. Dann ist G\X ein IS ==> man kann untereinander gut switchen 

1. Hofft auf Sondernfall: VC auf BT 
Process: Wenn man einen Knoten v mit deg(v) = 1, dann ist der Nachbar mindestens genau so gut, kannaber auch besser sein. 
Bei BT: fange von den Blättern an und wähle den Parent. Lösche nach jedem Schritt alle Kanten vom ausgewählten Knoten v, sowie Knoten die deg(1) haben. 

2. Parametrisierte Algorithmen:
hier hat man neben den Problem noch einen Parameter (bzw. können mehrere sein) $k \in \N$ welcher uns mehr Informationen gibt und hilft das Problem einzuschränken. Bei VC-Problemen kann k die Anzahl an Knoten im VC bedeuten. => Suchbaumalgorithmus mit Höhe k; also (2^k * (m+n)) Laufzeit. 

Frage: wieso 2^k * (m+n). 2^k ist die Anzahl an Knoten im Suchbaum. Und diesen ruft man ja für jede Kante auf. 

=> laut nml: sind die einfachen Operationen pro Rekursionsaufruff, um den Graphen zu kopiere, Knoten und Kanten zu löschen und den nächsten Rekursionsschritt aufzurufen 
