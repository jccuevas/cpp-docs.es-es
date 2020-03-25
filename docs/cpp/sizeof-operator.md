---
title: sizeof (Operador)
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: bc1165cf1df3933575013906d1b24673467f0b36
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178722"
---
# <a name="sizeof-operator"></a>sizeof (Operador)

Da como resultado el tamaño de su operando con respecto al tamaño del tipo **Char**.

> [!NOTE]
>  Para obtener información sobre el operador `sizeof ...`, consulte [las plantillas Ellipse y variádicas](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Sintaxis

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Observaciones

El resultado del operador **sizeof** es de tipo `size_t`, un tipo entero definido en el archivo de inclusión \<stddef. h >. Este operador permite no tener que especificar tamaños de datos dependientes del equipo en los programas.

El operando de **sizeof** puede ser uno de los siguientes:

- Nombre de tipo. Para usar **sizeof** con un nombre de tipo, el nombre debe ir entre paréntesis.

- Expresión. Cuando se utiliza con una expresión, **sizeof** se puede especificar con o sin paréntesis. La expresión no se evalúa.

Cuando el operador **sizeof** se aplica a un objeto de tipo **Char**, produce 1. Cuando se aplica el operador **sizeof** a una matriz, se produce el número total de bytes de esa matriz, no el tamaño del puntero representado por el identificador de matriz. Para obtener el tamaño del puntero representado por el identificador de matriz, páselo como parámetro a una función que utiliza **sizeof**. Por ejemplo:

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

## <a name="sample-output"></a>Salida de ejemplo

```Output
The size of a char is: 1
The length of Hello, world! is: 14
The size of the pointer is 4
```

Cuando el operador **sizeof** se aplica a un tipo **Class**, **struct**o **Union** , el resultado es el número de bytes de un objeto de ese tipo, además del relleno agregado para alinear los miembros en los límites de palabras. El resultado no corresponde necesariamente al tamaño que se calcula agregando los requisitos de almacenamiento de los miembros individuales. La opción del compilador [/ZP](../build/reference/zp-struct-member-alignment.md) y el pragma [Pack](../preprocessor/pack.md) afectan a los límites de alineación de los miembros.

El operador **sizeof** nunca produce 0, ni siquiera para una clase vacía.

El operador **sizeof** no se puede usar con los siguientes operandos:

- Funciones. (Sin embargo, **sizeof** se puede aplicar a punteros a funciones).

- Campos de bits.

- Clases no definidas.

- Tipo **void**.

- Matrices asignadas dinámicamente.

- Matrices externas.

- Tipos incompletos.

- Nombres entre paréntesis de tipos incompletos.

Cuando el operador **sizeof** se aplica a una referencia, el resultado es el mismo que si se hubiera aplicado **sizeof** al propio objeto.

Si una matriz sin tamaño es el último elemento de una estructura, el operador **sizeof** devuelve el tamaño de la estructura sin la matriz.

El operador **sizeof** se usa a menudo para calcular el número de elementos de una matriz mediante una expresión con el formato:

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Consulte también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
