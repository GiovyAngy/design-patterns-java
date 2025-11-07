# 🧪 Abstract Factory (Erzeugungsmuster)

## Kategorie
Erzeugungsmuster

## Idee
Erzeugt **Familien** von zusammengehörigen Objekten, ohne konkrete Klassen zu nennen.  
Der Aufrufer arbeitet ausschließlich gegen abstrakte Interfaces — ganze „Produktwelten“ können ausgetauscht werden (z. B. OS-spezifische GUI Widgets).

## Einsatz / Wann benutzen?
- komplette Themenwelten / Produktfamilien austauschbar machen
- Konsistenz gewährleisten zwischen Produkten (passen zusammen)
- Aufrufer soll keine `new` konkreter Klassen kennen müssen

## Java Beispiel

```java
// Produktfamilie 1: API
sealed interface Button permits WinButton, MacButton {}
sealed interface Textbox permits WinTextbox, MacTextbox {}

// konkrete Produkte
final class WinButton implements Button {}
final class MacButton implements Button {}
final class WinTextbox implements Textbox {}
final class MacTextbox implements Textbox {}

// Abstract Factory
interface UIFactory {
    Button createButton();
    Textbox createTextbox();
}

// konkrete Fabriken (Familien)
final class WinFactory implements UIFactory {
    public Button createButton() { return new WinButton(); }
    public Textbox createTextbox() { return new WinTextbox(); }
}

final class MacFactory implements UIFactory {
    public Button createButton() { return new MacButton(); }
    public Textbox createTextbox() { return new MacTextbox(); }
}

// Client
public class App {
    public static void main(String[] args) {

        UIFactory factory = new MacFactory(); // ganze Familie austauschbar

        Button b = factory.createButton();
        Textbox t = factory.createTextbox();

        System.out.println(b.getClass().getSimpleName()); // MacButton
        System.out.println(t.getClass().getSimpleName()); // MacTextbox
    }
}
