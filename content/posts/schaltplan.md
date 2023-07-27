---
title: "Labor: Schaltplan"
date: 2022-11-15T17:47:41+01:00
type: "post"
tags: ["fritzing", "arduboy"]
showTableOfContents: false
---

Sehr wichtig im Bezug auf die Elektrotechnik (letzter Post), sind Schaltpläne.
Hierfür gibt es die Software "Fritzing". Sie bietet eine Umgebung, in welcher man sich anhand von gegebenen Items Schaltpläne ausgeben lassen kann.

Die Aufgabe ist nun so einen Schaltplan für das Projekt, welches mich in diesem Semester begleiten soll, zu erstellen.

Ich habe mir Projekt 2 ausgesucht: die RetroPie Gamestation:

![Projekt_2](project2.png)
![Projekt_2](project2_zoom.png)

Um herauszufinden wie die Pins des RaspberryPi Zero belegt sind habe ich diesen Plan genutzt:

![Pinlayout_Pi_Zero](Pinlayout_RaspberryPi_Zero.png)

Demnach benutze ich die Pins 2 und 4 als Anschluss zum Strom. Alles was GPIO heißt, ist ein Pin für Input/Output. Dort habe ich dann den GLCD (Bildschirm), Lautsprecher und die Buttons angeschlossen.

Und hier mein Schaltplan dazu:

![Schaltplan](Schaltplan_Gamingconsole.jpg)

Ob das alles so richtig ist, bezweifle ich stark. Aber immerhin habe ich mir jetzt schonmal Gedanken dazu gemacht. :)
