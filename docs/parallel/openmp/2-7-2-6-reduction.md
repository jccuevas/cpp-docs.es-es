---
title: 2.7.2.6 reduction
ms.date: 11/04/2016
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
ms.openlocfilehash: 54b326feb4e4ccf1f1da5c8152ffc8d1e4bd13b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456022"
---
# <a name="2726-reduction"></a>2.7.2.6 reduction

Esta cláusula realiza una reducción en las variables escalares que aparecen en *lista de variables*, con el operador *op*. La sintaxis de la `reduction` cláusula es como sigue:

> reducción (*op*: *variable lista*)

Una reducción se suele especificar para una instrucción con una de las formas siguientes:

> *x* = *x* *op* *expr*
> *x* *binop* = *expr*
> *x* = *expr* *op* *x* (excepto para la resta) *x*++
> ++*x*
> *x*--
> --*x*

donde:

*x*<br/>
Una de las variables de reducción especificadas en el `list`.

*lista de variables*<br/>
Una lista separada por comas de variables de reducción escalar.

*expr*<br/>
Una expresión con tipo escalar que no hace referencia a *x*.

*OP*<br/>
No es un operador sobrecargado, pero uno de +, &#42;, -, &amp;, ^, &#124;, &amp; &amp;, o &#124; &#124;.

*binop*<br/>
No es un operador sobrecargado, pero uno de +, &#42;, -, &amp;, ^, o &#124;.

El siguiente es un ejemplo de la `reduction` cláusula:

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

Como se muestra en el ejemplo, un operador puede estar oculto dentro de una llamada de función. El usuario debe tener cuidado de que el operador especificado en el `reduction` cláusula coincide con la operación de reducción.

Aunque el operando derecho de la &#124; &#124; operador tiene efectos secundarios en este ejemplo, se permiten, pero deben usarse con cuidado. En este contexto, puede producirse un efecto secundario que se garantiza que no se producen durante la ejecución secuencial del bucle durante la ejecución en paralelo. Esta diferencia puede producirse porque el orden de ejecución de las iteraciones es indeterminado.

El operador se utiliza para determinar el valor inicial de las variables privadas utilizadas por el compilador para la reducción y determinar el operador de finalización. Especificar explícitamente el operador permite la instrucción de reducción que pueden estar fuera de la extensión de la construcción de léxica. Cualquier número de `reduction` cláusulas se pueden especificar en la directiva, pero puede aparecer una variable en a lo sumo uno `reduction` cláusula para dicha directiva.

Una copia privada de cada variable en *lista de variables* se crean, uno para cada subproceso, como si el `private` cláusula hubiese utilizada. La copia privada se inicializa según el operador (consulte la tabla siguiente).

Al final de la región para el que el `reduction` se especificó la cláusula, el objeto original se actualiza para reflejar el resultado de combinar su valor original con el valor final de cada una de las copias privadas mediante el operador especificado. Los operadores de reducción son todas asociativos (excepto para la resta), y el compilador puede reasociar libremente el cálculo del valor final. (Los resultados parciales de una reducción de la resta se suman para formar el valor final).

El valor del objeto original se convierte en indeterminado cuando el primer subproceso llega a la cláusula contenedora y permanece así hasta que finalice el cálculo de reducción.  Normalmente, el cálculo se completará al final de la construcción; Sin embargo, si la `reduction` cláusula se usa en una construcción que `nowait` es también se aplica el valor del objeto original permanece indeterminado hasta que se ha realizado una sincronización de barrera para asegurarse de que todos los subprocesos han completado la `reduction`cláusula.

En la tabla siguiente se enumera los operadores que son válidos y sus valores de inicialización canónico. El valor de inicialización real será coherente con el tipo de datos de la variable de reducción.

|Operador|Inicialización|
|--------------|--------------------|
|+|0|
|&#42;|1|
|-|0|
|&amp;|~0|
|&#124;|0|
|^|0|
|&amp;&amp;|1|
|&#124;&#124;|0|

Las restricciones para el `reduction` cláusula son los siguientes:

- El tipo de las variables en el `reduction` cláusula debe ser válida para el operador de reducción, salvo que nunca se permiten los tipos de puntero y tipos de referencia.

- Una variable que se especifica en el `reduction` cláusula no debe ser **const**-completo.

- Las variables que son privadas dentro de una región paralela o que aparecen en la `reduction` cláusula de una **paralelo** directiva no se puede especificar en un `reduction` cláusula en una directiva de uso compartido que se enlaza a la construcción paralela.

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }

   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```
