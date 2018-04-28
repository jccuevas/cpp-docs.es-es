---
title: Usar operadores en bloques __asm | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e1c7c4b8415655aff36327db9c6a9f866d82683
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="using-operators-in-asm-blocks"></a>Uso de operadores en bloques __asm
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Un `__asm` bloque no puede utilizar operadores específicos de C o C++, como la **<<** operador. Sin embargo, operadores compartidos por C y MASM, como el \* (operador), se interpretan como operadores de lenguaje de ensamblado. Por ejemplo, fuera de un `__asm` bloquear, corchetes (**[]**) se interpretan como envolvente subíndices de matriz, que C ajusta automáticamente el tamaño de un elemento de la matriz. Dentro de un bloque `__asm`, se ven como el operador índice de MASM, que produce un desplazamiento de bytes sin ajuste de escala desde cualquier objeto de datos o etiqueta (no solo una matriz). El código siguiente ilustra la diferencia:  
  
```  
int array[10];  
  
__asm mov array[6], bx ;  Store BX at array+6 (not scaled)  
  
array[6] = 0;         /* Store 0 at array+24 (scaled) */  
```  
  
 La primera referencia a `array` no se ajusta a escala, pero la segunda sí. Tenga en cuenta que puede usar el **tipo** operador para lograr el ajuste de escala basándose en una constante. Por ejemplo, las instrucciones siguientes son equivalentes:  
  
```  
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24  
  
array[6] = 0;                   /* Store 0 at array + 24 */  
```  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)