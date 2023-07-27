---
title: "Labor: Subtraktive Fertigung"
date: 2023-01-27T15:21:55+01:00
type: "post"
tags: ["lasercutting", "cnc", "lightburn"]
showTableOfContents: false
---

## Theorie

Subtraktive Fertigung beschreibt alle Verarbeitungsprozesse bei welchem Material (stückweise) abgetragen wird (Subtraktion von Material). Da dieser Vorgang in der Realität oft irreversibel ist (bzw.nur durch aufwendige Reperaturarbeiten umkehrbar), ist es ratsam sich das Design im Voraus zu konstruieren und sich auch daran zu halten.
Klassische subtraktive Fertigungsverfahren aus dem Handwerk sind beispielsweise das Schnitzen von Modellen, Hobeln ("Wo gehobelt wird, fallen Späne." -> Späne = Ergebnis der Subtraktion), Drechseln oder Meiseln.

Da wir uns in diesem Kurs jedoch eher mit automatisierten Fertigungsverfahren beschäftigen, werde ich in meinem Blogeintrag nur auf diese Sparte eingehen. Typische Geräte zur automatisierten subtraktiven Fertigung sind CNC*-Fräsen oder Laser-Cutter (hier: Emblaser 2, auch CNC) (es gibt auch noch weitere, mir bisher unbekannte: Waterjet Cutters, Plasma Cutters, etc.) (ebenfalls subtraktiv und automatisiert ist z.B. ein Sandstrahler).

(CNC steht für Computerized Numerical Control)

Wie ich oben bereits erwähnt habe, ist ein Design bzw.ein Konstruktionsplan bei der subtraktiven Fertigung super wichtig. Bei der automatisierten subtraktiven Fertigung ist dieser Plan sogar unumgänglich, da das zu nutzende Gerät sonst nicht weis wie es agieren soll.
	
Es gibt 2D und 3D Modelle. Das wichtigste für beide Modellarten ist dass es vektorbasierte Zeichnungen sind.  Das ist daher so wichtig, da das Gerät durch berechnete Kurven gesteuert wird. Softwares zum Erstellen und Bearbeiten der Modelle gibt es zahlreiche.
Für Laser-Cutting haben wir Lightburn genutzt. Das ist eine kostenfreie 2D Software in welche man eine SVG hochladen und dann bearbeiten oder direkt erstellen kann. Außerdem bereitet das Programm die Software für das Gerät auf (Berechnungen etc.), connected sich zu diesem und man kann den Fertigungsprozess von dort aus starten.
Für CNC-Fräsen kann man 2D Modelle nutzen (einfache Sägearbeiten) oder auch 3D Modelle (auf die 3D Modellierung werden wir im nächsten Labor zu Additiven Fertigungen eingehen). Als Software dazu haben wir Fusion 360 kennengelernt (Autodesk, kostenlose 30-Tage Testversion oder Studentenlizenz).
	
Theoretisch (haben die Fräse im Lab nicht ausprobiert) kann ich auf wichtige Punkte der Fräse eingehen, welche es zu beachten gilt:

* Bittiefe beachten -> tiefer als ein Bit lang ist kann nicht gefräst werden (es gibt jedoch Tricks und Methoden das zu umgehen: wenn man z.B. so freigräbt, dass der Bohrerkopf reinpasst)
	
Was man beim Laser-Cutting beachten sollte:

* genaue Positionierung des Materials (wird nicht gescannt)
* leichte Objekte können durch die Air-Funktion verrutschen. Daher ist es ratsam sie irgendwie zu fixieren. Z.B. mit kleinen Gewichten (mein Probestück ist mir leider etwas verrutscht, weswegen dann aus einem Quadrat ein leichtes Rechteck wurde)
* immer daneben stehen bleiben (auch bei längeren Aktionen) -> das Prinzip vom Laser-Cutting ist, dass ein Laser einen ausgewählten Teil der Oberfläche abbrennt. Sollte etwas schiefgehen kann schnell auch das ganze Gerät brennen.

Allgemein bei Subtraktiver Fertigung zu beachten:

