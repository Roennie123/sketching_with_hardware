---
title: "Labor: Microcontroller"
date: 2022-11-30T17:44:17+01:00
type: "post"
tags: ["arduino"]
draft: true
---

Die letzten drei Labore handelten von Microcontrollern. Arduinos sind die mitunter bekanntesten Microcontroller, da sie "genormt" sind. Viele andere Hersteller halten sich an diese Normung. Mikrocontroller werden mit C programmiert (was garnicht so schwer ist wie man zuerst denkt, wenn man noch nie was mit C gemacht hat). Für die optimale Arbeitsumgebung haben wir uns eine Arduino IDE installiert. Darüber lassen sich die passenden Libaries zu den Bauteilen direkt suchen, installieren und einbinden. Ansonsten hat die IDE natürlich auch noch viele weitere Vorteile, auf die ich jetzt aber nicht eingehen möchte.

Am wichtigsten bei der Verkabelung und Programmierung von Mikrocontrollern ist das Wissen darüber, welcher Pin für was zuständig ist. Ohne dieses Wissen wird vermutlich auch nichts funktionieren. :D Hier ist ein Pinlayout des Arduino Uno R3:
![Pinlayout Arduino R3](arduinoUnoR3_pinlayout.jpg)
https://i.stack.imgur.com/dVkQU.jpg

Alle türkisfarbenen Pins sind digitale Anschlussstellen (z.B. für LEDs etc), alle grünen Pins sind analog. Das bedeutet, dass hier Signalvarianzen angeschlossen werden können, wie z.B. Lautsprecher etc. Zusätzlich gibt es noch PWM (pulse width modulation) Pins (rot): das sind "semi-analoge" Digital-Pins (auf dem Board mit ~ gekennzeichnet).
Die orangenen Pins sind für Bauteile mit serieller Kommunikation wichtig.
Was man auf jeden Fall immer braucht sind die schwarzen Pins mit 5V (oder 3.3V) für die Stromversorgung des Pluspols und GND (ground) für den Minuspol und um den Kreis zu schließen.

Hauptsächlich haben wir rumprobiert, was wir Cooles mit den gegebenen Bauteilen (Sensoren, Motoren, Displays, LEDs, etc.) machen können. Hier sind meine Versuche:

### Blinkende LEDs (Output)

![blinkende LED](signal-2022-12-07-181505.gif)

Die LED (light-emitting diode) wird über einen Digitalpin angeschlossen. Im Code wird dann der Pin als Output initialisiert. Microcontroller lassen sich am besten über einen Loop programmieren, welchen sie speichern und dann immer wieder abspielen können. Bei der blinkenden LED wird im Loop eine Leuchtdauer definiert und eine Pause. Bei Outputs spricht man die am Pin angeschlossene Hardware mit **digitalWrite(pin, wert)** an. Es folgt ein Codebeispiel wie das für 2 LEDs aussehen könnte:
```Shell
void setup() {
  pinMode(8, OUTPUT);
  pinMode(9, OUTPUT);
}

void loop() {
  digitalWrite(8, HIGH);  // turn the LED on (HIGH is the voltage level)
  delay(100);  
  digitalWrite(9, HIGH);  // turn the LED on (HIGH is the voltage level)
  digitalWrite(8, LOW);   // turn the LED off by making the voltage LOW
  delay(100); 
  digitalWrite(9, LOW);   // turn the LED off by making the voltage LOW
}
```
![blinkende LED](signal-2022-12-07-181538.gif)
![blinkende LED](signal-2022-12-07-181555.gif)

### Taster (Input)

Hubtaster (Buttons) sind Bauteile um Input zu kommunizieren. Also: das System bemerkt, wenn der Button gedrückt wurde, und reagiert ggf. darauf. Input wird im Cood mit **digitalRead(pin)** ausgelesen.
![Verkabelung von Pushbutton](signal-2022-12-07-174920_002.jpeg)
![Verkabelung von Pushbutton](signal-2022-12-07-174920_003.jpeg)

