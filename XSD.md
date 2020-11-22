# Creació d'Esquemes amb *XSD*

## Avantatges respecte DTD

* Permet especificar tipus de dades
* Permet crear nous tipus derivats de dades
* especificat 100% en xml

# Casos Pràctics
  * Cas 1: [libros](https://github.com/jvidal86/M4.XML/wiki/Cas-pr%C3%A0ctic-1-XSD---Libros)


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

## Definir un Element amb Fills

Un element que contingui *fills* es considerat un tipus complexe. Per exemple:

```xml
<adreca>
  <carrer>C/ Diputació</carrer>
  <numero>155</numero>
  <pis> 1r 2a B</pis>
  <CP>28732</CP>
  <provincia>Girona</provincia>
</adreca>
```

```xml
<xs:element adreça>
 <xs:complexType>
  <xs:sequence>
   <xs:element name="carrer" type="xs:string"/>
   <xs:element name="numero" type="xs:positiveInteger"/> 
   <xs:element name="pis" type="xs:string"/>
   <xs:element name="CP" type="xs:positiveInteger"/>
   <xs:element name="provincia" type="xs:string"/>
  </xs:sequence>
 </xs:complexType>
</xs:element>
```

## Definir atributs per a un Element

Afegir atributs a un element també es considera que es un tipus *complexe*.

```xml
<treballador categoria="tècnic"/>
```
```xml
<xs:element name="treballador">
 <xs:complexType>
  <xs:attribute name="categoria" type="xs:string"/>
 </xs:complexType>
<xs:element>
```

Si a més a més l'element amb atributs té un contingut *simple*, es a dir sense fills, o element fulla, llavors

```xml
```

```xml
```
## Tipus de Dades Simples de XSD

Veure la pàgina [següent](https://github.com/jvidal86/M4.XML/wiki/Tipus-de-Dades-per-Defecte-en-XSD)