* es gibt immer eine gewisse "Abtragungstoleranz" welche von Gerät zu Gerät verschieden ist. D.h. das Gerät wird wahrscheinlich nie nur exakt das entfernen was man auf dem Plan hat, sondern immer ein bisschen mehr. Wenn man passgenau arbeiten möchte, sollte man daher die Toleranz des Gerätes, mit welchem man arbeitet, kennen. Hierfür gibt es eine Menge Probestücke (ähnlich einem Farbtestdruck im Tintenstrahldrucker).
* jedes Material verhält sich verschieden. Wenn man noch keine Erfahrung in der gewollten Gerät-Material-Kombi hat, lieber auch hier ein Probestück machen.

## Planung eigenes Projekt

Für mein eigenes Endprojekt in diesem Semester (Arduboy) werde ich den Laser-Cutter nicht benutzen. Jedoch die CNC-Fräse. Da wir von einer Raspberry Pi Gamestation auf einen Arduino-Mini-Gameboy umgestiegen sind (immense Preise für Raspberry Pies aufgrund von Lieferengpässen), habe ich mich von dem "Mini" in Mini-Gameboy inspirieren lassen und möchte das Gesamtprodukt möglichst klein und platzsparend gestalten. Vllt.geht das auch in die Hose, da ich noch nie wirklich am Produkt gelötet habe, trotzdem aber schon spezifische Designansprüche stelle, aber vllt.klappts ja auch. Jedenfalls soll es an einen würfelförmigen Wecker erinnern und ein Holzgehäuse haben. Dieses wird dann auch gefräst, um Platz für das Innenleben (Arduino, Platine, Akku, etc.) zu haben. Wenn noch Zeit ist bekommt der "Gamecube" eine Art Lederumschlag für Schutz und Ästhetik. Diesen könnte man mit Laser-Cutting mit eine Gravur versehen. Mit dem 3D-Drucker (additive Fertigung) werde ich noch ein Bewegungskreuz drucken, welches auf die (fürs Projekt bestellten) Hubtaster aufklicken kann.

Also zusammengefasst werde ich zur Fertigung hauptsächlich CNC-Fräse, 3D-Drucker, Handarbeit und bei Zeit Laser-Cutting benutzen.

![erster Entwurf](signal-2023-01-28-131644_003.jpeg)

Diesen ersten "klassischen" Entwurf habe ich dann nochmal auf die Seite gelegt und mich für den zweiten Entwurf entschieden.

![zweiter Entwurf](signal-2023-01-28-131644_002.jpeg)


## Praxis: Laser-Cutting

Wie oben schon einmal kurz erwähnt, bezog sich der Praxispart des Labors zu "Subtraktiven Fertigungsmethoden" auf das Laser-Cutting. Hierfür durften wir was immer wir wollen in Lightburn erstellen, bearbeiten und letztendlich lasern. Solange es sich in einem dem Lab entsprechenden Zeit- und Kostenrahmen befand.

Da man sich in der Materialauswahl so manche Faux-Pas ersparen kann möchte ich kurz noch auf die Goes und Nogoes diesbzgl.eingehen. Was sich alles mit dem Emblaser 2 (Laser-Cutter aus dem Uni-Labor) bearbeiten lässt: Holz, Filz, Baumwollstoffe, Echtleder, dickere Pappe, Acrylscheiben, Kork und noch ein paar weitere (siehe Tabelle). Von superdünnen Holzplatten, bzw.allg.leicht entflammbarem Material sollte man abraten. Uns wurde besonders oft ans Herz gelegt, dass man bei Lederbrandings darauf achten sollte dass es Echtleder ist. Denn Kunstleder besteht aus Plastik und fängt sofort an bestialisch zu stinken.

![Bild Tabelle](material_table.png)

Mein Probebranding war ein Wels auf einer dünnen Holzplatte. Ich hatte die SVG dazu noch auf dem PC und konnte sie daher in Lightburn importieren. Ich wollte bestimmte Teile der Grafik ausfüllen lassen. Dazu musste ich erst noch manuell alle Pfade miteinander verbinden um zusammenhängende Flächen zu erzeugen (gab irgendwie noch Lücken). 

![Lightburn](lightburn_one.png)
![Lightburn testroutine](signal-2023-01-28-131913.gif)

Als das dann ready war ging die Datei an den Emblaser und wurde gelasert. Ich hatte das Holzplättchen nicht fixiert, weshalb es etwas verrutscht ist. Bin ganz froh dass mir das jetzt mit dem Probestück passiert ist, da ich nun in Zukunft immer daran denken werde.

![Laser](laser.gif)
![Laser-Cutter](laser_cutting.gif)
![Emblaser](emblaser.jpg)
![Catfish on wood](wels.jpg)
