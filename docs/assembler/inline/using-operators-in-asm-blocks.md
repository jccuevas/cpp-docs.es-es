---
title: Usar operadores en bloques __asm | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 8731169013cba50e01c36aa721859e136938f015
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676915"
---
# <a name="using-operators-in-asm-blocks"></a>Uso de operadores en bloques __asm

**Específicos de Microsoft**

Un `__asm` bloque no puede usar operadores específicos de C o C++, como la **<<** operador. Sin embargo, operadores compartidos por C y MASM, como el \* operador, se interpretan como operadores de lenguaje de ensamblado. Por ejemplo, fuera de un `__asm` bloquear los corchetes (**[]**) se interpretan como subíndices de matriz, que C ajusta automáticamente el tamaño de un elemento de la matriz de inclusión. Dentro de un bloque `__asm`, se ven como el operador índice de MASM, que produce un desplazamiento de bytes sin ajuste de escala desde cualquier objeto de datos o etiqueta (no solo una matriz). El código siguiente ilustra la diferencia:

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

La primera referencia a `array` no se ajusta a escala, pero la segunda sí. Tenga en cuenta que puede usar el **tipo** operador para conseguir un escalado según una constante. Por ejemplo, las instrucciones siguientes son equivalentes:

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>