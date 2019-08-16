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
ms.openlocfilehash: da4484ec86d39c8fa55a741eadd53a1d614b20dc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510179"
---
# <a name="pack"></a>pack
Especifica la alineación de empaquetado de los miembros de estructura, unión y clase.

## <a name="syntax"></a>Sintaxis

```
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )
```

### <a name="parameters"></a>Parámetros

**Feria**<br/>
Opta Muestra el valor actual de bytes para la alineación de empaquetado. El valor se muestra mediante un mensaje de advertencia.

**push**<br/>
Opta Envía el valor actual de la alineación de empaquetado en la pila interna del compilador y establece el valor actual de la alineación de empaquetado en *n*. Si no se especifica *n* , se inserta el valor actual de la alineación de empaquetado.

**pop**<br/>
Opta Quita el registro de la parte superior de la pila interna del compilador. Si no se especifica *n* con **pop**, el valor de empaquetado asociado al registro resultante en la parte superior de la pila es el nuevo valor de alineación de empaquetado. Si se especifica *n* , por ejemplo, `#pragma pack(pop, 16)` *n* se convierte en el nuevo valor de alineación de empaquetado. Si extrae el *identificador*, por ejemplo `#pragma pack(pop, r1)`,, todos los registros de la pila se extraerán hasta que se encuentre el registro con el *identificador* . Ese registro se saca y el valor de empaquetado asociado al registro resultante en la parte superior de la pila es el nuevo valor de alineación de empaquetado. Si extrae con un *identificador* que no se encuentra en ningún registro de la pila, se omite el **pop** .

*identifier*<br/>
Opta Cuando se usa con la *extracción*, asigna un nombre al registro en la pila interna del compilador. Cuando se usa con **pop**, extrae los registros de la pila interna hasta que se quita el *identificador* ; Si no se encuentra el *identificador* en la pila interna, no se extrae nada.

*n*<br/>
Opta Especifica el valor, en bytes, que se va a usar para el empaquetado. Si la opción del compilador [/ZP](../build/reference/zp-struct-member-alignment.md) no está establecida para el módulo, el valor predeterminado de *n* es 8. Los valores válidos son 1, 2, 4, 8 y 16. La alineación de un miembro estará en un límite que sea un múltiplo de *n* o un múltiplo del tamaño del miembro, lo que sea menor.

`#pragma pack(pop, identifier, n)`no está definido.

## <a name="remarks"></a>Comentarios

Empaquetar una clase consiste en colocar sus miembros uno tras otro en la memoria, lo que puede conllevar que algunos o todos los miembros se alineen en un límite menor que la alineación predeterminada de la arquitectura de destino. **Pack** proporciona el control en el nivel de declaración de datos. Esto difiere de la opción del compilador [/ZP](../build/reference/zp-struct-member-alignment.md), que solo proporciona control de nivel de módulo. **Pack** surte efecto en la primera declaración de **estructura**, **Unión**o **clase** después de que se vea la Directiva pragma. **Pack** no tiene ningún efecto en las definiciones. El **paquete** de llamada sin argumentos establece *n* en el valor establecido en la opción `/Zp`del compilador. Si no se establece la opción del compilador, el valor predeterminado es 8.

Si cambia la alineación de una estructura, puede que no use tanto espacio en la memoria, pero es posible que vea una disminución del rendimiento o incluso que obtenga una excepción generada por el hardware debido al acceso no alineado.  Puede modificar este comportamiento de excepción mediante [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode).

Para obtener más información acerca de cómo modificar la alineación, vea estos temas:

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [Ejemplos de alineación de estructura](../build/x64-software-conventions.md#examples-of-structure-alignment) (específico de x64)

   > [!WARNING]
   > Tenga en cuenta que en Visual Studio 2015 y posterior puede usar los operadores estándar alignof y alignas, que, a diferencia de `__alignof` y `declspec( align )`, son portátiles entre compiladores. El C++ estándar no trata el empaquetado, por lo que todavía debe usar **Pack** (o la extensión correspondiente en otros compiladores) para especificar las alineaciones más pequeñas que el tamaño de la palabra de la arquitectura de destino.

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
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)