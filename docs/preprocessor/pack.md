---
title: módulo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- pack_CPP
- vc-pragma.pack
dev_langs:
- C++
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c29c31cae2b7de59d4db5ed6546ad4eda6baecf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843631"
---
# <a name="pack"></a>pack
Especifica la alineación de empaquetado de los miembros de estructura, unión y clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )  
```  
  
## <a name="remarks"></a>Comentarios  
 Empaquetar una clase consiste en colocar sus miembros uno tras otro en la memoria, lo que puede conllevar que algunos o todos los miembros se alineen en un límite menor que la alineación predeterminada de la arquitectura de destino. `pack` proporciona control en el nivel de declaración de datos. Esto difiere de la opción de compilador [/Zp](../build/reference/zp-struct-member-alignment.md), que solo proporciona control de nivel de módulo. `pack` tiene efecto en la primera declaración `struct`, `union` o `class` después de ver la directiva pragma. `pack` no tiene ningún efecto en las definiciones. Al llamar a `pack` sin argumentos establece `n` en el valor establecido en la opción del compilador **/Zp**. Si no se establece la opción del compilador, el valor predeterminado es 8.  
  
 Si cambia la alineación de una estructura, puede que no use tanto espacio en la memoria, pero es posible que vea una disminución del rendimiento o incluso que obtenga una excepción generada por el hardware debido al acceso no alineado.  Puede modificar este comportamiento de excepción mediante [SetErrorMode](http://msdn.microsoft.com/library/windows/desktop/ms680621).  
  
 **Mostrar** (opcional)  
 Muestra el valor de byte actual para la alineación de empaquetamiento. El valor se muestra mediante un mensaje de advertencia.  
  
 **inserción** (opcional)  
 Inserta el valor de alineación de empaquetado actual en la pila interna del compilador y establece el valor actual de la alineación de empaquetado en `n`. Si no se especifica `n`, se inserta el valor actual de la alineación de empaquetado.  
  
 **confirmación** (opcional)  
 Quita el registro de la parte superior de la pila interna del compilador. Si `n` no se especifica con **pop**, entonces el valor de empaquetado asociado al registro resultante en la parte superior de la pila es el nuevo valor de alineación de empaquetado. Si se especifica `n`, por ejemplo, `#pragma pack(pop, 16)`, `n` se convierte en el nuevo valor de la alineación de empaquetado. Si saca con `identifier`, por ejemplo, `#pragma pack(pop, r1)`, se sacan todos los registros de la pila hasta encontrar el registro que tiene `identifier`. Ese registro se saca y el valor de empaquetado asociado al registro resultante en la parte superior de la pila es el nuevo valor de alineación de empaquetado. Si saca con un `identifier` que no se encuentra en ningún registro en la pila, la **pop** se omite.  
  
 `identifier` (opcional)  
 Cuando se usa con **inserción**, asigna un nombre para el registro en la pila interna del compilador. Cuando se usa con **pop**, extrae registros de la pila interna hasta que `identifier` se quita; si `identifier` no se encuentra en la pila interna, se extrae nada.  
  
 `n` (opcional)  
 Especifica el valor, en bytes, que se usará para el empaquetado. Si la opción del compilador [/Zp](../build/reference/zp-struct-member-alignment.md) no está establecida para el módulo, el valor predeterminado de `n` es 8. Los valores válidos son 1, 2, 4, 8 y 16. La alineación de un miembro estará en un límite que sea un múltiplo de `n` o un múltiplo del tamaño del miembro, lo que sea menor.  
  
 `#pragma pack(pop, identifier, n)` no está definido.  
  
 Para obtener más información acerca de cómo modificar la alineación, vea estos temas:  
  
-   [__alignof](../cpp/alignof-operator.md)  
  
-   [align](../cpp/align-cpp.md)  
  
-   [__unaligned](../cpp/unaligned.md)  
  
-   [Ejemplos de alineación de estructuras](../build/examples-of-structure-alignment.md) (x64 específico)  
  
    > [!WARNING]
    >  Tenga en cuenta que en Visual Studio 2015 y posterior puede usar los operadores estándar alignof y alignas, que, a diferencia de `__alignof` y `declspec( align )`, son portátiles entre compiladores. El estándar de C++ no se ocupa del empaquetado, por lo que deberá usar `pack` (o la extensión que corresponda en otros compiladores) para especificar alineaciones que sean inferiores al tamaño de palabra de la arquitectura de destino.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar la directiva pragma `pack` para cambiar la alineación de una estructura.  
  
```  
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
  
```  
0 4 8  
0 4 6  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo utilizar el **inserción**, **pop**, y **mostrar** sintaxis.  
  
```  
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