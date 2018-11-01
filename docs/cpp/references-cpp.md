---
title: Referencias (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- objects [C++], referencing
- references [C++]
- references, to pointers
- declarations, references
- references, declaring
- referencing objects, declarator syntax
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
ms.openlocfilehash: aafc582299402eabab2736ac7d07b6c4c397413c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616475"
---
# <a name="references-c"></a>Referencias (C++)

Una referencia (por ejemplo, un puntero) almacena la dirección de un objeto que se encuentra en otra parte de la memoria. A diferencia de un puntero, una referencia inicializada no puede hacer referencia a otro objeto ni establecerse en null. Hay dos tipos de referencias: referencias lvalue, que hacen referencia a un nombre variable y referencias rvalue, que hacen referencia a un [objeto temporal](../cpp/temporary-objects.md). El operador & significa una referencia lvalue, mientras que el operador && significa una referencia rvalue o una referencia universal (lvalue o rvalue) según el contexto.

Las referencias se pueden declarar con la sintaxis siguiente:

> \[*especificadores de clase de almacenamiento*] \[ *calificadores cv*] *especificadores de tipo* \[ *ms-modifier*]  *declarador* \[ **=** *expresión*]**;**

Se puede usar cualquier declarador válido que especifique una referencia. A menos que la referencia sea una referencia a un tipo de función o matriz, se aplica la siguiente sintaxis simplificada:

> \[*especificadores de clase de almacenamiento*] \[ *calificadores cv*] *especificadores de tipo* \[ **&** o **&&**] \[ *calificadores cv*] *identificador* \[ **=** *expresión*]**;**

Las referencias se declaran mediante la siguiente secuencia:

1. Los especificadores de la declaración:

   - Un especificador de clase de almacenamiento opcional.

   - Opcional **const** o **volátil** calificadores.

   - El especificador de tipo: el nombre de un tipo.

1. El declarador:

   - Un modificador opcional específico de Microsoft. Para obtener más información, consulte [modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md).

   - El **&** operador o **&&** operador.

   - Opcional **const** o **volátil** opcionales.

   - El identificador.

1. Un inicializador opcional.

Las formas de declarador más complejas para punteros a matrices y funciones también se aplican a las referencias a las matrices y funciones. Para obtener más información, consulte [punteros](../cpp/pointers-cpp.md).

Varios declaradores e inicializadores pueden aparecer en una lista separada por comas detrás de un único especificador de declaración. Por ejemplo:

```cpp
int &i;
int &i, &j;
```

Las referencias, punteros y objetos se pueden declarar juntos:

```cpp
int &ref, *ptr, k;
```

Una referencia contiene la dirección de un objeto, pero se comporta sintácticamente como un objeto.

Observe que, en el siguiente programa, el nombre del objeto `s` y la referencia al objeto, `SRef`, se pueden usar de la misma forma:

## <a name="example"></a>Ejemplo

```cpp
// references.cpp
#include <stdio.h>
struct S {
   short i;
};

int main() {
   S  s;   // Declare the object.
   S& SRef = s;   // Declare the reference.
   s.i = 3;

   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);

   SRef.i = 4;
   printf_s("%d\n", s.i);
   printf_s("%d\n", SRef.i);
}
```

```Output
3
3
4
4
```

## <a name="see-also"></a>Vea también

[Argumentos de función de tipo de referencia](../cpp/reference-type-function-arguments.md)<br/>
[Valores devueltos de función de tipo de referencia](../cpp/reference-type-function-returns.md)<br/>
[Referencias a punteros](../cpp/references-to-pointers.md)
