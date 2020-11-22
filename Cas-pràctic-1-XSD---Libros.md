# Caso Práctico 1 de XSD

Este es el 1r tutorial de una serie que mostrarà como crear esquemas de validacion de XML.

XSD es más complejo, a la par que más potente, que DTD.

En este primer tutorial veremos los aspectos más bàsicos y novedosos de XSD
* Definicion de Tipos Complejos
* Uso de tipos bàsicos

# Objetivo

Crear un esquema de validación en XSD para el siguiente xml.

```xml
<libros>
    <libro disponible="true">
        <titulo>The Elements</titulo>
        <fechaPubli>2000-11-24</fechaPubli>
        <ref>23-TE</ref>
        <precio>12.45</precio>
    </libro>
    <libro disponible="true">
        <titulo>Alquimia</titulo>
        <fechaPubli>1988-01-02</fechaPubli>
        <ref>13-Al</ref>
        <precio divisa="$">25.24</precio>
    </libro>
    <libro disponible="false">
        <titulo>El Médico</titulo>
        <fechaPubli>2007-07-30</fechaPubli>
        <ref>09-EM</ref>
        <precio divisa="€">30.12</precio>
    </libro>   
</libros>
```

## Paso 1: Definir el elemento raiz y sus hijos

Un elemento se define con la etiqueta:

```xml
<xs:element name="nomnbre_elemento">
```
Si es un elemento final, su tipo se especifica como un argumento y se puede escjer unos de los multiples tipos bàsicos existente en XSD. Por ejemplo:

```xml
<xs:element name="nombre" type="xs:string"/>
<xs:element name="edad" type="xs:positiveInteger"/>
<xs:element name="fechaNacimiento" type="xs:date"/>
```

Pero si el elemento va a contener otros elementos, Los elementos hijos se declaran dentro de un elemento **complejo**. Ademàs tambien tendremos que especificacar si les elementos hijos son
* una sequencia
* se escoje uno solo
* pueden aparecer todos en qualquier orden

```xml
<xs:element name="raiz">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="hijo1"/>
      <xs:element name="hijo2"/>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

Volviendo al ejemplo inicial, vamos a declarar el elemento raiz **libros** y el elemento hijo (solo hay un tipo) **hijo**.

```xml
<xs:element name="libros">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="libro"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
```

El siguiente paso es indicar la **repetición** del elemento `<libro>`. En XSD hay dos atributos para definirla:
* `minOccurs` : número mínimo de ocurrencias
* `maxOccurs`: número màximo de ocurrencias, y *unbounded* para indicar *infinitas* veces

Ampliando el ejemplo anterior
```xml
<xs:element name="libros">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="libro" minOccurs="1" maxOccurs="unbounded"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
```
Con este XSD, podemos validar, a modo ilustrativo, el siguiente XML

```xml
<?xml version="1.0" encoding="UTF-8"?>
<libros xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:noNamespaceSchemaLocation="libros00.xsd">
    <libro/>
    <libro></libro>
</libros>
```


---
## Paso 2: Definir los hijos de `<libro>`

En este paso definiremos los hijos (elementos hoja) del xml de este tutorial. En este caso, estos nodos ya no seran de *tipo complejo* sino que podremos hacer uso de los tipos que trae XSD por defecto.

Primero, como el contenido de libro son varios hijos, abriremos con un elemento *complejo* y una *sequencia*.

Cada elemento especifica el tipo de contenido mediante el atributo `type`.


```xml
<xs:element name="libro" maxOccurs="unbounded" minOccurs="1">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="titulo" type="xs:string"/>
            <xs:element name="fechaPubli" type="xs:date"/>
            <xs:element name="ref" type="xs:string"/>
            <xs:element name="precio" type="xs:decimal"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
```


----
## Paso 3: Añadir el atributo `<libro disponible="">`

Para definir un atributo usaremos, por ejemplo:

```xml
<xs:attribute name="ID" type="xs:string" use="optional">
````

Donde vemos que los atributos tambien usan los tipos definidos en XSD, y u uso puede ser *optional* o *required*

Los atributos son **solo** parte de elementos **complejos**, y se definen dentro de un elmento `<xs:complexType>`.

çasi que en el ejmeplo de este tutorial, el atributo `disponible`de `<libro>` se define **despues** de *sequence*.

```xml
<xs:element name="libro" maxOccurs="unbounded" minOccurs="1">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="titulo" type="xs:string"/>
            <xs:element name="fechaPubli" type="xs:date"/>
            <xs:element name="ref" type="xs:string"/>
            <xs:element name="precio" type="xs:decimal"/>
        </xs:sequence>
        <xs:attribute name="disponible" type="xs:boolean" default="true" use="required"/>
    </xs:complexType>
</xs:element>
```

## Pase 4: Añadir atributo a un elemento final `<precio divisa="">`

Añadir un atributo a un elemento final, eno es tant obvio como parece.
Uno podria pensar que para añadir el atributo `divisa`, solo hay que escrivir

```xml
<xs:element name="precio" type="xs:decimal">
    <xs:complexType>
        <xs:attribute name="divisa" type="xs:string" default="€" use="optional"/>
    </xs:complexType>
</xs:element>
````

Pero esto no es así.


En realidad al añadir el atributo a través de un `<xs:complexType>`, el atributo `type="xs:decimal"`queda invalidado.

La manera de resolver esta situación és:


```xml
<xs:element name="precio">
    <xs:complexType>
        <xs:simpleContent>
            <xs:extension base="xs:decimal">
                <xs:attribute name="divisa" type="xs:string" default="€" use="optional"/>
            </xs:extension>
        </xs:simpleContent>
    </xs:complexType> 
</xs:element>
```

Y con esto ya tenemos la primera version del XSD, que nos permite validar el ejemplo inicial.

El código completo es:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="libros">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="libro" maxOccurs="unbounded" minOccurs="1">
                    <xs:complexType>
                        <xs:sequence>
                            <xs:element name="titulo" type="xs:string"/>
                            <xs:element name="fechaPubli" type="xs:date"/>
                            <xs:element name="ref" type="xs:string"/>
                            <xs:element name="precio">
                                <xs:complexType>
                                    <xs:simpleContent>
                                        <xs:extension base="xs:decimal">
                                            <xs:attribute name="divisa" type="xs:string" default="€" use="optional"/>
                                        </xs:extension>
                                    </xs:simpleContent>
                                </xs:complexType> 
                            </xs:element>
                        </xs:sequence>
                        <xs:attribute name="disponible" type="xs:boolean" default="true" use="required"/>
                    </xs:complexType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```
