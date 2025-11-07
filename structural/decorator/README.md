# 🎀 Decorator (Strukturmuster)

## Kategorie
Strukturmuster

## Idee
Fügt Objekten dynamisch zusätzliche Verantwortlichkeiten hinzu, **ohne** neue Subklassen erstellen zu müssen.  
Das Objekt wird „eingewickelt“ — Verhalten wird erweitert / kombiniert, ohne den Originaltyp zu verändern.

## Einsatz / Wann benutzen?
- zusätzliche optionale Features flexibel kombinierbar
- keine Klassenexplosion durch Subklassen-Varianten
- Verhalten zur Laufzeit hinzufügen / entfernen

## Java Beispiel

```java
// Grundkomponente
sealed interface Notifier permits BaseNotifier, SmsDecorator, SlackDecorator {
    void send(String msg);
}

// Basis-Objekt
final class BaseNotifier implements Notifier {
    public void send(String msg) {
        System.out.println("send email: " + msg);
    }
}

// Decorator Basis
abstract sealed class NotifierDecorator implements Notifier permits SmsDecorator, SlackDecorator {
    protected final Notifier wrappee;

    NotifierDecorator(Notifier wrappee) { this.wrappee = wrappee; }

    public void send(String msg) {
        wrappee.send(msg); // weiterreichen
    }
}

// konkrete Erweiterungen
final class SmsDecorator extends NotifierDecorator {
    SmsDecorator(Notifier wrappee) { super(wrappee); }

    public void send(String msg) {
        super.send(msg);
        System.out.println("send SMS: " + msg);
    }
}

final class SlackDecorator extends NotifierDecorator {
    SlackDecorator(Notifier wrappee) { super(wrappee); }

    public void send(String msg) {
        super.send(msg);
        System.out.println("send Slack: " + msg);
    }
}

// Client
public class App {
    public static void main(String[] args) {

        Notifier notifier =
            new SlackDecorator(
                new SmsDecorator(
                    new BaseNotifier()
                )
            );

        notifier.send("Alert!");  
        // email + sms + slack
    }
}
