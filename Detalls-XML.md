# Detalls de XML
**XML** pot ser definit com un meta llenguatge ja que pot ser utilitzat per a crear (i definir) altres llenguatges com: XHTML.

A continuació exposem les regles que regeixen la construcció de XML:

* Un XML està escrit principalment en "text pla", ja que un dels objectius principals es la facilitat de lectura humana (en contrast amb els formats binaris que estan orientats a la lectura per programes)

* Les marques estan delimitades pels símbols `<`i `>` i les corresponents variants de etiqueta d'obertura (`<tag>`, tancament(`</tag>`) i buida (`<tag/>`).

* Els elements poden tenir definits atributs, que son parelles de nom d'atribut i valor (`atribut:valor`)

* Els elements han de format una estructura d'arbre (aniuament dels elements), o no hi poden haver solapament d'elements.

* El document XML només pot tenir una sola arrel, un sol node pare.

* Tots arxius XML ha de començar per una linia d'especificació, un element especial, que no forma part de l'arbre XML: `<?xml version = "1.0" encoding="UTF-8"?>`o `<?xml version = "1.0" encoding="UTF-8" standalone="yes"?>`

Si es compleixen totes aquestes regles els document XML es considerarà un document **ben format**, concepte molt utilitzat alhora de **validar** amb eines informàtiques els arxius **XML** juntament amb les descripcions de tipus **DTD** o **XSD**.

Un document **ben format** és aquell que compleix amb les regles bàsiques de XML.

# Següent: Exemples de XML i alguns errors comuns
[Exemples](https://github.com/jvidal86/M4.XML/wiki/Exemples-de-XML)

# Validació de XML

Com que amb XML definir un nou format d'arxiu, amb lexic i regles sintactiques particulars, hem de tenir les eines per a assegurar que aqueste s es compleixin i per tant poder **validar** un XML.

Les eines per definir les regles lexiques i sintàctiques més comuns son:

* **[DTD](https://github.com/jvidal86/M4.XML/wiki/DTD)**, senzilla però limitada, i basada en unes etiquetes que no son purament XML
* **[XSD](https://github.com/jvidal86/M4.XML/wiki/_new)**, més completa, basada en XML