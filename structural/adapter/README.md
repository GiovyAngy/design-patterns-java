# 🔌 Adapter (Strukturmuster)

## Kategorie
Strukturmuster

## Idee
Lässt inkompatible Schnittstellen zusammenarbeiten, indem eine bestehende Klasse in ein neues Interface „eingepasst“ wird (Wrapped / überbrückt).  
Zielt darauf ab **Integration** = nicht umschreiben, sondern adaptieren.

## Einsatz / Wann benutzen?
- Legacy / Fremd-Code einbinden der nicht unser Interface spricht
- APIs harmonisieren / vereinheitlichen
- Consumer soll auf *unser* Interface zugreifen können ohne Änderung im Legacy Code

## Java Beispiel

```java
// Ziel-Interface (neuer Standard)
sealed interface Shape permits Circle { 
    double area(); 
}

// "Legacy" Klasse (kann nicht angepasst werden)
final class LegacyCircleLib {
    double computeArea(double radius) { return Math.PI * radius * radius; }
}

// Adapter
final class Circle implements Shape {
    private final LegacyCircleLib legacy = new LegacyCircleLib();
    private final double radius;

    Circle(double radius) { this.radius = radius; }

    public double area() {
        return legacy.computeArea(radius);
    }
}

public class App {
    public static void main(String[] args) {
        Shape s = new Circle(3);
        System.out.println(s.area()); // funktioniert wie "unser" Shape Interface
    }
}
