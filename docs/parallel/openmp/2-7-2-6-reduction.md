---
title: "2.7.2.6 reducción de | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 684067eae668398e71ca4ace0cc136e3210e0dbf
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2018
---
# <a name="2726-reduction"></a>2.7.2.6 reduction

Esta cláusula lleva a cabo una reducción en las variables escalares que aparecen en *lista de variables*, con el operador *op*. La sintaxis de la `reduction` cláusula es como sigue:

> reducción (*op*: *lista de variables*)

Normalmente, se especifica una reducción para una instrucción con una de las formas siguientes:

> *x* = *x* *op* *expr*  
> *x* *binop* = *expr*  
> *x* = *expr* *op* *x* (a excepción de resta)  
> *x*++  
> ++*x*  
> *x*--  
> --*x*  

donde:

*x*  
Una de las variables de reducción especificadas en el `list`.

*variable-list*  
Una lista separada por comas de variables de reducción escalar.

*expr*  
Una expresión con un tipo escalar que no hace referencia a *x*.

*op*  
No es un operador sobrecargado, pero uno de +, &#42;, -, &amp;, ^, &#124;, &amp; &amp;, o &#124; &#124;.

*binop*  
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
  
Como se muestra en el ejemplo, un operador puede estar ocultos dentro de una llamada de función. El usuario debe tener cuidado de que el operador especificado en el `reduction` cláusula coincide con la operación de reducción.

Aunque el operando derecho de la &#124; &#124; operador no tiene efectos secundarios en este ejemplo, se permiten, pero deben utilizarse con cuidado. En este contexto, un efecto secundario que se garantiza que no se producen durante la ejecución secuencial del bucle pueden producirse durante la ejecución en paralelo. Esta diferencia puede producirse porque el orden de ejecución de las iteraciones es indeterminado.

Este operador se usa para determinar el valor inicial de las variables privadas utilizado por el compilador para la reducción y para determinar el operador de finalización. Especificar explícitamente el operador permite la instrucción de reducción debe estar fuera de la extensión léxica de la construcción. Cualquier número de `reduction` cláusulas se pueden especificar en la directiva, pero una variable puede aparecer en al menos uno `reduction` cláusula para dicha directiva.

Una copia privada de cada variable de *lista de variables* se crea, uno para cada subproceso, como si el `private` cláusula hubiese utilizada. La copia privada se inicializa según el operador (vea la tabla siguiente).

Al final de la región para el que el `reduction` se especificó la cláusula, el objeto original se actualiza para reflejar el resultado de combinar su valor original con el valor final de cada una de las copias privadas utilizando el operador especificado. Los operadores de reducción son todos los asociativos (a excepción de resta) y el compilador puede volver a asociar el cálculo del valor final libremente. (Los resultados parciales de una reducción de resta se agregan para formar el valor final).

El valor del objeto original vuelve al estado indeterminado cuando el primer subproceso llega a la cláusula que lo contiene y permanece así hasta que se complete el cálculo de la reducción.  Normalmente, el cálculo se completará al final de la construcción; Sin embargo, si la `reduction` cláusula se usa en una construcción que `nowait` es también se aplica, el valor del objeto original sigue siendo indeterminado hasta que se ha realizado una sincronización de barrera para asegurarse de que todos los subprocesos han completado la `reduction`cláusula.

En la tabla siguiente se enumera los operadores que son válidos y sus valores de inicialización canónica. El valor de inicialización real será coherente con el tipo de datos de la variable de reducción.

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

Las restricciones a la `reduction` cláusula son los siguientes:

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
