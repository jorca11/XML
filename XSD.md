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
| Tipo | declración |
|-|-|
| cadena |
| fecha |
| hora |
|fecha y hora |
| periodo de tiempo |
| decimal |
| entero |
| booleano |
| hexBinario |

```xml
<xs:element name="biblioteca"/>

<xs:attribute name="abierto" type="xs:boolean"/>
```

## Elements Simples
Podem definir 9  tipus de dades simples


* **xs:string**
```xml
<xs:element name="titol" type="xs:string"/>

<titol>El petit princep</títol>
```

* **xs:date**
La data s'especifica en el format `YYYY-MM-DD`
```xml
<xs:element name="dataPubblicacio" type="xs:date"/>

<dataPublicacio>2005-03-12</dataPublicació>
```

* **xs:time**
```xml
<xs:element name="horaSalida" type="xs:time"/>

<horaSalida>21:00:00</horaSalida>
<horaEntrada>15:25:00+01:00</horaEntrada> <!--time zone +1h GMT-->
<momentoEvento>19:36:15.4</momentoEvento>
```
* **xs:dateTime**
```xml
```
* **xs:duration**
   * **P** indicates the period (required)
   * **nY** indicates the number of years
   * **nM** indicates the number of months
   * **nD** indicates the number of days
   * **T** indicates the start of a time section (required if you are going to specify hours, minutes, or seconds)
   * **nH** indicates the number of hours
   * **nM** indicates the number of minutes
   * **nS** indicates the number of seconds

```xml
<xs:element name="period" type="xs:duration"/>

<period>P5Y</period>
<period>P5Y2M10DT15H</period>
<period>PT15H</period>
```

* **xs:decimal**
```xml
<xs:element name="price" type="xs:decimal"/>

<price>999.50</price>
<price>+999.5450</price>
<price>-999.5230</price>
<price>14</price>
```
* **xs:integer**
```xml
<xs:element name="price" type="xs:integer"/>

<price>999</price>
<price>+999</price>
<price>-999</price>
```
* **xs:boolean**
```xml
```
* **xs:hexBinary**
```xml
```