# 🏭 Factory (Erzeugungsmuster)

## Kategorie
Erzeugungsmuster

## Idee
Kapselt die Objekterzeugung basierend auf Eingaben/Kontext und liefert den passenden Subtyp, ohne konkrete Klassen / Konstruktoren offenzulegen.

## Einsatz / Wann benutzen?
- mehrere Implementierungen eines Interfaces vorhanden
- eine zentrale Stelle entscheidet, welche konkrete Klasse erstellt wird
- Aufrufer soll nicht wissen müssen, *wie* Objekte erzeugt werden

## Java Beispiel

```java
sealed interface Payment permits PaypalPayment, CreditCardPayment {}

final class PaypalPayment implements Payment {}
final class CreditCardPayment implements Payment {}

final class PaymentFactory {

    public static Payment create(String method) {
        return switch (method) {
            case "paypal" -> new PaypalPayment();
            case "card" -> new CreditCardPayment();
            default -> throw new IllegalArgumentException("Unbekannte Zahlungsmethode: " + method);
        };
    }
}

public class App {
    public static void main(String[] args) {
        Payment p = PaymentFactory.create("paypal");
        System.out.println(p.getClass().getSimpleName()); // PaypalPayment
    }
}
