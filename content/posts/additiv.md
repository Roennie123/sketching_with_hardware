---
title: "Labor: Additive Fertigung"
date: 2023-02-28T16:57:42+01:00
type: "post"
tags: ["3D-Druck"]
draft: true
---

## Theorie

Wie der Name schon vermuten lässt, kann man das Grundprinzip der Additiven Fertigungsverfahren darauf herunterbrechen, dass während des Fertigungsprozesses, schichtweise Material dem Fertigungsprodukt hinzugefügt wird. Oftmals ist mit Additiver Fertigung auch 3D-Druck gemeint.
Additive Fertigung ist computergesteuert und somit wiederholbar. Dadurch hat sich der 3D-Druck gerade in der Industrie stark durchgesetzt, da Produkte seriell nach exakt dem gleichen Model erstellt werden können. Andererseits sind die Drucker individuell verstellbar und dadurch vielseitig einsetzbar. Das ist auch einer der Gründe weswegen sie vor allem im Hobbybereich sehr beliebt sind.

Die aktuell am meisten genutzten Arten von 3D-Druckern sind:

* Stereolithography (SLA) -> bestrahlt flüssiges Resin und härtet es schichtweise aus, sehr detailreiche Drucke möglich, eher für kleinere Drucke da auf Resinbecken beschränkt, Resin ist giftig (benötigt daher speziellen Standort)
![SLA](sla.gif)
* Fused Deposition Modeling (FDM) -> Klassiker unter den Hobby 3D-Druckern, relativ günstige Drucke möglich, Material: Filament (oft Kunststoff)
![FDM](fdm.gif)
* Selective Laser Sintering (SLS) -> feingranulares Material (Sandartig) wird bestrahlt und so schichtweise miteinander an gewünschten Stellen verbunden, wird vor allem in der Industrie genutzt da stark skalierbar, ziemlich teuer
![SLS](sls.gif)
* Selective Powder Deposition (SPD) -> für Objekte aus Metall, Sand als "Negativ-Modell" (wo dann kein Sand ist kommt Metallpulver hin), grober Druck (muss meistens noch nachgearbeitet werden)

*https://www.signmedia.ca/accelerating-use-3-d-printers*


Da bei computergesteuerten Fertigungen ein konkretes Modell vorhanden sein muss ist im Fertigungsprozess die Planung des Modells sehr wichtig. Das beinhaltet ein 3D-Model in Abhängigkeit zu den Eigenschaften des gegebenen Druckers, des Materials mit welchem gedruckt werden soll und der Maße des fertigen Produkts zu erstellen. Für 3D-Modelle gibt es viele verschiedene Formate (STL, OBJ, FBX, etc.).
Es gibt auch die Möglichkeit (bei vorhandener Hardware) ein Produkt zu scannen und sich anhand dessen dann ein automatisiertes 3D-Modell generieren zu lassen (mit passender Software).

Nach dem Erstellen des Modells ist der nächste Schritt in der Prozesskette des 3D-Drucks das "Slicen" des Modells. Dabei wird das 3D-Model in Scheiben geschnitten, bzw. horizontale Schichten welche dann aufeinanderfolgend gedruckt werden. Nutzende haben die Möglichkeit, hier auch selbst Einstellungen vorzunehmen (z.B. die Struktur des Drucks, die Geschwindigkeit, Stützstruktur etc.). Der Input ist eine STL-Datei, welche mitsamt aller Einstellungen in einen G-Code transformiert wird. Dieser enthält dann die Bewegungen (in Form von Koordinaten), welche der Drucker ausführen soll um das Produkt nach Wunsch fertigen zu können. Dieser Code kann dann (z.B. über eine Speicherkarte) dem Drucker übergeben werden, und wird dann ausgeführt.

Wichtig für den Druck ist dann noch die Wahl des Materials. Hier eine kleine Auswahl:

* PLA (Kunststoff -> Klassiker )
* ABS
* PETG
* TPU
* Nylon
* Polycarbonat
* Spezielle Filamente (z.B. Holz, Magnetisches, Leitendes, etc. -> meist teuer)

