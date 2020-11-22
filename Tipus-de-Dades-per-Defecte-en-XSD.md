# Tipus de Dades Simples

Del gran nombre de tipus de dades, aquí en mostrem 9:


* **xs:string**
```xml
<xs:element name="titol" type="xs:string"/>

<titol>El petit princep</títol>
```
On un xml và
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

* **Todos los tipos numericos**
Name	Description
byte	A signed 8-bit integer
decimal	A decimal value
int	A signed 32-bit integer
integer	An integer value
long	A signed 64-bit integer
negativeInteger	An integer containing only negative values (..,-2,-1)
nonNegativeInteger	An integer containing only non-negative values (0,1,2,..)
nonPositiveInteger	An integer containing only non-positive values (..,-2,-1,0)
positiveInteger	An integer containing only positive values (1,2,..)
short	A signed 16-bit integer
unsignedLong	An unsigned 64-bit integer
unsignedInt	An unsigned 32-bit integer
unsignedShort	An unsigned 16-bit integer
unsignedByte	An unsigned 8-bit integer

* **xs:boolean**
Els valors permesos son: true, false, 1 i 0.

```xml
<xs:attribute name="disabled" type="xs:boolean"/>
<xs:element name="pagado" type="xs:boolean"/>

<price disabled="true">999</price>
<pagado>false</pagado>
```

* **xs:hexBinary** i **xs:base64Binary**
```xml
<xs:element name="blobsrc" type="xs:hexBinary"/>
<xs:element name="blobsrc" type="xs:base64Binary"/>
```

* **xs:anyURI**
```xml
```

| Tipo | Declaración |
|-|-|
| cadena | xs:string
| fecha | xs:date
| hora | xs:time
|fecha y hora |
| periodo de tiempo |
| decimal | xs:decimal
| entero | xs:int xs:integer xs:positiveInteger xs:negativeInteger xs:nonpositiveInteger ...
| booleano | xs:boolean xs:bool
| hexBinario |