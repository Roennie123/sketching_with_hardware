---
title: "Labor: Elektrotechnik"
date: 2022-11-09T18:48:35+01:00
type: "post"
tags: ["löten"]
showTableOfContents: false
---

Diesen Mittwoch ging es um Elektrotechnik. Aufgeteilt in zwei Einheiten, gab es einen theoretischen Einstieg in die Elektrotechnik und einen praktischen Teil, welcher ein Crashkurs in Löten und Messtechnik beinhaltete.

Die Theorie war sehr spannend und lehrreich. Grob ging es darum, was Spannung, Strom, Widerstand und Leistung ist. Insbesondere wie man sie berrechnet, denn das kann einem als Vorarbeit oder Kontrolle im Praktischen vieles Erleichtern.

Strom I = Ladung Q / Zeit t

Spannung U = Arbeit W / Ladung Q

Widerstand R = Spannung U / Strom I

Leistung P = Arbeit W / Zeit t

Ladung -> C

Zeit -> s (Sekunden)

Strom -> A (Ampere)

Spannung -> V (Volt)

Arbeit -> Nm (Newton Meter)

Widerstand -> Ohm

Sehr wichtig zu wissen ist dass die Leistungsabgabe quadratisch verläuft, was sich durch Umstellung der Formel für Leistung erkennen lässt. 

P = W / t = (W*Q) / (Q*t) = U * I

R = U / I <=> U = R * I

P = R * I^2

Daraus kann man ziehen, dass eine Verdopplung der Stromstärke, eine Vervierfachung der Leistung ergibt. Und eine Vervierfachung der Stromstärke eine Versechzehnfachung. Damit muss man sehr aufpassen, denn mehr Leistung bedeutet auch mehr Wärmeabgabe. Und dann entscheidet das Material wie es mit der Wärme umgeht (im Worst-Case z.B.mit einer Selbstentzündung).
Um das zu Verhindern und Strom "abzufangen" (passend auf alle Verbraucher zu verteilen) können Vorwiderstände eingebaut werden.

Leider kennt man nicht immer die technischen Daten aller Verbraucher um Kontrollrechnungen durchführen zu können. Hier kommt dann die Messtechnik ins Spiel.
Dazu durften wir dann auch selbst ins Labor gehen und Gelerntes in (hoffentlich) Verstandenes umsetzen.

Wichtigster Bestandteil der Messtechnik: das Multimeter (Definition Skript: misst alles und jedes).
Jedoch sollten wir ja das Berrechnen lernen. Daher machten wir einen Versuch, in welchem wir anhand von verschiedenen Strom- und Spannungs-Tupeln einen Widerstand berrechnen sollten (Wir erinnern uns R = U / I). Um alles genauer zu machen (da das Netzteil - wo der Strom rauskommt - sehr grobe Angaben macht) schlossen wir ein Multimeter an und lasen dort dann die Strom- und Spannungs-Tupel ab. Komplett eindeutig war unser Ergebnis nicht (Begründung Kursleiter: die Messgeräte sind scheiße), aber im Durchschnitt konnten wir uns auf einen Widerstand von 1000 Ohm einigen.

![Multimeter](signal-2022-11-14-214744_002.jpeg)
![Netzteil](signal-2022-11-14-214744_003.jpeg)
![Versuchsaufbau](signal-2022-11-14-214744_027.jpeg)

In einem weiteren Versuch sollte der Wert eines (anderen) Widerstandes anhand eines Spannungsteilers bestimmt werden. Dazu musste erst die Spannungsteiler-Formel umgeschrieben werden:

U_R2 = (R_2 / R_1 + R_2) * U gesamt <=> R_1 = U gesamt * (R_2 / U_R2) - R_2

