---
title: "Labor: Mechanik"
date: 2022-12-20T20:37:43+01:00
type: "post"
tags: []
draft: true
---

Da es bei "Sketching with Hardware" vor allem darum geht aktive (im Besten Fall sogar inteaktive) Hardware zu erschaffen, werden wir uns heute der Bewegung von Dingen widmen. Besser ausgedrückt: der Mechanik.
Wie in den Labs zuvor teilt sich auch dieses in einen Theorie- und einen Praxispart auf.

## Theorie

Die Menge an Energie, welche durch eine Kraft übertragen wird, wird als Arbeit (work) bezeichnet. (W = Fs)
Die Geschwindigkeit, mit welcher eine Arbeit erledigt wird, nennt sich Leistung (power) (P = dW/dt)

Es gibt 4 Arten von Maschinen:

* um Energie zu transformieren (z.B. Windkraft, welche ein Windrad antreibt)

* um Energie zu übertragen (z.B. Flaschenöffner)

* um Kraft umzulenken oder zu vervielfachen (z.B. Flaschenzüge)

* um Geschwindigkeit zu erhöhen (z.B. Zahnräder)

(viele Maschinen vereinen auch mehrere der genannten Prinzipien)

Die wichtigsten Grundmechaniken, auf welchen Maschinenkonstruktion auch schon seit Jahrhunderten aufbaut, möchte ich kurz vorstellen:

* Das Grundprinzip von Hebeln basiert auf der mechanischen Kraftwandlung. Um eine Hubkraft berrechnen zu können, ist es wichtig zu wissen um welche Hebelklasse es sich handelt. Das macht sich daran aus, wie Last, Kraft und Drehpunkt auf dem Hebelelement verteilt sind. (nachreichen: Skizze Hebelklassen)

* Umlenkrollen werden dazu genutzt die Richtung einer Kraft zu ändern (z.B. dass wenn man ein Seil nach unten zieht eine Last angehoben wird) oder eine Kraft zu skalieren. Zu diesen gehört auch der Flaschenzug.

* Rad und Achse

* Rampen flachen Höhenunterschiede ab und skalieren diese stattdessen in der Ebene.

* Gewinde und Schrauben transformieren Rotations- in Liniearbewegung.

* Zahnräder übertragen Rotationen und können durch Größe und Anzahl der Zähne die Geschwindigkeit der Rotationen gezielt beeinflussen.

Da die Energie ja auch von irgendwoher initiiert werden muss wird Mechanik oft auch mit Hilfe von Motoren betrieben. Es gibt z.B.:
Servo Motoren (Rotation von 0-180 Grad, sehr präzise Positionierung mögich)
Stepper Motoren (Rotation schrittweise, sehr präzise Positionierung mögich, oft bei wiederholenden Bewegungen eingesetzt, Geschwindigkeit variabel)
Normale DC Motoren (keine Positionierung, kontinuierliche Drehung)

Ein weiterer wichtiger Begriff im Zusammenhang der Mechanik ist die Kinematik. Darunter wird Mechanik beschrieben, welche die Bewegung eines Körpers nicht anhand von dynamischen Kräften, sondern von Ort, Zeit, Geschwindigkeit und Beschleunigung beschreibt. Man spricht auch von Bewegungslehre.

## Praxis

Um nun mechanische Prinzipien selbst zu erleben, haben wir mit einem Fischertechnikbausatz folgende Beispiele nachgebaut.

### Schubkurbel

Schubkurbelgetriebe dienen dazu eine Drehbewegung (Kurbel) in eine periodische Schubbewegung zu transformieren. Eine der bekanntesten Einsatzmöglichkeiten für Schubkurbeln ist der Ottomotor, bei welchem durch Verbrennung Druckunterschiede erzeugt werden, diese einen Kolben bewegen (Schub) und diese Bewegung durch das Schubkurbelgetriebe in eine Rotation umgesetzt wird.
![Viertakt Ottomotor](viertakt-ottomotor.gif)

[https://de.wikipedia.org/wiki/Ottomotor]

![kurbel](20221214_133757.gif)

### Drei-Gang Schaltgetriebe

Schaltgetriebe sind dafür nötig eine Drehzahlen zu übersetzen. Z.B. generiert der oben genannte Ottomotor die Motordrehzahl. Um diese effektiv zu nutzen (Justierung der Fahrtgeschwindigkeit) muss diese in eine veränderbare Antriebsdrehzahl (wie schnell sich die Räder drehen sollen) verändert werden. Hierfür nutzt man Schaltgetriebe.

![getriebe](schalt.gif)

[https://www.autogyar.hu/autotechnika/hajtaslanc/gepjarmuvek-eroatviteli-berendezesei-a-sebessegvalto-20150102]

![getriebe](20221214_145730.gif)

Eine andere Variante der Schaltgetriebe sind Planetengetriebe.

![Planetengetriebe](planet.gif)
[https://www.pinterest.co.kr/pin/2040762323476502]

### Rotierende Plattform

Das letzte Praxisbeispiel war eine rotierende Plattform, welche mit einem kleinen Motor angetrieben wurde. Mit einem vom Motor in Bewebung gebrachten Gewinde wird ein Zahnrad rotiert. Das Prinzip solcher Plattformen findet man z.B. als Drehbühne im Theater oder als Drehscheibe für Schienenfahrzeuge.

![getriebe](20221214_172100.jpg)


