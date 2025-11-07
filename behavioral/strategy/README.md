# 🧠 Strategy (Verhaltensmuster)

## Kategorie
Verhaltensmuster

## Idee
Definiert eine **Familie von Algorithmen**, kapselt jeden einzeln und macht sie **zur Laufzeit austauschbar** — ohne den Client-Code anzupassen.

## Einsatz / Wann benutzen?
- austauschbare Algorithmen / Berechnungslogik
- klare Trennung: *Was* tun wir (Context) → *Wie* tun wir (Strategy)
- Unit Tests einfacher: Strategien einzeln testbar

## Java Beispiel

```java
// Strategien
sealed interface PriceStrategy permits StandardPrice, DiscountPrice {
    double calculate(double base);
}

final class StandardPrice implements PriceStrategy {
    public double calculate(double base) { return base; }
}

final class DiscountPrice implements PriceStrategy {
    public double calculate(double base) { return base * 0.8; } // -20%
}

// Context
final class PriceContext {
    private PriceStrategy strategy;

    PriceContext(PriceStrategy strategy) { this.strategy = strategy; }

    public void setStrategy(PriceStrategy strategy) { this.strategy = strategy; }

    public double finalPrice(double base) {
        return strategy.calculate(base);
    }
}

// Client
public class App {
    public static void main(String[] args) {
        PriceContext ctx = new PriceContext(new StandardPrice());
        System.out.println(ctx.finalPrice(100)); // 100

        ctx.setStrategy(new DiscountPrice());
        System.out.println(ctx.finalPrice(100)); // 80
    }
}