Die Spannung von R2 (U_R2) haben wir gemessen und den Wert des einen Widerstands (welcher als Spannungsteiler diente) wussten wir noch vom Vorversuch (1000 Ohm). U gesamt war die im Netzteil eingestellte Spannung. Einfach alles Einsetzen und schon hatten wir den Wert von Widerstand R_1. Leider war am gemessenen Wert von R_2 irgendwas faul. Oder an unseren Umrechnungen von Volt zu Minnievolt. Keine Ahnung. Auf jeden Fall war das Ergebnis etwas merkwürdig und nicht richtig. Um tiefer in unser Scheitern dieses Versuches einzugehen, hatte die Zeit gefehlt. Trotzdem haben wir das Prinzip verstanden und können uns bei Bedarf an den Versuchsaufbau erinnern.

Dann wurde uns die Mächtigkeit eines Oszillators vorgeführt. Das ist ebenfalls ein Messgerät, mit welchem sich z.B. das Debouncing von Schaltern visualisieren lässt, um dann eine Idee davon zu haben, wie die Software angepasst werden muss.

Obwohl Messtechnik (und das Verständnis dahinter) super wichtig sind möchte ich nun noch zum spaßigsten Teil des Labs kommen: dem Löten. Hatte das vorher noch nie gemacht und war daher sehr gespannt was mich erwartet, bzw. auf was es dabei ankommt. Ob es Tricks, Kniffe, etc. gibt.

Als erstes möchte ich das ABC (Hauptausrüstung) des Lötens erläutern:
Lotzinn -> auf einer Spule. Schmilzt bei Erhitzung und bildet dann die Verbindung zwischen Platine und Stift.
Flussmittelstift -> Braucht man um das Lotzinn zum flüssig werden zu lassen. Ohne den geht garnichts. 
Lötstift -> Damit lässt sich der Lotzinn schmelten. Obacht: wird extrem heiß.
Goldener Topfkratzschwamm -> zum Lötstift säubern.
Platine/Stift -> irgendwas zum verlöten.
Kupferdraht -> damit können Fehler korrigiert werden. Saugt bei Erhitzen Lotzinn auf wie ein Schwamm.

![Lötstift](signal-2022-11-14-214744_024.jpeg)
![Kupferdraht](signal-2022-11-14-214744_026.jpeg)
![Lötstifttermostat](signal-2022-11-14-214744_033.jpeg)
![Platine, Stifte und Lotzinn](signal-2022-11-14-214744_011.jpeg)

Nun zur Vorbereitung: Stift und Platine so miteinander verbinden wie es der gewünschten Endsituation entspricht. Am besten die Platine in irgendeine Halterung klemmen, auf den Tisch legen klappt theoretisch aber auch. Hauptsache die Verbindung bleibt stabil. Dann mit dem Flussmittelstift großzügig den zu verlötenden Bereich "bewässern". Lötstiftgerät einschalten.

Der Prozess: Mit dem Lötstift die zu lötende Stelle erhitzen. Nun wird zwischen den Lötstift und der Platine die Spitze des Lötzinn-Drahtes geschoben. Diese schmilzt und lötet. Zu beachten ist, dass genau die richtige Menge an Lotzinn auf der Platine landet: so viel dass alles hält, aber auch nicht zu viel, da sonst Noppen entstehen an welchen irgendwas hängen bleiben könnte, oder mehrere Stifte miteinander verbunden werden.

Es hat alles schon ziemlich gut geklappt, aber ich denke, dass man mit ein paar Übungsversuchen mehr den Dreh dann relativ schnell raushat und auch genau weis worauf es wirklich ankommt. Denn das lernt man ja am besten durch eigene Anwendungen. :)

Hier kommen Impressionen zum Löten:

![Flussmittel auf der Platine auftragen](signal-2022-11-14-214744_023.jpeg)
![Löten](signal-2022-11-14-214744_030.jpeg)
![Hier ist der Lotzinn leider etwas zu großzügig geflossen](signal-2022-11-14-214744_016.jpeg)

Zu guter Letzt noch ein paar Fachbegriffe aus der Vorlesung: Reihenschaltung, Parallelschaltung, Spannungsteiler, Elektrolyt- und Keramikkondensatoren. Wer wissen möchte was die machen, kann es selbst recherchieren. Dieser Post sollte nämlich nun auch mal ein Ende finden. :)
