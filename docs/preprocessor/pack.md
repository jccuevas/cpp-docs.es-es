---
title: pack
ms.date: 12/17/2018
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: bf1ae81184d53dd271f63c26e8f9a52a6410b232
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038452"
---
# <a name="pack"></a>pack
Especifica la alineación de empaquetado de los miembros de estructura, unión y clase.

## <a name="syntax"></a>Sintaxis

```
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )
```

### <a name="parameters"></a>Parámetros

**show**<br/>
(Opcional) Muestra el valor de byte actual para la alineación de empaquetado. El valor se muestra mediante un mensaje de advertencia.

**push**<br/>
(Opcional) Valor de la alineación de empaquetado actual de inserciones en la pila interna del compilador y establece la alineación de empaquetado actual valor en *n*. Si *n* no se especifica, el actual se inserta el valor de alineación de empaquetado.

**pop**<br/>
(Opcional) Quita el registro de la parte superior de la pila interna del compilador. Si *n* no se especifica con **pop**, entonces el valor de empaquetado asociado al registro resultante en la parte superior de la pila es el nuevo valor de alineación de empaquetado. Si *n* se especifica, por ejemplo, `#pragma pack(pop, 16)`, *n* se convierte en el nuevo valor de alineación de empaquetado. Si saca con *identificador*, por ejemplo, `#pragma pack(pop, r1)`, a continuación, se extraen todos los registros de la pila hasta que el registro que tiene *identificador* se encuentra. Ese registro se saca y el valor de empaquetado asociado al registro resultante en la parte superior de la pila es el nuevo valor de alineación de empaquetado. Si saca con un *identificador* que no se encuentra en cualquier registro en la pila, el **pop** se omite.

*identifier*<br/>
(Opcional) Cuando se usa con *inserción*, asigna un nombre para el registro en la pila interna del compilador. Cuando se usa con **pop**, extrae los registros de la pila interna hasta *identificador* se quita; si *identificador* no se encuentra en la pila interna, no se extrae nada.

*n*<br/>
(Opcional) Especifica el valor, en bytes, que se usará para el empaquetado. Si la opción del compilador [/Zp](../build/reference/zp-struct-member-alignment.md) no está establecida para el módulo, el valor predeterminado de *n* es 8. Los valores válidos son 1, 2, 4, 8 y 16. La alineación de un miembro estará en un límite que sea un múltiplo de *n* ni un múltiplo del tamaño del miembro, lo que sea menor.

`#pragma pack(pop, identifier, n)` no está definido.

## <a name="remarks"></a>Comentarios

Empaquetar una clase consiste en colocar sus miembros uno tras otro en la memoria, lo que puede conllevar que algunos o todos los miembros se alineen en un límite menor que la alineación predeterminada de la arquitectura de destino. **módulo** ofrece un control en el nivel de declaración de datos. Esto difiere de la opción del compilador [/Zp](../build/reference/zp-struct-member-alignment.md), que solo proporciona control de nivel de módulo. **módulo** surte efecto en la primera **struct**, **unión**, o **clase** declaración después de la pragma. **módulo** no tiene ningún efecto en las definiciones. Una llamada a **pack** sin argumentos establece *n* en el valor establecido en la opción del compilador `/Zp`. Si no se establece la opción del compilador, el valor predeterminado es 8.

Si cambia la alineación de una estructura, puede que no use tanto espacio en la memoria, pero es posible que vea una disminución del rendimiento o incluso que obtenga una excepción generada por el hardware debido al acceso no alineado.  Puede modificar este comportamiento de excepción mediante [SetErrorMode](https://msdn.microsoft.com/library/windows/desktop/ms680621).

Para obtener más información acerca de cómo modificar la alineación, vea estos temas:

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [Ejemplos de alineación de estructuras](../build/x64-software-conventions.md#examples-of-structure-alignment) (x64 específico)

   > [!WARNING]
   > Tenga en cuenta que en Visual Studio 2015 y posterior puede usar los operadores estándar alignof y alignas, que, a diferencia de `__alignof` y `declspec( align )`, son portátiles entre compiladores. El estándar de C++ no se ocupa del empaquetado, por lo que deberá seguir usando **pack** (o la extensión que corresponda en otros compiladores) para especificar alineaciones que sean inferiores al tamaño de palabra de la arquitectura de destino.

## <a name="examples"></a>Ejemplos

El ejemplo siguiente muestra cómo usar el **pack** pragma para cambiar la alineación de una estructura.

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

El ejemplo siguiente muestra cómo usar el *inserción*, *pop*, y *mostrar* sintaxis.

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>Vea también

[Directives pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)