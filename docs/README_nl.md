iSpindel | iSpindle
===================

**DIY elektronische Bierspindel | elektronische hydrometer | electronic Hydrometer**
***https://universam1.github.io/iSpindel***

***

***Dit document is op dit moment onder bewerking***

## Documentation in other languages

### [English Documentation (work in progress)](docs/README_en.md) :us:
### [Originele document](docs/README.md) [](#lang-de)

***

***Ondersteuning van het project*** 
[![Donate](https://www.paypalobjects.com/de_DE/DE/i/btn/btn_donate_LG.gif)](https://www.paypal.me/universam)

> Update 03.12.16: Firmware 2.1.2 Wlan verbeteringen  
> Update 29.11.16: Kalibreren en Excel Tabel  
> Update 28.11.16: Firmware v.2.0 - Ubidots Auto-configuratie  
> Update 28.11.16: Ubidots instellingen  
> Update 23.11.16: Schema en Firmware


>De ````iSpindel```` bevindt zich op dit momen midden in de ontwikkeling. Op het forum Hobbybrouwen.nl is hier het nodige over te vinden. De ontwikkeling is ontstaan vanuit het Dutise forum Hobbybrauer.de zie hiervoor [Dit topic](http://hobbybrauer.de/forum/viewtopic.php?f=7&t=11235). Hulp is van harte welkom. Veranderingen graag inbrengen met een **Pull request**. Grote dank aan alle die ondersteuning geven op wat voor manier dan ook.


![Spindel im Reinwasser](docs/floating.jpg)
![Dashboard](docs/Dashboard.jpg)


## Inhoudsopgave
- [Licentie](#licentie)
- [Principe](#principe)
  - [Centrale zwaartepunt](#centrale-zwaartepunt)
- [Opbouw](#opbouw)
  - [Onderdelen](#onderdelen)
  - [Schema](#schema)
  - [Componenten schuifhouder](#componenten-schuifhouder)
- [Configuratie](#configuratie)
  - [Ubitdots](#ubitdots)
  - [Toegangsportaal](#toegangsportaal)
- [Weergave](#weergave)
  - [Kalibreren van de  Spindel](#kalibrierung)
  - [Ubidots grafieken](#ubidots-graphen)
  - [CraftBeerPi](#craftbeerpi)
- [Software](#software)


***

## Licentie
>Iedere commerciële nabouw of toepassing is principieel niet toegestaan omdat hiermee geldende patenten worden overtreden.
>
> All rights reserverd, any commercial use is hereby prohibited and will violate applicable patents.

***

## Principe

Voortgedreven door de foumdiscussie [Alternatief voor de hydrometer](http://hobbybrauer.de/forum/viewtopic.php?f=7&t=11157&view=unread#p170499) werd het iedee geboren om de commerciëel verkrijgbare elektronische hydrometer na te bouwen.

Het idee van een scheef in de vloeistof drijvende cylinder is net zo geniaal als eenvoudig.  De cylinder his onafhankelijk van een extern punt (behalve de aarde) en is extreem makkelijk schoon te houden. De hellingshoek verandert met de mate van drijven. Daardoor is er een direkte relatie met het suikergehalte in de vloeistof.
Geen onnodig openen van het gistvat, en de daarmee samenhangende kans op besmetting, om de densiteit te meten. 


![Helling](docs/kraengung.jpg)

Vandaar het idee om een IoT bordje te voorzien van WiFi, gecombineerd met een bewegingssensor en een temperatuursensor, en dat in een drijvende cylinder te plaatsen. De applicatie wordt iedere bijvoorbeeld 5 minuten wakker, verbindt met het netwerk en zendt de hellingshoek, temperatuur en accuspanning naar een Cloudservice.

### *Centrale zwaartepunt*

Eigenlijk draait het om het centrale zwaartepunt. De cylinder zal net zolang reteren tot het centrale zwaartepunt in het centrum van het drijvende centrum is. Dat punt wordt gemeten.

Je kan de cylinder in enige mae trimmen door op de bodem een paar gram toe te voegen zodat de cylinder meer rechtop in de vloeistof drijft (hellingshoek kleiner). Door extra gewicht in het deksel aan te brengen  komt de cylinder schever in de vloeistof te liggen (hellingshoek is groter)

In de software berekent men uit de XYZ  waarden de euler hoeken voorX en Y en van daaruit de berekende absolute hoek. Vervolgens berekenen we uit een formule verkregen met de kalibratiewaarden  het aantal graden Plato of de densiteit (SG).


***

## Opbouw

>***OPMERKING: dit is volgens de stand van zaken op  20.11.2016***

### Onderdelen

- [Wemos D1 mini](https://www.wemos.cc/product/d1-mini.html)
- ```GY-521``` Gyro & bewegingssonsor (MPU-6050 op een passend breakout board)
- [DS18B20 Temperatursensor](https://www.maximintegrated.com/en/products/analog/sensors-and-sensor-interface/DS18B20.html)
- Printplaat 3x4cm
- Weerstanden
  - 4k7 Ohm
  - 220k Ohm
  - 470 Ohm
- Micro schakelaar
- ```18650 Li-Ion accu``` (B.v. ```Panasonic NCR18650B``` **beveiligd** of zonder **PCB**) ***ONGETEST***
- Lipo laadmodule ```TP4056``` ***ONGETEST***
- Kunstof componenten-slede  (Voorstel voor 3D drukken nog in Repo)
 - alternatief (gaatjes) printplaat ***ONGETEST***)
- Kunstof cylinder ```Petling```

> ## Info
> De aanbieder[cachers-world.de](http://cachers-world.de/de/Petling-XL) ondersteunt dit project. Gebruik hiervoor de tegoedbon-code "```HOBBYBRAUER```"  (met hoofdletters) om 20% korting te krijgen.
Deze [Petling-XL](http://cachers-world.de/de/Petling-XL) past met de 3D gedrukte componenten-slede.
>
>Info: *"Deze pettling kost slechts 1,44 EUR , vanaf 2017 wordt het 1,52 EUR . Geadviseerd wordt om goed te kijken omdat verzendkosten vanuit Duitsland hoog kunnen zijn"*

>Info 2: Op dit moment zijn de pettlingen uitverkocht, ze zijn nabesteld.

***
### Schema

***zie [Schema](docs/Schaltplan.md)***

***

### Componenten schuifhouder

![Componenten schuifhouder](docs/Schlitten_cad.jpg)
![Samengesteld](docs/assembled2.jpg)
![Samengesteld 2](docs/assembled.jpg)

[Video 3D printen]<a href="http://www.youtube.com/watch?feature=player_embedded&v=gpVarh8BxhQ" target="_blank"><img src="http://img.youtube.com/vi/gpVarh8BxhQ/0.jpg" 
alt="Druck" width="240" height="180" border="10" /></a>



***

## Configuratie

### Ubitdots

- Om te beginnen moet een gratis account bei [Ubidots.com](https://ubidots.com) geopend worden
- In het menu  ```API Credentials``` kan je de ```Token``` vinden waarmee de iSpindel schrijfrechten voor de data krijgt.  
***Noteer deze!***  
![Token](docs/UbiToken.jpg)  

  ![UbiDS](docs/UbiDS.jpg)

### Toegangsportaal

Door herhaaldelijk drukken op de ```Reset knop```` van de Wemos wordt een Access Point gestart. Men moet met dit Access Point verbinden  om de benodigde instellingen in de iSpindel te kunnen maken. 

> De ```iSpindel``` geeft aan dat hij in de Configuratie modus zit door het permanente iedere seconde knipperen van de led.   
De *Configuratie modus* kan weer verlaten worden door het opslaan van de instellingen, door het drukken op de button ```Start iSpindel```of door 5 minuten te wachten. Daarna bevindt hij zich in de “bedrijfsmodus”, hetgeen betekent dat hij de gemeten data verzendt en vervolgens direkt in een “Deep Sleep” standby modus keert tot de volgende meting. In bedrijfsmodus is de iSpindel niet bereikbaar via de computer of telefoon. 
- Het Ubidots  ```Token``` die je boven genoteerd hebt wordt in dit toegangsportaal bij configuratie ingegeven.  

- Daarnaast geef je hier het ```Interval``` op waarmee data worden verzameld. Dit heeft direkt invloed op de accuduur. Het wordt in de praktijk geadviseerd om ongeveer om de  ```1800``` seconden (= 30 Minuten) te meten.

   ![Setup](docs/setup.jpg)


- Man erreicht es über

   ![AccessPoint](docs/AP.png)![Portal](docs/Portal.png)


- Eine Übersicht der Daten kann man über den ```Info``` Menüpunkt einsehen

  ![Info](docs/info.png)

> Nach dem man obige Daten eingetragen und gespeichert hat, wird die Spindel sich mit dem Wlan und Ubidots verbinden und die Daten übertragen.  
Auf der Ubidots Weboberfläche wird man nun unter ```Sources``` sehen dass die Daten aktualisiert werden.  
Nun kann man im ```Dashboard``` sich seine Graphen nach Belieben zusammenstellen.

***
## Anzeige

### Kalibrierung

> Zur Umrechnung von Winkel ° in °Plato, SG, %mas o.Ä. ist es initial nötig eine Referenzkurve zu kalibrieren. Die gewonnenen Referenzen können dann vereinfacht über eine Excel Tabelle in eine Funktion überführt werden, die zur Darstellung hinterlegt wird. Da jede selbstgebaute Spindel andere Messwerte ergeben wird, muss man diesen Prozess einmalig durchführen.

[siehe Kalibrierung durchführen](docs/Kalibrierung.md)

### Ubidots Graphen

- [Plato Formel](docs/Kalibrierung.md#formel)

### CraftBeerPi

[Work in Progress](https://github.com/universam1/iSpindel/issues/3)
***

## Software 

### Firmware flashen

[Firmware flashen](docs/Firmware.md)

### Benutzte Bibliotheken

- https://github.com/tzapu/WiFiManager zum Herstellen der Verbindung (verändert)
- https://github.com/bblanchon/ArduinoJson

***Gefällt es dir, na dann spende mir halt ein Bier***  :beers:

[![Donate](https://www.paypalobjects.com/de_DE/DE/i/btn/btn_donate_LG.gif)](https://www.paypal.me/universam)
