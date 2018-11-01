---
title: Salto a etiquetas en un ensamblado alineado
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
ms.openlocfilehash: 7653dc990e2f4b490bcbe333ed6f7586ac966d2e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616236"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>Salto a etiquetas en un ensamblado alineado

**Específicos de Microsoft**

Como una etiqueta normal de C o C++, una etiqueta en un bloque `__asm` tiene su ámbito en toda la función en la que se define (no solo en el bloque). Las instrucciones de ensamblado y las instrucciones `goto` pueden saltar a las etiquetas dentro o fuera del bloque `__asm`.

Las etiquetas definidas en los bloques `__asm` no distinguen entre mayúsculas y minúsculas; las instrucciones `goto` e instrucciones de ensamblado pueden hacer referencia a esas etiquetas sin tener en cuenta el uso de mayúsculas y minúsculas. Las etiquetas de C y C++ distinguen entre mayúsculas y minúsculas cuando se utilizan en las instrucciones `goto`. Las instrucciones de ensamblado pueden saltar a una etiqueta de C o C++ sin tener en cuenta el uso de mayúsculas y minúsculas.

El código siguiente muestra todas las permutaciones:

```cpp
void func( void )
{
   goto C_Dest;  /* Legal: correct case   */
   goto c_dest;  /* Error: incorrect case */

   goto A_Dest;  /* Legal: correct case   */
   goto a_dest;  /* Legal: incorrect case */

   __asm
   {
      jmp C_Dest ; Legal: correct case
      jmp c_dest ; Legal: incorrect case

      jmp A_Dest ; Legal: correct case
      jmp a_dest ; Legal: incorrect case

      a_dest:    ; __asm label
   }

   C_Dest:       /* C label */
   return;
}
int main()
{
}
```

No utilice nombres de función de biblioteca de C como etiquetas en los bloques `__asm`. Por ejemplo, podría verse tentado a utilizar `exit` como etiqueta, como sigue:

```cpp
; BAD TECHNIQUE: using library function name as label
   jne exit
   .
   .
   .
exit:
   ; More __asm code follows
```

Dado que **salir** es el nombre de una función de biblioteca de C, este código podría producir un salto a la **salir** función en lugar de a la ubicación deseada.

Como sucede en los programas MASM, el símbolo de dólar (`$`) sirve de contador para la ubicación actual. Es una etiqueta para la instrucción que se ensambla actualmente. En los bloques `__asm`, su uso principal es crear saltos condicionales largos:

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>