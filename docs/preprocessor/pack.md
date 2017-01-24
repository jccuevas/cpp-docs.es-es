---
title: "pack | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pack_CPP"
  - "vc-pragma.pack"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "pack (pragma)"
  - "pragma (directivas), pack"
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pack
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica la alineación de empaquetado de los miembros de estructura, unión y clase.  
  
## Sintaxis  
  
```  
  
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )  
```  
  
## Comentarios  
 Empaquetar una clase consiste en colocar sus miembros uno tras otro en la memoria, lo que puede conllevar que algunos o todos los miembros se alineen en un límite menor que la alineación predeterminada de la arquitectura de destino.  `pack` proporciona control en el nivel de declaración de datos.  Esto difiere de la opción del compilador [\/Zp](../build/reference/zp-struct-member-alignment.md), que solo proporciona control en el nivel de módulo.  `pack` tiene efecto en la primera declaración `struct`, `union` o `class` después de ver la directiva pragma.  `pack` no tiene ningún efecto en las definiciones.  La llamada a `pack` sin argumentos establece `n` en el valor establecido en la opción del compilador **\/Zp**.  Si no se establece la opción del compilador, el valor predeterminado es 8.  
  
 Si cambia la alineación de una estructura, puede que no use tanto espacio en la memoria, pero es posible que vea una disminución del rendimiento o incluso que obtenga una excepción generada por el hardware debido al acceso no alineado.  Puede modificar este comportamiento de excepción mediante [SetErrorMode](http://msdn.microsoft.com/library/windows/desktop/ms680621).  
  
 **show** \(opcional\)  
 Muestra el valor de byte actual para la alineación de empaquetamiento.  El valor se muestra mediante un mensaje de advertencia.  
  
 **push** \(opcional\)  
 Inserta el valor de alineación de empaquetado actual en la pila interna del compilador y establece el valor actual de la alineación de empaquetado en `n`.  Si no se especifica `n`, se inserta el valor actual de la alineación de empaquetado.  
  
 **pop** \(opcional\)  
 Quita el registro de la parte superior de la pila interna del compilador.  Si no se especifica `n` con **pop**, el valor de empaquetado asociado al registro resultante en la parte superior de la pila es el nuevo valor de la alineación de empaquetado.  Si se especifica `n`, por ejemplo, `#pragma pack(pop, 16)`, `n` se convierte en el nuevo valor de la alineación de empaquetado.  Si saca con `identifier`, por ejemplo, `#pragma pack(pop, r1)`, se sacan todos los registros de la pila hasta encontrar el registro que tiene `identifier`.  Ese registro se saca y el valor de empaquetado asociado al registro resultante en la parte superior de la pila es el nuevo valor de alineación de empaquetado.  Si saca con un `identifier` que no se encuentre en ningún registro de la pila, **pop** se omite.  
  
 `identifier` \(opcional\)  
 Cuando se usa con **push**, asigna un nombre al registro en la pila interna del compilador.  Cuando se usa con **pop**, extrae los registros de la pila interna hasta que se quita el `identifier`; si no se encuentra el `identifier` en la pila interna, no se extrae nada.  
  
 `n` \(opcional\)  
 Especifica el valor, en bytes, que se usará para el empaquetado.  Si no se establece la opción del compilador [\/Zp](../build/reference/zp-struct-member-alignment.md) para el módulo, el valor predeterminado de `n` es 8.  Los valores válidos son 1, 2, 4, 8 y 16.  La alineación de un miembro estará en un límite que sea un múltiplo de `n` o un múltiplo del tamaño del miembro, lo que sea menor.  
  
 `#pragma pack(pop,` `identifier``,` `n``)` está sin definir.  
  
 Para obtener más información acerca de cómo modificar la alineación, vea estos temas:  
  
-   [\_\_alignof](../cpp/alignof-operator.md)  
  
-   [align](../cpp/align-cpp.md)  
  
-   [\_\_unaligned](../cpp/unaligned.md)  
  
-   [Ejemplos de alineación de estructuras](../build/examples-of-structure-alignment.md) \(específico de x64\)  
  
    > [!WARNING]
    >  Tenga en cuenta que en Visual Studio 2015 y posterior puede usar los operadores estándar alignof y alignas, que, a diferencia de `__alignof` y `declspec( align )`, son portátiles entre compiladores.  El estándar de C\+\+ no se ocupa del empaquetado, por lo que deberá usar `pack` \(o la extensión que corresponda en otros compiladores\) para especificar alineaciones que sean inferiores al tamaño de palabra de la arquitectura de destino.  
  
## Ejemplo  
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
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo usar la sintaxis **push**, **pop** y **show**.  
  
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
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)