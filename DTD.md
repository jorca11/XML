# DTD

DTD (*Document Type Definition*) especifica el lèxic i la sintaxis per a **validar** un determinat XML.
El *lèxic* especifica el vocabulari acceptat: noms d'elements, atributs i valors acceptats.
La *sintaxis* especifica les regles de composició dels elements i els atributs disponibles per a cada element.

# Blocs d'un DTD

* Element
* Atribut
* Entitat: caràcters especials. Una entitat es substituida durant la seva interpretació pel seu equivalent.
* PCData: *Parsed Character Data*
* CData: *Character Data*

# Elements

```dtd
<!ELEMENT nom_element (llista_nodes_fills)>
```
o
```dtd
<!ELEMENT nom_element categoria>
```


# Composició d'elements

* Seqüència de fills:
Els elements fills han d'aparèixer exactament 1 vegada i en l'ordre especificat en el llistat de fills 
```html
<!ELEMENT pare (fill1 , fill2 , ... , fill-n)>
```

* Composició alternativa exclusiva
Només un dels elements pot aparèixer

```dtd
<!ELEMENT pare (fill1 | fill2 | ... | fill-n)>
```

* Repeticions
  * `+`: L'element es pot repetir 1 o més vegades
  * `*`: L'element es pot repetir 0 o més vegades
  * `?`: L'element es pot repetir 0 o 1 vegada

Les repeteicions es poden agrupar en sub-llistes