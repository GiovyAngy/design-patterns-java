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

## Ziel

Dieses Repository ist bewusst **kompakt**, lesbar und für eine allgemeine Wiederholung der behandelten Themen geeignet: keine übermäßig komplizierten realen Domänen.
Fokus: schnell verständliche Konzepte + didaktische Verwendung von modernem Java.

---

## Java Version

Java **21** (LTS)  
→ empfohlen: `sdkman` oder Amazon Corretto installieren.

```bash
java -version
