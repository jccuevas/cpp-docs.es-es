---
title: Operadores de direccionamiento indirecto y address-of | Microsoft Docs
ms.custom: ''
ms.date: 02/16/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- address-of operator (&)
- '* operator'
- operators [C++], address-of
- ampersand operator (&)
- '* operator, indirection operator'
- addresses [C++], indirection
- addresses [C++]
- indirection operator
- '& operator, address-of operator'
- null pointers [C++]
- '* operator, address-of operator'
- operators [C++], indirection
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75afd44b8c0a31d9f3731a4c6f9fb86c15de4328
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="indirection-and-address-of-operators"></a>Operadores de direccionamiento indirecto y address-of

El operador unario de direccionamiento indirecto (__&#42;__) accede a un valor indirectamente, mediante un puntero. El operando debe ser un tipo de puntero. El resultado de la operación es el valor al que hace referencia el operando; es decir, el valor de la dirección a la que señala el operando. El tipo del resultado es el tipo al que apunta el operando.

El resultado del operador de direccionamiento indirecto es *type* si el operando es del tipo *pointer to type*. Si el operando señala a una función, el resultado es un designador de función. Si señala a un objeto, el resultado es un valor L que designa el objeto.

Si el valor del puntero no es válido, el resultado del operador de direccionamiento indirecto es indefinido. Estas son algunas de las condiciones más comunes que invalidan un valor de puntero:

- El puntero es un puntero null.

- El puntero especifica una dirección de un objeto una vez que su duración ha finalizado (por ejemplo, un objeto que ha salido del ámbito o que se ha desasignado) en el momento de la referencia.

- El puntero especifica una dirección que está alineada de una forma no adecuada para el tipo de objeto al que se señala.

- El puntero especifica una dirección no utilizada por el programa que se ejecuta.

El operador unario address-of (**&**) proporciona la dirección de su operando. El operando debe ser un valor L que designe un objeto que no esté declarado como __registro__ y no sea un campo de bits, o bien el resultado de un operador unario __&#42;__ de un operador de desreferencia de matriz (__&#91;&#93;__) o, por último, un designador de función. El resultado es del tipo *pointer to type* para un operando de tipo *type*.

Si el operando es el resultado de un operador unario __&#42;__, no se evaluará ningún operador y el resultado será el mismo que si se hubiesen omitido ambos. El resultado no es un valor L, y se siguen aplicando las restricciones de los operadores. Si el operando es el resultado de un operador __&#91;&#93;__, no se evaluarán ni el operador __&__ ni el unario __&#42;__ implicados por el operador __&#91;&#93;__. El resultado tiene el mismo efecto que si se eliminase el operador __&__ y se cambiase el operador __&#91;&#93;__ por un operador __+__. De lo contrario, el resultado es un puntero que señala al objeto o a la función designados por el operando.


## <a name="examples"></a>Ejemplos

En los ejemplos siguientes se usan estas declaraciones comunes:

```C
int *pa, x;
int a[20];
double d;
```

Esta instrucción utiliza el operador address-of (**&**) para tomar la dirección del sexto elemento de la matriz `a`. El resultado se almacena en la variable de puntero `pa`:

```C  
pa = &a[5];
```

En este ejemplo se utiliza el operador de direccionamiento indirecto (__&#42;__) para acceder al valor `int` de la dirección almacenada en `pa`. El valor se asigna a la variable de entero `x`:

```C
x = *pa;
```

En este ejemplo se muestra que el resultado de aplicar el operador de direccionamiento indirecto a la dirección de `x` es igual que `x`:

```C
assert( x == *&x );
```

En este ejemplo se muestran otras maneras de declarar un puntero a una función:

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```  

Una vez declarada la función `roundup`, se declaran y se inicializan dos punteros a `roundup`. El primer puntero, `proundup`, se inicializa solo con el nombre de la función, mientras que el segundo, `pround`, utiliza el operador address-of en la inicialización. Las inicializaciones son equivalentes.

## <a name="see-also"></a>Vea también

[Operador de direccionamiento indirecto: &#42;](../cpp/indirection-operator-star.md)  
[address-of (Operador): &](../cpp/address-of-operator-amp.md)  
