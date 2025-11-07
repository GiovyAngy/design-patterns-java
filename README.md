# Java Design Patterns (Java 21)

Dieses Repository enthält kompakte, minimalistische Beispiele zu den wichtigsten klassischen GoF Design Patterns – in **modernem Java 21** (sealed interfaces, switch expressions), jeweils mit kurzer Definition + kleinem Beispiel.

## Struktur

| Kategorie | Patterns |
|---|---|
| Erzeugungsmuster (Creational) | Factory, Abstract Factory |
| Strukturmuster (Structural) | Adapter, Decorator |
| Verhaltensmuster (Behavioral) | Strategy, Observer |

---

## Creational (Erzeugungsmuster)

| Pattern | Kurzbeschreibung | Link |
|---|---|---|
| 🏭 Factory | kapselt Objekterzeugung; entscheidet zentral welcher konkrete Typ erstellt wird | https://github.com/GiovyAngy/design-patterns-java/tree/main/creational/factory |
| 🧪 Abstract Factory | erzeugt ganze Produktfamilien ohne konkrete Klassen zu kennen | https://github.com/GiovyAngy/design-patterns-java/tree/main/creational/abstract%20Factory |

---

## Structural (Strukturmuster)

| Pattern | Kurzbeschreibung | Link |
|---|---|---|
| 🔌 Adapter | lässt inkompatible Interfaces zusammenarbeiten | https://github.com/GiovyAngy/design-patterns-java/tree/main/structural/adapter |
| 🎀 Decorator | fügt Verhalten dynamisch hinzu ohne Subklassen | https://github.com/GiovyAngy/design-patterns-java/tree/main/structural/decorator |

---

## Behavioral (Verhaltensmuster)

| Pattern | Kurzbeschreibung | Link |
|---|---|---|
| 🧠 Strategy | austauschbare Algorithmen zur Laufzeit | https://github.com/GiovyAngy/design-patterns-java/tree/main/behavioral/strategy |
| 👀 Observer | 1 → n Abhängigkeit, automatische Benachrichtigung bei Zustandsänderung | https://github.com/GiovyAngy/design-patterns-java/tree/main/behavioral/observer |

---

## Vergleichstabelle

| Pattern | Kategorie | Einsatz (Wann?) | Vorteile | Nachteile |
|---|---|---|---|---|
| Factory | Erzeugungsmuster | zentrale Auswahl + Erstellung eines konkreten Subtyps | Aufrufer entkoppelt; einheitliche Erzeugung | Fabrik kann zu viel Logik sammeln |
| Abstract Factory | Erzeugungsmuster | ganze Produktfamilien austauschbar machen | konsistente Produkte; Welten leicht wechselbar | mehr Abstraktion / Interfaces notwendig |
| Adapter | Strukturmuster | inkompatible Interfaces integrieren | Wiederverwendung von Legacy / Fremd-Code | zusätzliche Schicht; evtl. Overhead |
| Decorator | Strukturmuster | Verhalten dynamisch ergänzen ohne Subklassen | kombinierbare Erweiterungen; kein Klassenbloat | verschachtelte Wrapper erschweren Debugging |
| Strategy | Verhaltensmuster | Algorithmen austauschbar zur Laufzeit | sehr testbar; klare Trennung | Auswahl-Logik muss definiert werden |
| Observer | Verhaltensmuster | automatische Updates bei Zustandänderung | lose Kopplung / PubSub | potentielle Memory-Leaks + Race Conditions |


## Ziel

Dieses Repository ist bewusst **kompakt**, lesbar und für eine allgemeine Wiederholung der behandelten Themen geeignet: keine übermäßig komplizierten realen Domänen.
Fokus: schnell verständliche Konzepte + didaktische Verwendung von modernem Java.

---

## Java Version

Java **21** (LTS)  
→ empfohlen: `sdkman` oder Amazon Corretto installieren.

```bash
java -version
