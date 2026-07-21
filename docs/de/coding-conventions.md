# Allgemeine Richtlinien
Folgende Prinzipien sind zu berücksichtigen:

- KISS Keep it simple, stupid
- YAGNI You Aren’t Gonna Need It
- DRY Don't repeat yourself
- SRP Single-responsibility principle
- PLA Principle of least astonishment
- Information hiding
- Eingeschränke Pfadfinder-Regel: "Leave the ground cleaner..." -> aber nur in Klassen, die wg. der Userstory angefasst werden müssen.
- Beachte: Clean Code (Robert C. Martin)

# Sprache
- Die Dokumentationssprache (Sysspec, javadoc) ist deutsch (optional zusätzl. englisch)
- In Commits wird die englische Sprache verwendet. Fachliche Begriffe werden jedoch in Deutsch benannt (z. B. `calculateBedarf()`)
- Logausgaben im Code in Deutsch
- Diskussionen und Reviews in Deutsch

# Namenskonventionen
- Alle Artefakte (artifactId, Github-Repo) beginnen mit "dave"
- Attribute, Variablen, Methodenparameter und Methodennamen sind im Code der GUI sowie im backendseitigen Code grundsätzlich in [camelCase](https://en.wikipedia.org/wiki/Camel_case) zu schreiben (z.B. Dto).
- Alle Variablen und Parameter sind wenn möglich als `final` und `private` zu deklarieren.
- Konstanten sind als `private`, `static` und `final` sowie in **UPPER_CASE** zu definieren.

# Backend Conventions
- Fürs REFACTORING: Sauberes Dto-Pattern, Dto nur im Controller, im Service konkrete Klasse
- Fürs REFACTORING: Ein DTO pro konkrete Klasse, Ausnahmen müssen gut dokumentiert werden
- Wandlung von konkreter Klasse nach Dto nicht im Controller sondern in Serviceklasse durch Mapper (mapstruct, ...)
- Keine mehrfach verschachtelten Lambdas (kein .stream() im .stream())
- Das Java-Sprachfeature `var` kann verwendet werden, wenn der Datentyp eindeutig bei der Zuweisung erkennbar ist (z.B Ctor(), copy()).
- Urls sind in kepab-case zu definieren

# Frontend Conventions
- Die Bezeichner von Custom Components werden in HTML im kebab-case geschrieben, z.B.: `<abfrage-component/>`
- Alle Objekte, die in Komponenten benötigt werden, sind im Pinia-Store vorzuhalten und von dort zu holen.
- Statusänderungen eines Objektes sind über den Pinia-Store vorzunehmen und nicht über Events an übergeordnete Komponenten zurückzuspiegeln.
- Einheitliche Verwendung von Semikola in Frontend (immer anfügen)

# Tests
- getter etc müssen nicht getestet sein, alles andere möglichst schon
- Testmethoden: test<Methode>_With<Bedingung>

# Commits
- Beschreibung, was getan wurde (mit Verb!). Darf nicht "Code" drinstehen.
- Beim Mergen vom Feature-Branch nach sprint sollte der Titel der Userstory im Commit erscheinen.