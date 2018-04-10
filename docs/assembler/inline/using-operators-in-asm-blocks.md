---
title: Usar operadores en bloques __asm | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca8ac739793c81ef18f8657cbf53c9cb018b3e38
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
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