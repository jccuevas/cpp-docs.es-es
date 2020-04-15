---
title: sizeof (Operador)
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: 8789bb5e0e363458edffa7207ea1e138aae4d284
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365570"
---
# <a name="sizeof-operator"></a>sizeof (Operador)

Produce el tamaño de su operando con respecto al tamaño de tipo **char**.

> [!NOTE]
> Para obtener `sizeof ...` información sobre el operador, vea [Elipses y plantillas variádicas](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Sintaxis

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Observaciones

El resultado del operador **sizeof** es de tipo `size_t`, \<un tipo entero definido en el archivo de inclusión stddef.h>. Este operador permite no tener que especificar tamaños de datos dependientes del equipo en los programas.

El operando a **sizeof** puede ser uno de los siguientes:

- Nombre de tipo. Para utilizar **sizeof** con un nombre de tipo, el nombre debe estar entre paréntesis.

- Expresión. Cuando se utiliza con una expresión, **sizeof** se puede especificar con o sin paréntesis. La expresión no se evalúa.

Cuando el operador **sizeof** se aplica a un objeto de tipo **char**, produce 1. Cuando el operador **sizeof** se aplica a una matriz, produce el número total de bytes de esa matriz, no el tamaño del puntero representado por el identificador de matriz. Para obtener el tamaño del puntero representado por el identificador de matriz, páselo como parámetro a una función que utilice **sizeof**. Por ejemplo:

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

Cuando el operador **sizeof** se aplica a un tipo **de clase**, **struct**o **union,** el resultado es el número de bytes en un objeto de ese tipo, además de cualquier relleno agregado para alinear miembros en límites de palabras. El resultado no corresponde necesariamente al tamaño que se calcula agregando los requisitos de almacenamiento de los miembros individuales. La opción del compilador [/Zp](../build/reference/zp-struct-member-alignment.md) y el pragma [pack](../preprocessor/pack.md) afectan a los límites de alineación de los miembros.

El operador **sizeof** nunca produce 0, incluso para una clase vacía.

El operador **sizeof** no se puede utilizar con los siguientes operandos:

- Funciones. (Sin embargo, **sizeof** se puede aplicar a punteros a funciones.)

- Campos de bits.

- Clases no definidas.

- El tipo **void**.

- Matrices asignadas dinámicamente.

- Matrices externas.

- Tipos incompletos.

- Nombres entre paréntesis de tipos incompletos.

Cuando el operador **sizeof** se aplica a una referencia, el resultado es el mismo que si **sizeof** se hubiera aplicado al propio objeto.

Si una matriz sin tamaño es el último elemento de una estructura, el operador **sizeof** devuelve el tamaño de la estructura sin la matriz.

El operador **sizeof** se utiliza a menudo para calcular el número de elementos de una matriz utilizando una expresión del formulario:

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Consulte también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
