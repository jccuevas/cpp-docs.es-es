---
title: Operadores relacionales y de igualdad de C
ms.date: 10/18/2018
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
ms.openlocfilehash: 78dfd9f208b4c5cf484f0ff43c5e07ce1aadec35
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149653"
---
# <a name="c-relational-and-equality-operators"></a>Operadores relacionales y de igualdad de C

Los operadores relacionales y de igualdad binarios comparan el primer operando con el segundo para probar la validez de la relación especificada. El resultado de una expresión relacional es 1 si la relación probada es true y 0 si es false. El tipo del resultado es `int`.

**Sintaxis**

*relational-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **&lt;** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **>** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **&lt;=** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **>=** *shift-expression*<br/>

*equality-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression* **==** *relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression* **!=** *relational-expression*

Los operadores relacionales y de igualdad prueban las relaciones siguientes:

|Operador|Relación probada|
|--------------|-------------------------|
|**&lt;**|Primer operando menor que el segundo operando|
|**>**|Primer operando mayor que el segundo operando|
|**&lt;=**|Primer operando menor o igual que segundo operando|
|**>=**|Primer operando mayor o igual que segundo operando|
|**==**|Primer operando igual a segundo operando|
|**!=**|Primer operando no igual a segundo operando|

Los cuatro primeros operadores de la lista anterior tienen mayor prioridad que los operadores de igualdad (`==` y `!=`). Vea la información de prioridad en la tabla [Prioridad y asociatividad de los operadores de C](../c-language/precedence-and-order-of-evaluation.md).

Los operandos pueden tener tipo entero, flotante o puntero. Los tipos de operando pueden ser diferentes. Los operadores relacionales realizan las conversiones aritméticas habituales sobre operandos de tipo entero y flotante. Además, puede usar las siguientes combinaciones de tipos de operando con los operadores relacionales y de igualdad:

- Ambos operandos de cualquier operador relacional o de igualdad puede ser punteros al mismo tipo. Para los operadores de igualdad (`==`) y desigualdad (`!=`), el resultado de la comparación indica si los dos punteros direccionan la misma ubicación de memoria. Para los otros operadores relacionales (**\<**, **>**, **\<**= y **>**=), el resultado de la comparación indica la posición relativa de las dos direcciones de memoria de los objetos a los que se señala. Los operadores relacionales comparan solo desplazamientos.

   La comparación de puntero solo se define para partes del mismo objeto. Si los punteros hacen referencia a miembros de una matriz, la comparación es equivalente a la comparación de los subíndices correspondientes. La dirección del primer elemento de la matriz es “menor que” la dirección del último elemento. En el caso de las estructuras, los punteros a miembros de estructura declarados más tarde son “mayores que” los punteros a miembros declarados antes en la estructura. Los punteros a los miembros de la misma unión son iguales.

- Un valor de puntero se puede comparar con el valor constante 0 para igualdad (`==`) o desigualdad (`!=`). Un puntero a un valor de 0 se denomina un puntero “NULL”; es decir, no señala a una ubicación de memoria válida.

- Los operadores de igualdad siguen las mismas reglas que los operadores relacionales, pero permiten posibilidades adicionales: un puntero se puede comparar con una expresión entera constante con valor 0 o con un puntero a `void`. Si dos punteros son ambos nulos, se consideran iguales. Los operadores de igualdad comparan tanto el segmento como el desplazamiento.

## <a name="examples"></a>Ejemplos

En los ejemplos siguientes se muestran los operadores relacionales y de igualdad.

```C
int x = 0, y = 0;
if ( x < y )
```

Dado que `x` y `y` son iguales, la expresión de este ejemplo produce el valor 0.

```C
char array[10];
char *p;

for ( p = array; p < &array[10]; p++ )
    *p = '\0';
```

El fragmento de este ejemplo establece cada elemento de `array` en una constante de carácter nulo.

```C
enum color { red, white, green } col;
   .
   .
   .
   if ( col == red )
   .
   .
   .
```

Estas instrucciones declaran una variable de enumeración denominada `col` con la etiqueta `color`. En cualquier momento, la variable puede contener un valor entero de 0, 1, 2, que representa uno de los elementos del conjunto de enumeración `color`: el color rojo, blanco o verde, respectivamente. Si `col` contiene 0 cuando se ejecuta la instrucción **if**, se ejecutará cualquier instrucción que dependa de **if**.

## <a name="see-also"></a>Vea también

[Operadores relacionales: \<, >, \<= y >=](../cpp/relational-operators-equal-and-equal.md)<br/>
[Operadores de igualdad: == y !=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)