Kombination von Input und Output: wenn das System über den Taster einen Input bekommt (also dieser gedrückt wurde), gibt es einen Output (die LED leuchtet):
```Shell
unsigned int button_status = 0;

void setup() {
  pinMode(13, INPUT_PULLUP);
  pinMode(12, OUTPUT);
}

void loop() {
  button_status = digitalRead(13);
  if(button_status == 0){
    digitalWrite(12, HIGH);
  } else{
    digitalWrite(12, LOW);
  }
}
```
![Verkabelung von Pushbutton](signal-2022-12-07-174920_009.jpeg)

### LED Matrix (inkl. serielle Kommunikation)

Eine LED-Matrix sind im Prinzip mehrere LEDs auf einer Platine, welche einzeln angesprochen werden können. Das praktische ist, das man aber nur 5 Pins für den Anschluss braucht (VCC: 5V, GND, DIN, CS: ~, CLK: ~). LED-Matrizen benutzen serielle Kommunikation. Dadurch lassen sich mehrere hintereinander schalten.
![LED Matrix](signal-2022-12-07-181619.gif)


Ich habe zusätzlich noch einen Joystick als Input-Hardware angeschlossen. Bei diesem habe ich dann im Code die x- und y- Koordinaten in oben, unten, rechts und links eingeteilt. Je nachdem welche Richtung entgegengenommen wird, wird der passende Pfeil auf der Matrix angezeigt (leider spiegelverkehrt, da beide Matrizen aufgrund der Kabel nur übereinander aufs Video gepasst haben).
![Aufbau serielle LED Matrix](signal-2022-12-07-174920_012.jpeg)
![LED Matrix mit Joystick](signal-2022-12-07-181647.gif)

LED-Bänder benutzen ebenfalls (in der Regel) Protokolle mit serieller Kommunikation (z.B. SPI oder I2C). Mit der passenden Libary kann man dadurch dann auf jede LED einzeln, oder alle zusammen als Output zugreifen. Habe mich selbst an einem LED-Band versucht, aber etwas beim Löten gepfuscht, sodass es einen leichten Wackelkontakt hatte und immer ein paar LEDs ausgelassen wurden.
![serielle Kommunikation mit LED-Band](signal-2022-12-07-181414_002.jpeg)


### LCD Bildschirm

Den kleinen LCD habe ich angeschlossen, und als direkte Ausgabe des Seriel Monitors der Arduino IDE genutzt. Also alles was ich in die IDE eingegeben habe, wurde dann auf dem Display eingeblendet. Dazu braucht man natürlich eine Libary. Eine kleine Schwierigkeit dabei, war das Entfernen des Enter-Zeichens in der Anzeige (um zu kommunizieren dass die Eingabe vollständig ist und angezeigt werden soll wurde Enter gedrückt. Das war dann immer ebenfalls sichtbar auf dem Display). Hat dann aber auch geklappt, indem der Input in einen String (Char-Array) umgewandelt wurde und dann einfach das letzte Zeichen entfernt.
![LCD](signal-2022-12-07-181631.gif)


### Motoren

Um auch mit den Motoren warm zu werden habe ich den **Micro Servo 9g** an den Arduino angeschlossen. Zusätzlich noch einen Joystick. Mit dem Joystick sollte man dann die Richtung der Rotorenblattdrehung steuer können. Das hat jedoch nicht komplett geklappt, da die Motordrehung in 0 bis 360 Grad angegeben wird, und irgendein Fehler im Code sie immer wieder springen hat lassen. Denke mit etwas mehr Initiative hätte das auch noch komplett geklappt, wollte dann aber lieber die Zeit dahin investieren, noch mehr Hardware kennenzulernen, statt mich an einer aufzuhängen.
![Motor mit Joystick](signal-2022-12-07-174920_008.jpeg)


### Interrupt und Sleep-Modis

