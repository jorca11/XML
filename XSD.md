# Creació d'Esquemes amb *XSD*

## Avantatges respecte DTD

* Permet especificar tipus de dades
* Permet crear nous tipus derivats de dades
* especificat 100% en xml

# Arrel de l'esquema

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

</xs:schema>
```


## Definir Elements i Atributs

Per exemple:
```xml
<xs:element name="biblioteca" type="xs:string"/>

<xs:attribute name="abierto" type="xs:boolean"/>
```
Un exemple seria:

```xml
<biblioteca abierto="true">
 Atlántida
</biblioteca>
```

