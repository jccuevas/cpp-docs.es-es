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
ms.openlocfilehash: 2353f0861f0f249416d0bb84a7a951b1cb6d64bc
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857338"
---
# <a name="references-c"></a>Referencias (C++)

Una referencia (por ejemplo, un puntero) almacena la dirección de un objeto que se encuentra en otra parte de la memoria. A diferencia de un puntero, una referencia inicializada no puede hacer referencia a otro objeto ni establecerse en null. Hay dos tipos de referencias: referencias de valor l que hacen referencia a una variable con nombre y referencias rvalue que hacen referencia a un [objeto temporal](../cpp/temporary-objects.md). El operador & denota una referencia lvalue y el operador & & indica una referencia rvalue o una referencia universal (rvalue o lvalue) dependiendo del contexto.

Las referencias se pueden declarar con la sintaxis siguiente:

> \[Type- *Class-Specifier*] \[*CV-calificadores*] *tipo-especificadores* \[*MS-modifier*] *declarador* \[ **=** *expresión*] **;**

Se puede usar cualquier declarador válido que especifique una referencia. A menos que la referencia sea una referencia a un tipo de función o matriz, se aplica la siguiente sintaxis simplificada:

> \[s-especificadores de *clase de almacenamiento*] \[de los *calificadores CV*] *de tipo-especificadores* \[ **&** o **&&** ] \[*de los calificadores CV*] *identificador* \[ **=** *expresión*] **;**

Las referencias se declaran mediante la siguiente secuencia:

1. Los especificadores de la declaración:

   - Un especificador de clase de almacenamiento opcional.

   - Calificadores **const** y/o **volatile** opcionales.

   - El especificador de tipo: el nombre de un tipo.

1. El declarador:

   - Modificador opcional concreto de Microsoft. Para obtener más información, vea [Modificadores específicos de Microsoft](../cpp/microsoft-specific-modifiers.md).

   - Operador de **&** o operador de **&&** .

   - Opcionales **const** y/o **volatile** opcional.

   - El identificador.

1. Un inicializador opcional.

Las formas de declarador más complejas para punteros a matrices y funciones también se aplican a las referencias a las matrices y funciones. Para obtener más información, vea [punteros](../cpp/pointers-cpp.md).

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