Unterbrechungen der Routine sind super wichtig. Also wenn das und das passiert, halte an und mache das. Da aber die Programmierung von Mikrocontrollern auf sich ständig wiederholenden Loops basiert, ist es sehr schwierig eine manuelle Wartefunktion für einen Interrupt einzubauen. Die Schleife hat ja mehrere "Aufträge" zu erledigen, und kann erst ab einer bestimmten Stelle im Code dann abfragen ob die Situation für einen Interrupt eingetroffen ist. Das bedeutet es gäbe keine wirkliche "Echtzeit"-Unterbrechung. Genau aus diesem Grund gibt es bei der Arduinoprogrammierung Interrupts und Sleep-Modis.

"Ein Interrupt ist ein Signal, das die aktuelle Aktivität des Prozessors unterbricht, damit eine andere Funktion ausgeführt werden kann. Die Unterbrechung kann extern, wie zum Beispiel durch das Drücken eines Tasters, oder intern, beispielsweise durch eine Zeituhr oder ein Software-Signal hervorgerufen werden. Einmal aktiviert unterbricht Interrupt die Aktivität des Prozessors und sorgt dafür, dass eine andere Funktion ausgeführt wird. Bekannt ist dies unter dem Namen Unterbrechungsroutine oder ISR, nach der englischen Abkürzung. Sobald die ISR abgeschlossen ist, kehrt das Programm wieder zu seiner vorherigen Aktivität zurück."
(http://diwo.bq.com/de/interrupts-mit-arduino-benutzen/)

Ich habe um Interrupts auszuprobieren einen Taster und eine LED an den Arduino angschlossen. Die LED leuchtet. Wenn der Taster gedrückt wird, wird die Leuchtung der LED unterbrochen:
![interrupt](signal-2022-12-07-181701.gif)

Der Code dazu ist relativ einfach: im Setup wird mit **attachInterrupt(interrupt, ISR, mode)** definiert welche Funktion (ISR) aufgerufen wird wenn die Unterbrechung eintritt. Diese habe ich als **interruptMethod()** deklariert. Mit **interrupt** ist die Nummer des Interrupts gemeint, bei welchem man auf einen Input zur Unterbrechung wartet. Bei mir ist das der buttonState welcher mit 0 deklariert ist. Und **mode** ist die Art, wann die ISR (Interrupt Service Routine) einsetzen soll, also was bei der InterruptNr. passieren muss, dass die ISR aufgerufen wird. Bei mir also: wenn der mode LOW bei interrupt 0 passiert wird interruptMethod() aufgerufen.
```Shell
const int button = 13;
const int led1 = 12;
//const int led2 = 7;

volatile int buttonState = 0;

void setup() {
  // put your setup code here, to run once:
  pinMode(led1, OUTPUT);
  //pinMode(led2, OUTPUT);
  pinMode(button, INPUT);
  attachInterrupt(0, interruptMethod, LOW);
}

void loop() {
  // put your main code here, to run repeatedly:
}

void interruptMethod(){
  buttonState = digitalRead(button);
  digitalWrite(led1, buttonState);
}
```

## Schlusswort

Mein Ziel bezüglich der Mikrocontroller Labs war eigentlich nur, die gängigste Hardware kennenzulernen, benutzen zu können und allgemein einfach was hinzubekommen. Das habe ich meiner Meinung nach geschafft und bin daher sehr zufrieden. :) Natürlich konnte ich nicht alles ausprobieren, und habe auch immer nur maximal 2 Bauteile genutzt. Daher fehlt mir noch das Wissen dazu, wie man bei größeren Projekten mit mehr Hardware verfährt. Ob dann ein Arduino reicht, oder man vllt.sogar mehrere miteinander koppeln kann. Außerdem habe ich nichts wirklich "fest" verbaut. Aber das kommt noch.
Außerdem habe ich keine Zeit mehr gehabt den WLAN-Chip, Sensoren oder den Buzzer (Summer) auszuprobieren. Habe aber mitbekommen das einige andere in der Laborgruppe ihre Erfahrungen diesbezüglich gemacht haben, und die kann ich sicher dazu befragen wenn ich das Wissen dazu brauche.