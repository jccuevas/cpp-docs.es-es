---
title: Escribir funciones con ensamblado alineado | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8b2694d2dc5781a6ef521abdc97e98c928be92c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680833"
---
# <a name="writing-functions-with-inline-assembly"></a>Escribir funciones con ensamblado alineado

**Específicos de Microsoft**

Si escribe una función con código de ensamblado alineado, es fácil pasar argumentos a la función y devolver un valor de ella. En los ejemplos siguientes se compara una función escrita primero para un ensamblador independiente y después reescrita para el ensamblador alineado. La función, denominada `power2`, recibe dos parámetros y multiplica el primer parámetro por 2 elevado a la potencia del segundo parámetro. Escrita para un ensamblador independiente, la función podría ser así:

```asm
; POWER.ASM
; Compute the power of an integer
;
       PUBLIC _power2
_TEXT SEGMENT WORD PUBLIC 'CODE'
_power2 PROC

        push ebp        ; Save EBP
        mov ebp, esp    ; Move ESP into EBP so we can refer
                        ;   to arguments on the stack
        mov eax, [ebp+4] ; Get first argument
        mov ecx, [ebp+6] ; Get second argument
        shl eax, cl     ; EAX = EAX * ( 2 ^ CL )
        pop ebp         ; Restore EBP
        ret             ; Return with sum in EAX

_power2 ENDP
_TEXT   ENDS
        END
```

Puesto que se escribió para un ensamblador independiente, la función requiere un archivo de código fuente independiente y pasos de ensamblado y vinculación. Los argumentos de función de C y C++ se pasan normalmente en la pila, por lo que esta versión de la función `power2` obtiene acceso a sus argumentos por sus posiciones en la pila. (Tenga en cuenta que el **modelo** directiva, disponible en MASM y otros ensambladores, también le permite tener acceso a argumentos de la pila y las variables locales de la pila por nombre.)

## <a name="example"></a>Ejemplo

Este programa escribe la función `power2` con código de ensamblado alineado:

```cpp
// Power2_inline_asm.c
// compile with: /EHsc
// processor: x86

#include <stdio.h>

int power2( int num, int power );

int main( void )
{
    printf_s( "3 times 2 to the power of 5 is %d\n", \
              power2( 3, 5) );
}
int power2( int num, int power )
{
   __asm
   {
      mov eax, num    ; Get first argument
      mov ecx, power  ; Get second argument
      shl eax, cl     ; EAX = EAX * ( 2 to the power of CL )
   }
   // Return with result in EAX
}
```

La versión alineada de la función `power2` hace referencia a sus argumentos por nombre y aparece en el mismo archivo de código fuente que el resto del programa. Esta versión también requiere menos instrucciones de ensamblado.

Dado que la versión alineada de `power2` no ejecuta la instrucción de C++ `return`, provoca una advertencia inofensiva si se compila en el nivel de advertencia 2 o más alto. La función devuelve un valor, pero el compilador no lo percibe en ausencia de una instrucción `return`. Puede usar [advertencia #pragma](../../preprocessor/warning.md) para deshabilitar la generación de esta advertencia.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>