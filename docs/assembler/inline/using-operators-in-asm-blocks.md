---
title: Uso de operadores en bloques __asm
ms.date: 08/30/2018
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
ms.openlocfilehash: b6ac9f7174baf1e0ebe41181c6a6f43e7bb3f5d1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169102"
---
# <a name="using-operators-in-__asm-blocks"></a>Uso de operadores en bloques __asm

**Específicos de Microsoft**

Un bloque `__asm` no puede usar C C++ ni operadores específicos, como el operador **<<** . Sin embargo, los operadores compartidos por C y MASM, como el operador \*, se interpretan como operadores de lenguaje de ensamblado. Por ejemplo, fuera de un bloque `__asm`, los corchetes ( **[]** ) se interpretan como subíndices de matriz envolventes, lo que C escala automáticamente al tamaño de un elemento de la matriz. Dentro de un bloque `__asm`, se ven como el operador índice de MASM, que produce un desplazamiento de bytes sin ajuste de escala desde cualquier objeto de datos o etiqueta (no solo una matriz). El código siguiente ilustra la diferencia:

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

La primera referencia a `array` no se ajusta a escala, pero la segunda sí. Tenga en cuenta que puede utilizar el operador **Type** para lograr el escalado basado en una constante. Por ejemplo, las siguientes instrucciones son equivalentes:

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
