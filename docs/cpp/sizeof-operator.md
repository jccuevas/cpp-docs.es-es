---
title: sizeof (operador) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- sizeof_cpp
dev_langs:
- C++
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6445fb834982cd13348c9e94def4b75fe31c02e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058825"
---
# <a name="sizeof-operator"></a>sizeof (Operador)

Genera el tamaño de su operando con respecto al tamaño del tipo **char**.

> [!NOTE]
>  Para obtener información sobre la `sizeof ...` operador, consulte [puntos suspensivos y plantillas Variádicas](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Sintaxis

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Comentarios

El resultado de la **sizeof** operador es de tipo `size_t`, un tipo entero definido en el archivo de inclusión \<stddef.h >. Este operador permite no tener que especificar tamaños de datos dependientes del equipo en los programas.

El operando situado a **sizeof** puede ser uno de los siguientes:

- Nombre de tipo. Para usar **sizeof** con un nombre de tipo, el nombre debe ir entre paréntesis.

- Una expresión. Cuando se usa con una expresión, **sizeof** se puede especificar con o sin paréntesis. La expresión no se evalúa.

Cuando el **sizeof** operador se aplica a un objeto de tipo **char**, genera 1. Cuando el **sizeof** operador se aplica a una matriz, genera el número total de bytes en dicha matriz, no el tamaño del puntero representado por el identificador de matriz. Para obtener el tamaño del puntero representado por el identificador de matriz, páselo como un parámetro a una función que usa **sizeof**. Por ejemplo:

## <a name="example"></a>Ejemplo

```cpp
#include <iostream>
using namespace std;

size_t getPtrSize( char *ptr )
{
   return sizeof( ptr );
}

int main()
{
   char szHello[] = "Hello, world!";

   cout  << "The size of a char is: "
         << sizeof( char )
         << "\nThe length of " << szHello << " is: "
         << sizeof szHello
         << "\nThe size of the pointer is "
         << getPtrSize( szHello ) << endl;
}
```

## <a name="sample-output"></a>Resultados del ejemplo

```Output
The size of a char is: 1
The length of Hello, world! is: 14
The size of the pointer is 4
```

Cuando el **sizeof** operador se aplica a un **clase**, **struct**, o **unión** tipo, el resultado es el número de bytes de un objeto de ese tipo, además de cualquier relleno agregado a alinear los miembros en los límites de palabra. El resultado no corresponde necesariamente al tamaño que se calcula agregando los requisitos de almacenamiento de los miembros individuales. El [/Zp](../build/reference/zp-struct-member-alignment.md) opción del compilador y el [pack](../preprocessor/pack.md) pragma afectan a los límites de alineación de miembros.

El **sizeof** operador nunca genera 0, incluso para una clase vacía.

El **sizeof** operador no se puede usar con los operandos siguientes:

- Funciones. (Sin embargo, **sizeof** se pueden aplicar a punteros a funciones.)

- Campos de bits.

- Clases no definidas.

- El tipo **void**.

- Matrices asignadas dinámicamente.

- Matrices externas.

- Tipos incompletos.

- Nombres entre paréntesis de tipos incompletos.

Cuando el **sizeof** operador se aplica a una referencia, el resultado es el mismo que si **sizeof** hubiera aplicado el propio objeto.

Si una matriz sin tamaño es el último elemento de una estructura, el **sizeof** operador devuelve el tamaño de la estructura sin la matriz.

El **sizeof** operador a menudo se usa para calcular el número de elementos en una matriz mediante una expresión de formato:

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Vea también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)