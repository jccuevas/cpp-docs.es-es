---
title: sizeof (Operador) (C)
ms.date: 11/04/2016
f1_keywords:
- sizeof
helpviewer_keywords:
- sizeof operator
ms.assetid: 70826d03-3451-41e4-bebb-a820ae66d53f
ms.openlocfilehash: 0bc0de5481cade10f89634d9e4ec78f4ec7b09f6
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149562"
---
# <a name="sizeof-operator-c"></a>sizeof (Operador) (C)

El operador `sizeof` proporciona la cantidad de almacenamiento, en bytes, necesaria para almacenar un objeto del tipo del operando. Este operador permite no tener que especificar tamaños de datos dependientes del equipo en los programas.

## <a name="syntax"></a>Sintaxis

```
sizeof unary-expression
sizeof ( type-name )
```

## <a name="remarks"></a>Comentarios

El operando es un identificador que es un elemento *unary-expression* o una expresión de conversión de tipo (es decir, un especificador de tipo incluido entre paréntesis). El elemento *unary-expression* no puede representar un objeto de campo de bits, un tipo incompleto ni un designador de función. El resultado es una constante entera sin signo. El encabezado estándar STDDEF.H define este tipo como **size_t**.

Cuando se aplica el operador `sizeof` a un identificador de matriz, el resultado es el tamaño de la matriz completa en lugar del tamaño del puntero representado por el identificador de matriz.

Cuando se aplica el operador `sizeof` a un nombre de tipo de estructura o unión, o a un identificador de tipo de estructura o unión, el resultado es el número de bytes de la estructura o unión, incluidos los caracteres de relleno internos y finales. Este tamaño puede incluir caracteres de relleno internos y finales utilizados para ajustar los miembros de la estructura o unión a los límites de memoria. Por tanto, el resultado no se corresponde necesariamente con el tamaño que se calcula sumando los requisitos de almacenamiento de los distintos miembros.

Si una matriz sin tamaño es el último elemento de una estructura, el operador `sizeof` devuelve el tamaño de la estructura sin la matriz.

```
buffer = calloc(100, sizeof (int) );
```

En este ejemplo se utiliza el operador `sizeof` para pasar el tamaño de un `int`, que varía según el equipo, como un argumento de una función en tiempo de ejecución denominada `calloc`. El valor devuelto por la función se almacena en `buffer`.

```
static char *strings[] = {
      "this is string one",
      "this is string two",
      "this is string three",
   };
const int string_no = ( sizeof strings ) / ( sizeof strings[0] );
```

En este ejemplo, `strings` es una matriz de punteros a `char`. El número de punteros es el número de elementos de la matriz, pero no se especifica. Es fácil determinar el número de punteros utilizando el operador `sizeof` para calcular el número de elementos de la matriz. El valor entero **const** `string_no` se inicializa en este número. Como es un valor **const**, `string_no` no puede modificarse.

## <a name="see-also"></a>Vea también

[Operadores de C](c-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
