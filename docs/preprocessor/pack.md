---
title: pack (pragma)
ms.date: 11/11/2019
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 335289802b6c370158fc655646b710914a07a3f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160338"
---
# <a name="pack-pragma"></a>pack (pragma)

Especifica la alineación de empaquetado para los miembros de estructura, Unión y clase.

## <a name="syntax"></a>Sintaxis

> **#pragma Pack (Mostrar)** \
> **#pragma Pack (Inserte** [ **,** *Identifier* ] [ **,** *n* ] **)** \
> **#pragma Pack (pop** [ **,** { *Identifier* | *n* }] **)** \
> **#pragma Pack (** [ *n* ] **)**

### <a name="parameters"></a>Parámetros

**mostrar**\
Opta Muestra el valor actual de bytes para la alineación de empaquetado. El valor se muestra mediante un mensaje de advertencia.

\ de **extracción**
Opta Envía el valor actual de la alineación de empaquetado en la pila interna del compilador y establece el valor actual de la alineación de empaquetado en *n*. Si no se especifica *n* , se inserta el valor actual de la alineación de empaquetado.

\ **pop**
Opta Quita el registro de la parte superior de la pila interna del compilador. Si no se especifica *n* con **pop**, el valor de empaquetado asociado al registro resultante en la parte superior de la pila es el nuevo valor de alineación de empaquetado. Si se especifica *n* , por ejemplo, `#pragma pack(pop, 16)`, *n* se convierte en el nuevo valor de alineación de empaquetado. Si usa un *identificador*, por ejemplo, `#pragma pack(pop, r1)`, todos los registros de la pila se extraen hasta que se encuentra el registro que tiene el *identificador* . Ese registro se extrae y el valor de empaquetado asociado al registro resultante en la parte superior de la pila es el nuevo valor de alineación de empaquetado. Si se usa un *identificador* que no se encuentra en ningún registro de la pila, se omite el **pop** .

La instrucción `#pragma pack (pop, r1, 2)` es equivalente a `#pragma pack (pop, r1)` seguido de `#pragma pack(2)`.

*identificador*\
Opta Cuando se usa con la **extracción**, asigna un nombre al registro en la pila interna del compilador. Cuando se usa con **pop**, extrae los registros de la pila interna hasta que se quite el *identificador* . Si no se encuentra el *identificador* en la pila interna, no se extrae nada.

*n*\
Opta Especifica el valor, en bytes, que se va a usar para el empaquetado. Si la opción del compilador [/ZP](../build/reference/zp-struct-member-alignment.md) no está establecida para el módulo, el valor predeterminado de *n* es 8. Los valores válidos son 1, 2, 4, 8 y 16. La alineación de un miembro se encuentra en un límite que es un múltiplo de *n*o un múltiplo del tamaño del miembro, lo que sea menor.

## <a name="remarks"></a>Observaciones

Para *empaquetar* una clase, coloque sus miembros directamente entre sí en la memoria. Puede significar que algunos o todos los miembros se pueden alinear en un límite menor que la alineación predeterminada de la arquitectura de destino. **Pack** proporciona el control en el nivel de declaración de datos. Difiere de la opción del compilador [/ZP](../build/reference/zp-struct-member-alignment.md), que solo proporciona control de nivel de módulo. **Pack** surte efecto en la primera declaración de **estructura**, **Unión**o **clase** después de que se vea la Directiva pragma. **Pack** no tiene ningún efecto en las definiciones. El **paquete** de llamada sin argumentos establece *n* en el valor establecido en la opción del compilador `/Zp`. Si la opción del compilador no está establecida, el valor predeterminado es 8.

Si cambia la alineación de una estructura, puede que no use tanto espacio en la memoria, pero es posible que vea una disminución del rendimiento o incluso que obtenga una excepción generada por el hardware debido al acceso no alineado.  Puede modificar este comportamiento de excepción mediante [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode).

Para obtener más información acerca de cómo modificar la alineación, consulte estos artículos:

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [Ejemplos de alineación de estructura](../build/x64-software-conventions.md#examples-of-structure-alignment) (específico de x64)

   > [!WARNING]
   > En Visual Studio 2015 y versiones posteriores, puede usar los operadores **alignas** y **aligna** estándar, que a diferencia de `__alignof` y `declspec( align )` son portátiles entre compiladores. El C++ estándar no aborda el empaquetado, por lo que todavía debe usar **Pack** (o la extensión correspondiente en otros compiladores) para especificar las alineaciones más pequeñas que el tamaño de la palabra de la arquitectura de destino.

## <a name="examples"></a>Ejemplos

En el ejemplo siguiente se muestra cómo usar la pragma **Pack** para cambiar la alineación de una estructura.

```cpp
// pragma_directives_pack.cpp
#include <stddef.h>
#include <stdio.h>

struct S {
   int i;   // size 4
   short j;   // size 2
   double k;   // size 8
};

#pragma pack(2)
struct T {
   int i;
   short j;
   double k;
};

int main() {
   printf("%zu ", offsetof(S, i));
   printf("%zu ", offsetof(S, j));
   printf("%zu\n", offsetof(S, k));

   printf("%zu ", offsetof(T, i));
   printf("%zu ", offsetof(T, j));
   printf("%zu\n", offsetof(T, k));
}
```

```Output
0 4 8
0 4 6
```

En el ejemplo siguiente se muestra cómo usar la sintaxis de las operaciones de *envío*, de *pop*y de *presentación* .

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810

// pop to the identifier and then set
// the value of the current packing alignment:
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>Consulte también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
