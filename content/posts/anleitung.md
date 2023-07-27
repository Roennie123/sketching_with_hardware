---
title: "Walking Tortoise Nachbau Anleitung"
date: 2023-07-27T09:25:38+02:00
type: "post"
tags: ["walking tortoise", "3D-Druck", "Blender", "Microcontroller"]
draft: true
---

# Vorwort

In diesem Tutorial möchte ich euch Schritt für Schritt zeigen wie man sich ein sehr pflegeleichtes Haustier baut. Und zwar eine Schildkröte. :turtle:
Die Schildkröte ist 3D-gedruckt und kann über eine Smartphoneapp und Bluetoothconnection gesteuert werden.
Ich habe das Projekt im Rahmen des Kurses *Sketching with Hardware* der Universität Ulm gebaut.
Gerne stelle ich dir alle nötigen Dateien und Arbeitsanweisungen zur Verfügung und ermutige dich es doch auch selbst zu auszuprobieren. :wink:

![gif walking tortoise](ezgif.com-video-to-gif(2).gif)

### Arbeitszeit

* Druck: ca. vier Tage
* Montage und Löten: nicht länger als ein Tag


### Kosten

Je nachdem was dir bereits zur Verfügung steht und wo du benötigte Teile kaufst, können die Kosten sehr unterschiedlich ausfallen. Das teuerste sind Filament und Motoren. Schau dir doch einfach die Liste mit den Bauteilen an.


## Bauteile

* Microcontroller
    * ich habe einen Atmega Nano 328 benutzt
    * z.B. diesen hier *https://www.az-delivery.de/products/nano-v3-mit-ch340-arduino-kompatibel*
    * wenn du einen anderen benutzen möchtest musst du darauf achten dass genug Pins für die Motoren vorhanden sind und die Größe passt
* Bluetoothmodul
    * ich habe ein HC-05
    * *https://maker.pro/custom/tutorial/hc-05-bluetooth-transceiver-module-datasheet-highlights*
    * wenn du ein anderes nehmen möchtest informiere dich am besten über die Kompabilität mit deinem Microcontroller
* 8 Servomotoren
    * ich habe MG90S genutzt
    * *https://components101.com/motors/mg90s-metal-gear-servo-motor*
    * MG steht für Metal Gear :gear: und das war ausschlaggebend dafür dass die Schildkröte stabil ist, daher würde ich keine Servos mit Kunststoffgetrieben empfehlen
    * wird deine finale Schildkröte allerdings schwerer als Gramm, solltest du dich nach stärkeren Motoren umsehen
    * achte darauf dass pro Motor mindestens eine kleine und zwei größere Schräubchen, inklusive der Rotorblätter dabei sind
* Powerbank
    * ich habe eine mit 10.000 mA/h Leistung und einem Gewicht von 172 Gramm benutzt
    * diese hier von Bogseth *https://www.amazon.de/powerbank-led-anzeige-Ausgang-Externe-handyakkus/dp/B09JFX8VG1/ref=sr_1_19?keywords=runde%2Bpowerbank&qid=1686848431&sr=8-19&th=1*
    * wenn du eine andere nutzen möchtest achte darauf dass sie nicht zu schwer ist und dass sie von der Größe her passt, bzw. musst du dann das Inlay abändern
    * außerdem ist bei den von mir genutzten MG90S Servomotoren eine Leistung von mindestens 5.000 mA/h nötig
