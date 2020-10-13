# DTD

DTD (*Document Type Definition*) especifica el lèxic i la sintaxis per a **validar** un determinat XML.
El *lèxic* especifica el vocabulari acceptat: noms d'elements, atributs i valors acceptats.
La *sintaxis* especifica les regles de composició dels elements i els atributs disponibles per a cada element.

# Inserir un DTD en un XML

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE element_arrel [
]>
<element_arrel>
<element_arrel/>
````

# Enllaçar un DTD extern ammb un XML

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE resume SYSTEM "file:/C:/m04-uf1/extern-resume.dtd">
<resume>
```
# Blocs d'un DTD

* Element
* Atribut
* Entitat: caràcters especials. Una entitat es substituida durant la seva interpretació pel seu equivalent.
* PCData: *Parsed Character Data*
* CData: *Character Data*

# Elements

```xml
<!ELEMENT nom_element (llista_nodes_fills)>
```
o
```xml
<!ELEMENT nom_element categoria>
```


# Composició d'elements

* Seqüència de fills:
Els elements fills han d'aparèixer exactament 1 vegada i en l'ordre especificat en el llistat de fills 
```xml
<!ELEMENT pare (fill1 , fill2 , ... , fill-n)>
```

* Composició alternativa exclusiva
Només un dels elements pot aparèixer

```xml
<!ELEMENT pare (fill1 | fill2 | ... | fill-n)>
```

* Repeticions
  * `+`: L'element es pot repetir 1 o més vegades
  * `*`: L'element es pot repetir 0 o més vegades
  * `?`: L'element es pot repetir 0 o 1 vegada

Les repeteicions es poden agrupar en sub-llistes

# Atributs

Els atributs son una parella de nom_atribut i valor. En el DTD s'epecifica un atribut per a un determinat element amb un `<!ATTLIST>`. També el tipus d'atribut, però el seu contingut *no* es pot limitar massa. Aquesta falta d'especificació dels valors acceptats pels atrtibuts fa que els DTDs siguin fàcils però menys potents. La tecnologia XSD serà mès adequada per a esquemes més detallats.

Sintaxis d'un atribut:
```xml
<!ATTLIST nom_element nom_atribut tipus valor_per_defecte>
```

* Tipus d'atributs:
  * CDATA: Text amb espais
  * ID: Un identificador
  * IDREF: Referència a un identificador
  * ENTITY
  * ENTITIES
  * NMTOKEN
  * NMTOKENS

* Valor per defecte
  * #REQUIRED: Obligatorui
  * #IMPLIED: Opcional
  * #FIXED *valor* : Valor fixat amb *valor*