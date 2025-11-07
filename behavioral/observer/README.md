# 👀 Observer (Verhaltensmuster)

## Kategorie
Verhaltensmuster

## Idee
Stellt eine **1→n** Abhängigkeit her: wenn sich der Zustand des Subjekts ändert, werden alle registrierten Beobachter automatisch benachrichtigt.

## Einsatz / Wann benutzen?
- eventbasierte Aktualisierung
- lose Kopplung zwischen Zustandsquelle und Reaktionen
- GUIs, Domain Events, Cache Invalidierung, Pub/Sub

## Java Beispiel

```java
import java.util.ArrayList;
import java.util.List;

// Observer
sealed interface Observer permits ConsoleObserver {
    void update(String msg);
}

final class ConsoleObserver implements Observer {
    public void update(String msg) {
        System.out.println("received: " + msg);
    }
}

// Subject
final class Subject {
    private final List<Observer> observers = new ArrayList<>();

    public void attach(Observer o) { observers.add(o); }
    public void detach(Observer o) { observers.remove(o); }

    public void notifyAllObservers(String msg) {
        observers.forEach(o -> o.update(msg));
    }
}

// Client
public class App {
    public static void main(String[] args) {
        Subject newsFeed = new Subject();

        newsFeed.attach(new ConsoleObserver());
        newsFeed.attach(new ConsoleObserver());

        newsFeed.notifyAllObservers("Breaking News!");
    }
}