Dieses wird dann als Schlauch-Filament stückweise vom Drucker eingezogen und erhitzt. Das geschmolzene Filament wird dann über die ebenfalls erhitzte Nozzle abgegeben. Durch die gleichzeitige Bewegung des Druckkopfes wird somit das Material an die richtige Stelle gebracht und kann dann aushärten.

![filament](fila.png)
*https://www.reichelt.at/at/de/umleitung-auf-basfu-0025-am-04-05-2020-innofil-0025-p151917.html?GROUPID=7358&&r=1*


## Tools zur Additiven Fertigung

Im Labor haben wir mehrere 3D-Drucker zur Verfügung:

* Ultimaker 2+ (FDM)
* Ultimaker Original (FDM)
* Snapmaker (FDM)
* Creality CR10 S5 (FDM)
* Elegoo Mars 2 Pro (SLA) (wo anders untergebracht)

 Ich habe bisher nur den Ultimaker 2+ ausprobiert. Letzendlich funktionieren aber alle FDM Drucker ähnlich/gleich.

![Ultimaker](ultimaker.png)
*https://3dprintingindustry.com/news/ultimaker-releases-open-source-files-for-latest-3d-printers-60347*
 
 Über eine CAD-Software erstellt man ein 3D-Modell (z.B. über Fusion 360 oder TinkerCad) und exportiert dies als STL- oder OBJ-Datei. Diese läd man in eine Software zum Slicen (z.B. Cura). Den G-Code des Slices kann man dann dem 3D-Drucker übergeben und nach Überprüfung aller Einstellungen (auch Materialcheck) kann man dann den Druck starten. Über den G-Code bekommt man auch eine ungefähre Dauer des Druckes. Jedoch ist diese nur grob kalkuliert und kann sich auch noch ändern.


## Software

Es gibt zwar viele Programme welche es ermöglichen 3D-Modelle zu erstellen, jedoch sollte man die Wahl einer Software aufgrund des Anwendungsfalls des Modells treffen. Möchte man ein Modell erstellen um es explizit nur zu drucken, sollte die Wahl auf eine CAD-Software fallen (z.B. Autodesk Fusion 360, TinkerCad, etc.). Da diese recht intuitiv funktionieren und sich auf das für einen Druck wesentliche Konzentrieren.

![Fusion](fusion.gif)
*https://formizable.com/wp-content/uploads/2018/06/FVT4WY5J9OJ50VK.ANIMATED.LARGE_.gif*

Möchte man jedoch dass das 3D-Modell realistische Oberflächenstruktur, Farbe, etc. hat, kann man auch Software benutzen, welche Meshes bearbeitet (Blender, Meshmixer). Meshes sind Gitterstrukturen auf der Oberfläche des Objekts. Meshes ermöglichen sehr detailreiche Anpassungen des Modells. Mesh-Software hat oft sehr realistisches Rendering und ist somit vor allem für Animationen, detailreiche Skulpturen, etc. zu benutzen. Die meiste Software ist aber nicht ganz so intuitiv und für einfachen 3D-Druck daher nicht zu empfehlen. 

![Blender](blender.gif)
*https://www.blendernation.com/2017/12/15/bevelled-extrude-updates-interactive-mode-individual-extrusions*


## Fehlerpotenzial

* Oberhänge -> Da immer nur von einer Seite gedruckt wird ist bei klassischen FDM Druckern zu beachten, dass Oberhänge zu vermeiden sind. Bzw. wenn vorhanden, mit passender Stützstruktur ergänzt werden (beim Slice einstellbar).

![overhang](over.png)
*https://medium.com/bravovictornovember/3d-print-overhangs-and-how-to-deal-with-them-9eed6a7bcb5d*

* Verstopfte Nozzle -> lieber bei wichtigen Drucken immer mal wieder vorbeischauen, um rechtzeitig eingreifen zu können.

* Falsche Höhe -> wenn die Höhe der Oberfläche zu niedrig oder zu hoch eingestellt ist können Fehler passieren, da z.B. in der Luft gedruckt wird.

Um Fehler zu vermeiden ist es meist ratsam mit neuen Materialien oder Druckern Testdrucke zu machen. Hierfür gibt es einige frei zugängliche Modelle, welche die meisten Gefahrenquellen abdecken. Anhand dieser Testdrucke hat man dann meistens bessere Anhaltspunkte um die Einstellungen von Soft- und Hardware anzupassen.
