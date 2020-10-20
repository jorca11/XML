# Exemples de XML

* Un XML ben format (i ben *indentat*)

```xml
<?xml version = "1.0" encoding="UTF-8" standalone="yes"?>
<document>
  <employee>
    <name>
      <lastname>Kelly</lastname>
      <firstname>Grace</firstname>
    </name>
    <hiredate>October 15, 2005</hiredate>
    <projects>
      <project>
        <product>Printer</product>
        <id>111</id>
        <price>$111.00</price>
      </project>
      <project>
        <product>Laptop</product>
        <id>222</id>
        <price>$989.00</price>
      </project>
    </projects>
  </employee>
  <employee>
    <name>
      <lastname>Grant</lastname>
      <firstname>Cary</firstname>
    </name>
    <hiredate>October 20, 2005</hiredate>
    <projects>
      <project>
        <product>Desktop</product>
        <id>333</id>
        <price>$2995.00</price>
      </project>
    </projects>
  </employee>
</document>
```
On:
* Node arrel: `<document>`
* Fills de l'arrel: `<employee>`
* Fills d'employee: `<name>`, `<hiredsate>`i `<projects>``
* Fills de name: `<firstname>`i `<lastname>`
* Fills de projects: `<project>``
* Fills de project: `<product>`, `<id>`i `<price>``

Observacions per deduir les regles sintàctiques:

* 1 *document* pot tenir diversos fills, i només poden ser *employee*. Podria tenir sentit que inicialment en crear el `<document>`hi hagués 0 employees.

* 1 *employee* té 3 fills i per claredat apareixen en el mateix ordre: *name*, *hiredate* i *projects*. Sembla que els 3 son obligatòris d'omplir, si no no tendria sentit.

* l'element *name* tés 2 fills que semblen obligatòris i apareixen en el mateix ordre.

* L'element *projects* pot tenir més d'1 fill project (noteu la utilització de plurals i singulars). Sembla que no tindria sentit que en tingués 0.

* Cada *project* tés 3 fills i que sembla que apareixen en el mateix ordre.

* El contingut de tots els elements es de tipus *text*.

## Exemples amb errors

* Multiples arrels

```xml
<?xml version="1.0" encoding="UTF-8"?>
<note>
<to>Tove</to>
<from>Jani</from> 
<heading>Reminder</heading>
<body>Don't forget me this weekend!</body>
</note>
<note>
<to>Tove</to>
<from>Jani</from> 
<heading>Reminder</heading>
<body>Don't forget me this weekend!</body>
</note>
```

* Etiquetes no correctament emparellades
```xml
<?xml version="1.0" encoding="UTF-8"?>
<note>
<to>Tove</to>
<from>Jani</from> 
<heading>Reminder</pheading>
<body>Don't forget me this weekend!</body>
</note>
```