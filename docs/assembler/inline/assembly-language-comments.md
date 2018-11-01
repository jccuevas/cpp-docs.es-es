---
title: Comentarios en lenguaje de ensamblado
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: fc37658eccd99b61d45aa9a9a7a2675ef90eee89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578651"
---
# <a name="assembly-language-comments"></a>Comentarios en lenguaje de ensamblado

**Específicos de Microsoft**

Las instrucciones en un bloque `__asm` pueden utilizar comentarios en lenguaje de ensamblado:

```cpp
__asm mov ax, offset buff ; Load address of buff
```

Debido a que las macros de C se expanden en una única línea lógica, evite utilizar comentarios en lenguaje de ensamblado en las macros. (Consulte [definir bloques __asm como Macros de C](../../assembler/inline/defining-asm-blocks-as-c-macros.md).) Un `__asm` bloque también puede contener comentarios del estilo de C; para obtener más información, consulte [uso de C o C++ en bloques __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>