* PLA Filament
    * ich habe dieses Filament der Farbe Kaffee genutzt *https://filamentworld.de/shop/filament-3d-drucker/francofil-pla-kaffee-filament-1-75-mm/*
    * im Nachhinein hätte ich es sehr cool gefunden das Kaffee-Filament für Kopf, Schwanz, Beine und ein weiteres Filament der Farbe Bier für den Panzer zu nehmen (*https://filamentworld.de/shop/filament-3d-drucker/francofil-eco-pla-filament-bier-2-85-mm/*)
    * mir haben 750 Gramm gereicht (inklusive einem Fehldruck des Unterteils :D )
    * achte darauf dass der Durchmesser auch zu deinem Drucker passt
* Kathode
* Steckplatine
* USB Kabel
    * je nachdem welchen Output deine Powerbank hat
    * hab meins zerschnitten und daher ein altes etwas kaputtes genommen
* Kabel, Kabelschuhe und Steckhülsen
    * ganz grob geschätzt habe ich ca. 4 * 14 cm Kabel benötigt, da die Motoren ja bereits Kabel haben welche man nur noch kürzen muss
    * 28 Kabelschuhe und Hülsen
    * am besten besorgst du dir einen Kasten in dem alles schon drin ist
* Schrumpfschlauch
    * muss nicht sein, ist aber die smartere Arbeitsweise
* Lötzinn
* Zwei-Komponentenkleber
* 3 * 2 kleine Magnete
    * die Magnetaussparungen in meinem Modell passen perfekt zu bestimmten Magneten (einfach nachfragen bei Interesse)

### Was du zusätzlich noch brauchst

* 3D-Drucker
    * habe für Kopf, Beine, Schwanz und Panterteile einen Ultimaker2+ genutzt
    * für Inlay und Servohalterungen einen Snapmaker
* Kabelzange
* Lötkolben
* kleiner Schraubendreher
* Breadboard und Jumperkabel zum Testen
* Smartphone
    * mit meinem Arduino hat alles super funktioniert, habe jedoch gehört, dass das Bluetoothconnections über iOS Systeme Schwierigkeiten machen können
* einen sauberen Platz zum Arbeiten :wink:

![bauteile](nano.png)
![bauteile](servo.png)

## Dateien

Alle STL-Dateien, sowie die tortoiseWalk-APK findest du in meinem GitHub Repository: *https://github.com/Roennie123/walking_tortoise_data.git*.


# Schritt für Schritt Anleitung

## Schritt 1: Materialien besorgen

Oben in der Bauteileliste siehst du was du alles benötigst. Lese dir im ersten Schritt am besten auch einmal die komplette Nachbauanleitung durch um keine bösen Überaschungen aufgrund von übereiligem Handeln erleben zu müssen.


## Schritt 2: STL-Dateien für den Druck runterladen

Ich habe mein 3D-Modell mit Blender und Fusion erstellt. Du kannst es benutzen, aber natürlich auch sehr gerne ein eigenes machen um diese Erfahrung ebenfalls mitzunehmen. :wink:

Alle STL-Dateien findest du in meinem GitHub Repository: *https://github.com/Roennie123/walking_tortoise_data.git*

### STL-Dateien für den Druck und Supporteinstellungen:
* Vier Servohalter für die Stapelmontage:       
    * *servohalterung_MG90s.stl*
    * ohne Support
* Inlay:                                        
    * *inlay.stl*
    * ohne Support
* Panzeroberteil:                               
    * *top.stl*
    * tree
* Panzerunterteil mit Montageaussparungen:      
    * *bottom.stl*
    * standard Support
* Vier Beine (2 * rechts, 2 * links):           
    * *food_right.stl*, *food_left.stl*
    * tree
* Kopf:                                         
    * *head.stl*
    * tree
* Ausgleichs-Montagestütze für den Kopf:        
    * *head_stuetze.stl*
    * ohne Support
* Schwanz:                                      
    * *tail.stl*
    * tree

## Schritt 3: Drucken

Je nachdem welchen Drucker du verwendest, musst du im passenden Programm dann auch die STL-Datei slicen (um G-Code zu bekommen). Ich habe Cura für den Ultimaker2+ und Luban für den Snapmaker genommen.
Das Drucken braucht seine Weile. Daher kannst du dir ja alle Dateien schonmal slicen und dann je nachdem wie lange ein Teil benötigt eine Art Zeitplan machen. Um alles möglichst schnell über die Bühne zu bekommen.

In Schritt 2 sind bereit die Supporteinstellungen für die einzelnen Teile mit vermerkt. Drehe die einzelnen Teile immer so dass möglichst wenig der Details kaputt gehen oder im Support versinken. Ganz klappt das nicht, aber durch Tricksen bekommt man trotzdem ein gutes Ergebnis.

Natürlich den Support nach dem Druckvorgang vorsichtig mit einer Zange entfernen.

![drucken](druck.png)

## Schritt 4: Programmierung

Die Programmierung ist super simpel: kopiere einfach meinen Code in dein Arduinotool (*https://www.arduino.cc/en/software*). Wenn du Anpassungen machen möchtest, kannst du dies gerne machen.

Verbinde jetzt deinen Microcontroller mit dem Rechner und lade das Programm drauf. 

:warning: Sehr wichtig ist es das Bluetoothmodul vor dem Hochladen kurz abzuziehen. Ansonsten funktionierts nicht.

Solltest du Probleme beim Hochladen haben kann es am Treiber liegen (dazu findest du eigentlich immer Tipps im Datenblatt) oder daran dass du Updates machen musst. Je nachdem welchen Microcontroller du verwendest benötigst du auch noch die passende Bibliothek.

### Code
```markdown
#include <Servo.h> //servobib

//2 servos per food -> lower: hm, upper: vm
Servo hm1;                Servo vm1; //back rightside 
Servo hm2;                Servo vm2; //back leftside 
Servo hm3;                Servo vm3; //front leftside
Servo hm4;                Servo vm4; //front rightside

int servoPos;
int servoPosOpp;

bool started1;            bool started2;
bool started3;            bool started4;

bool walking;


void setup() {
  hm1.attach(12);         vm1.attach(11);
  hm2.attach(9);          vm2.attach(8);
  hm3.attach(6);          vm3.attach(5);
  hm4.attach(3);          vm4.attach(2);

  //starts everytime in neutral Position
  startPos();
  
  Serial.begin(9600);

}

int a = 0;

void loop() {
  if (Serial.available() > 0) {
    
      int i = Serial.read();
      if(i == '4'){
        sit();
      } else if(i == '5'){
        sitDown();
      } else if(i == '6'){
        layDown();
      } else if(i == '7'){
        sleep();
      } else if( i == '8'){
        startPos();
      } 

      while(i == '1'){
        movingRoutine();
        Serial.print(i);
        if(Serial.read() == '0'){
          break;
        }
      }

      while(i == '2'){
        movingRoutineFast();
        Serial.print(i);
        if(Serial.read() == '0'){
          break;
        }
      }

      while(i == '3'){
        movingRoutineSlow();
        Serial.print(i);
        if(Serial.read() == '0'){
          break;
        }
      }

      while(i == '9'){
        dance();
        Serial.print(i);
        if(Serial.read() == '0'){
          break;
        }
      }
  } 
}

//  one moving routine is:
//      3 back & 4 ahead      #1  -> threeFour()
//      1 back & 2 ahead      #2  -> oneTwo()
//      4 back & 3 ahead      #3  -> fourThree()
//      2 back & 1 ahead      #4  -> twoOne()

void startPos(){
  vm1.write(80);  vm2.write(90);  vm3.write(80);  vm4.write(90);
  hm1.write(80);  hm2.write(90);  hm3.write(80);  hm4.write(90);
  started1 = false;               started2 = false;
  started3 = false;               started4 = false;
}

void dance(){
  shake(7);
  shake(7);
  for(servoPos = 90; servoPos < 130; servoPos++){
    vm4.write(servoPos);
    delay(10);
  }
    for(servoPos = 130; servoPos > 90; servoPos--){
    vm4.write(servoPos);
    delay(10);
  }
  shake(7);
  shake(7);
    for(servoPos = 80; servoPos > 40; servoPos--){
    vm3.write(servoPos);
    delay(10);
  }
    for(servoPos = 40; servoPos < 80; servoPos++){
    vm3.write(servoPos);
    delay(10);
  }
}

void shake(int danceSpeed){
  if(started4 && started2 && started3 && started1){
    for(servoPos = 50; servoPos < 110; servoPos++){
      hm4.write(servoPos);
      hm2.write(servoPos);
      hm3.write(servoPos);
      hm1.write(servoPos);
      delay(danceSpeed);
    }
    delay(danceSpeed);
    for(servoPos = 110; servoPos > 50; servoPos--){
      hm4.write(servoPos);
      hm2.write(servoPos);
      hm3.write(servoPos);
      hm1.write(servoPos);
      delay(danceSpeed);
    }
    delay(danceSpeed);
  } else{
    for(servoPos = 90; servoPos < 110; servoPos++){
        hm4.write(servoPos);
        hm2.write(servoPos);
        hm3.write(servoPos);
        hm1.write(servoPos);
        delay(danceSpeed);
    }
    delay(danceSpeed);
    for(servoPos = 110; servoPos > 50; servoPos--){
      hm4.write(servoPos);
      hm2.write(servoPos);
      hm3.write(servoPos);
      hm1.write(servoPos);
      delay(danceSpeed);
    }
    delay(danceSpeed);
      started4 == true;
      started2 == true;
      started3 == true;
      started1 == true;
  }
}


void sit(){
  startPos();
  delay(30);
  servoPosOpp = 90;
  for(servoPos = 80; servoPos < 120; servoPos++){
    vm1.write(servoPos);
    vm2.write(servoPosOpp);
    servoPosOpp--;
    delay(5);
  }
}

void sitDown(){
  startPos();
  delay(30);
  servoPosOpp = 90;
  for(servoPos = 80; servoPos < 145; servoPos++){
    vm1.write(servoPos);
    vm2.write(servoPosOpp);
    servoPosOpp--;
    delay(5);
  }
}

void layDown(){
  sitDown();
  servoPosOpp = 90;
  for(servoPos = 80; servoPos < 145; servoPos++){
    vm3.write(servoPos);
    vm4.write(servoPosOpp);
    servoPosOpp--;
    delay(5);
  }
}

void sleep(){
  sitDown();
  servoPosOpp = 90;
  for(servoPos = 80; servoPos > 25; servoPos--){
    vm3.write(servoPos);
    vm4.write(servoPosOpp);
    servoPosOpp++;
    delay(5);
  }
}

void movingRoutine(){
  threeFour(5, 7);
  delay(7);
  oneTwo(5, 7);
  delay(7);
  fourThree(5, 7);
  delay(7);
  twoOne(5, 7);
  delay(7);
}

void movingRoutineFast(){
  threeFour(3, 5);
  delay(5);
  oneTwo(3, 5);
  delay(5);
  fourThree(3, 5);
  delay(5);
  twoOne(3, 5);
  delay(5);
}

void movingRoutineSlow(){
  threeFour(7, 9);
  delay(9);
  oneTwo(7, 9);
  delay(9);
  fourThree(7, 9);
  delay(9);
  twoOne(7, 9);
  delay(9);
}

//#1
void threeFour(int speedVM, int speedHM){
  if(started3 && started4){
    //4 up
    for(servoPos = 90; servoPos < 130; servoPos++){
      vm4.write(servoPos);
      delay(speedVM);
    }
    //vm3 back to 80
    for(servoPos = 70; servoPos < 80; servoPos++){
      vm3.write(servoPos);
      delay(speedVM);
    }
    //3 back & 4 ahead
    for(servoPos = 50; servoPos < 120; servoPos++){
      hm4.write(servoPos);
      hm3.write(servoPos);
      delay(speedHM);
    }
    //4 down
    for(servoPos = 130; servoPos > 100; servoPos--){
      vm4.write(servoPos);
      delay(speedVM);
    }
    
  }else{
    //only 4 ahead
    for(servoPos = 90; servoPos < 130; servoPos++){
      vm4.write(servoPos);
      delay(speedVM);
    }
    for(servoPos = 90; servoPos < 120; servoPos++){
      hm4.write(servoPos);
      delay(speedHM);
    }
    for(servoPos = 130; servoPos > 100; servoPos--){
      vm4.write(servoPos);
      delay(speedVM);
    }
    started4 = true;
  }

}

//#2
void oneTwo(int speedVM, int speedHM){

  if(started1 && started2){
    //2 up
    for(servoPos = 90; servoPos > 50; servoPos--){
      vm2.write(servoPos);
      delay(speedVM);
    }
    //vm1 back to 80
    for(servoPos = 90; servoPos > 80; servoPos--){
      vm1.write(servoPos);
      delay(speedVM);
    }
    //1 back & 2 ahead
    for(servoPos = 110; servoPos > 60; servoPos--){
      hm2.write(servoPos);
      hm1.write(servoPos);
      delay(speedHM);
    }
    //2 down
    for(servoPos = 50; servoPos < 80; servoPos++){
      vm2.write(servoPos);
      delay(speedVM);
    }
  }else{
    //only 2 ahead
    for(servoPos = 90; servoPos > 50; servoPos--){
      vm2.write(servoPos);
      delay(speedVM);
    }
    for(servoPos = 90; servoPos > 60; servoPos--){
      hm2.write(servoPos);
      delay(speedHM);
    }
    for(servoPos = 50; servoPos < 80; servoPos++){
      vm2.write(servoPos);
      delay(speedVM);
    }
    started2 = true;
  }
  
}

//#3
void fourThree(int speedVM, int speedHM){

  if(started3 && started4){
    //3 upside
    for(servoPos = 80; servoPos > 40; servoPos--){
      vm3.write(servoPos);
      delay(speedVM);
    }
    //vm4 back to 90
    for(servoPos = 100; servoPos > 90; servoPos--){
      vm4.write(servoPos);
      delay(speedVM);
    }
    //4 back & 3 ahead
    for(servoPos = 120; servoPos > 50; servoPos--){
      hm3.write(servoPos);
      hm4.write(servoPos);
      delay(speedHM);
    }
    //3 down
    for(servoPos = 40; servoPos < 70; servoPos++){
      vm3.write(servoPos);
      delay(speedVM);
    }
  }else{
    //3 upside
    for(servoPos = 80; servoPos > 40; servoPos--){
      vm3.write(servoPos);
      delay(speedVM);
    }
    //vm4 back to 90
    for(servoPos = 100; servoPos > 90; servoPos--){
      vm4.write(servoPos);
      delay(speedVM);
    }
    //4 back to mid
    for(servoPos = 120; servoPos > 80; servoPos--){
      hm4.write(servoPos);
      delay(speedHM);
    }
    //4 back & 3 first time ahead
    for(servoPos = 80; servoPos > 50; servoPos--){
      hm3.write(servoPos);
      hm4.write(servoPos);
      delay(speedHM);
    }
    //3 down
    for(servoPos = 40; servoPos < 70; servoPos++){
      vm3.write(servoPos);
      delay(speedVM);
    }
   started3 = true;
  }

}

//#4
void twoOne(int speedVM, int speedHM){

  if(started1 && started2){
    //1 upside
    for(servoPos = 80; servoPos < 130; servoPos++){
      vm1.write(servoPos);
      delay(speedVM);
    }
    //vm2 back to 90
    for(servoPos = 80; servoPos < 90; servoPos++){
      vm2.write(servoPos);
      delay(speedVM);
    }
    //2 back & 1 ahead
    for(servoPos = 50; servoPos < 110; servoPos++){
      hm1.write(servoPos);
      hm2.write(servoPos);
      delay(speedHM);
    }
    //1 down
    for(servoPos = 130; servoPos > 80; servoPos--){
      vm1.write(servoPos);
      delay(speedVM);
    }
  }else{
     //1 upside
    for(servoPos = 80; servoPos < 120; servoPos++){
      vm1.write(servoPos);
      delay(speedVM);
    }
    //vm2 back to 90
    for(servoPos = 80; servoPos < 90; servoPos++){
      vm2.write(servoPos);
      delay(speedVM);
    }
    //2 back to mid
    for(servoPos = 60; servoPos < 80; servoPos++){
      hm2.write(servoPos);
      delay(speedHM);
    }
    //2 back & 1 first time ahead
    for(servoPos = 80; servoPos < 110; servoPos++){
      hm1.write(servoPos);
      hm2.write(servoPos);
      delay(speedHM);
    }
    //1 down
    for(servoPos = 120; servoPos > 90; servoPos--){
      vm1.write(servoPos);
      delay(speedVM);
    }
    started1 = true;
  }
}
```


## Schritt 5: Smartphone-App installieren

Ich habe meine App mit dem MIT-Appinventor erstellt. Das ist ein Online-Tool mit welchem sich sehr leicht Interfaces programmieren lassen. Außerdem gestaltet sich dort auch die Einrichtung der Bluetoothconnection sehr einfach.

![Smartphone-App](app.png)

Du kannst entweder meine App (scanne dazu den QR-Code mit deinem Smartphone und folge den Anweisungen zur Installation, oder lade sie dir aus dem GitHub-Repo runter) nutzen, oder dir selbst eine bauen. :hammer:

* Hier gehts zur Seite:
    * *http://appinventor.mit.edu/*
* Und hier ist ein Tutorial welches mir sehr geholfen hatte mich zurecht zu finden:
    * https://www.youtube.com/watch?v=aQcJ4uHdQEA


## Schritt 6: Löten der Platine

:warning: Achtung: Bevor du anfängst irgendetwas festzulöten solltest du alles auf einem Breadboard stecken und testen. Das ist unabdinglich, denn selbst wenn du alles richtig gemacht hast, könnte es sein dass irgendein Teil kaputt ist (will man nicht hoffen aber kommt manchmal vor). Teile wieder zu entfernen kann manchmal sehr mühsam bis fast unmöglich sein.

Unten habe ich dir ein Lötdiagramm angehängt, welches zeigt nach welchen Pins ich verbunden habe (kannst du auch anders machen, musst das dann aber im Code anpassen). Es ist super wichtig zu beachten, dass das Bluetoothmodul jeweils eine Verbindung zwischen TXD - RX0 und RXD - TX1 hat (das ist kein Fehler :wink: )

Die Motoren haben ein orangenes, ein braunes und ein rotes Kabel. Das rote kommt zu +, das braune zu - und das orangene an den Pin.
Ich habe die Kabel der Motoren gekürzt, mit Kabelschuhen und Hülsen versehen und mit Schrumpfschlauch organisiert. Sieht so sehr viel ordentlicher aus als lauter wirre Kabel. Mir war es außerdem wichtig dass die Motoren austauschbar bleiben. Habe daher nur Pins an die Platine gelötet, an welche sich die Kabel dann ranstecken lassen.

Außerdem habe ich einen Microcontroller-externen Stromkreis gelötet. An diesen sind dann Microcontroller, Bluetoothmodul und Motoren jeweils mit + und - angeschlossen. Ebenfalls die Kathode. Achte hierbei auf + und - da sie sonst durchbrennen kann.

Zu guter letzt habe ich das USB-Kabel aufgeschnitten und auch am Stromkreis befestigt. Du brauchst nur + und -. Die Leitungen zur Datenübertragung können gekappt werde. Habe auch hier alles mit Schrumpfschlauch schön gemacht.

![Kabel](kabel.gif)

### Lötdiagramm
![loeten](loetplan2.png)
![loeten](loetplan.png)

## Schritt 7: Montage

Wenn alles ordentlich verkabelt ist und funktioniert kannst du schließlich auch alle Teile fest verbauen.

Setze alle Motoren auf 80 Grad, oder kalibriere sie mit der Funktion **startPos()** aus dem Code. Das ist super wichtig da du sonst womöglich nochmal die Gradzahlen umschreiben musst. Und die Arbeit kann man sich ja sparen.

Schraube die jeweils unteren Motoren (HM 1/2/3/4) in die Motoraussparungen des Unterteils. 
Die Nummerierung ist wie folgt (von oben auf den Körper blickend):
* 1: rechts hinten
* 2: links hinten
* 3: links vorne
* 4: rechts vorne

In das Getriebe der unteren Motoren schraubst du dann die für jeweilige Seite (links/rechts) passenden Servohalter. In die Halterungen kommen dann die dazugehörigen oberen Motoren (VM 1/2/3/4), und an diese die in die Aussparung der Füße passenden Rotorblätter. Drehe die lange Seite der Rotorblätter nach unten.

Jetzt kannst du die Rotorblätter mit Zwei-Komponentenkleber in die Montageaussparungen der Füße kleben. Achte darauf die passenden Füße zu wählen (links/rechts).

Klebe ebenfalls den Schwanz, die Kopf-Montagestütze, den Kopf und die Magnete an die passenden Stellen.

Jetzt setzt du noch das Inlay ein und die Elektronik.

Ich habe meiner Schildkröte noch mit schwarzem Nagellack die Nägel und die Augen lackiert, so dass sie etwas lebendiger aussah.

![lackieren](turtle.png)
![lackieren](turtle2.png)

## Schritt 8: Laufen lassen

Jetzt kannst du das USB-Kabel in der Powerbank einstecken und die App auf dem Smartphone öffnen.
Klicke auf Connect turtle und wähle HC-05 (oder je nachdem welches Bluetoothmodul du benutzt) aus.

Wenn alles geklappt hat solltest du deine Schildkröte nun laufen lassen können. Solange du auf einen der Bewegungsbuttons drückst läuft sie. Wenn du runter gehst macht sie noch den Schritt zu Ende und bleibt stehen.
Außerdem kannst du sie hinsetzen lassen.

Hoffe du hattest Spaß beim Lesen oder Nachbauen meines Projekts! :grin:

![walk](ezgif.com-rotate.gif)
