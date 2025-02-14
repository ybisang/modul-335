# Angular: Data Binding

Das Data Binding mit Angular ist eines der Hauptvorteile des Frameworks:

![](../.gitbook/assets/bildschirmfoto-2018-12-27-um-13.47.01.png)

## One-Way Data Binding

Bei einer einfachen Applikation hat man Daten im Model (blau) und meist ein Template / HTML (rot) bei welchem die Daten einmalig zusammengeführt werden und dem User in einer View (grün) dargestellt werden. Die Verschmelzung von Daten und Code passiert meist nur einmalig. Stellen wir uns nun ein Formular auf einer Website vor und der Benutzer gibt dort ein Wert in ein Textfeld ein, so ist es mit dieser Methode nicht so einfach Daten im gleiche HTML-DOM zu ändern. Meist wird hier dann mit Javascript ein sehr unschöner Code geschrieben.

## Two-Way Data Binding

Genau hier hat Angular seinen Vorteil. Das Data Binding in Angular synchronisiert das Model mit der View und umgekehrt. So kann ein Wert in der View geändert werden und gleichzeitig wird der Wert im Model auch angepasst. Umgekehrt natürlich auch, siehe Grafik rechts. Diese ständige Zweiweg-Synchronisation nennt man Two-Way Data Binding.

```markup
<!-- TwoWayBindingExample.page.html -->
<ion-content class="ion-padding">
    <h1>Hello {{ username }}</h1>
    <input type="text" value="" (input)="changeUsername($event)">
</ion-content>
```

```javascript
// TwoWayBindingExample.page.ts
...
export class TwoWayBindingExamplePage implements OnInit {

  username: string = "max.muster";
  ngOnInit() {
  }
  changeUsername(ev) {
    this.username = ev.target.value;
  }

}
...
```

### Hier noch ein kleiner Vergleich mit jQuery:

```markup
<html>
  <h1 id="ausgabe"></h1> 
  <input id="username" type="text">
</html>
```

```javascript
$(document).ready(function() {
  $('#username').keyup(function(){
    $('#ausgabe').html("Hallo " + $('#eingabe').val());
  });
});
```

## Data binding mit ngModel

`ngModel` erlaubt es, eine Variable an ein Input-Feld in der App zu binden. Dies funktioniert nicht nur mit Textfelder (Inputs) sondern auch mit Radios, Selects, usw.

Füge folgenden Zeile deiner Component hinzu:

```javascript
userData: any = {'name': 'Ralph', 'city': 'Luzern, Switzerland'};
```

Nun fügen wir unserem HTML einen `input`-Feld hinzu und verbinden es mit `ngModel` mit unserem Code. Dabei wollen wir auf den Namen unter `userData.name` zugreifen.

```markup
<ion-content class="ion-padding">
    <input id="name" type="text" [(ngModel)]="userData.name">
    <h1 id="ausgabe">Hey, my name is {{userData.name}} and I'm from {{userData.city}}</h1>
</ion-content>
```

Dieses TwoWay-Binding machen wir uns in der Ausgabe gleich wieder zu Nutze. Und geben dabei einen einfachen Text aus. Der Ort lassen wir unverändert.



![2-Way Data Binding](<../.gitbook/assets/Untitled-2021-02-25-1512 (1).png>)



## Übungen

![](../.gitbook/assets/ralph\_uebung.png)

1. Nimm dein am Tag 1 erstelltes  Projekt "GX\_NachnameVorname\_Übung"
2. Erstelle eine neue Seite "Data Binding" und füge diese wie gewohnt in dein Sidemenu ein.
3. Erstelle in deinem HTML folgende drei Felder. Verwende dazu das [Ionic Grid](https://ionicframework.com/docs/api/grid). Bitte wähle auch logische Namen und wähle [passende UI-Elemente](https://ionicframework.com/docs/components/#inputs):
   1. Input: Name - Text
   2. Input: Vorname - Text
   3. Input: Alter - Number
4. Verknüpfe nun die jeweiligen Input-Felder mit deiner Component mit Hilfe der oben beschriebene Methode `ngModel`.
5.  Füge nun unter deine Inputs ein Paragraph hinzu und gib einen Satz in folgendem Stil (je nach Eingaben) aus:

    `Mein Name ist Max Muster und ich bin 23 Jahre alt!`
6. Teste deine App\
   1\. Funktioniert Sie wie erwartet?\
   2\. Hast du die richtigen Input-Typen gewählt? 3. Kannst du bei deinem Alter auch wirklich nur eine Zahl eingeben?
