---
title: Comentarios en lenguaje de ensamblado
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: a8b2c98c61d58d72e78dbffd4f3b6ed7707d2d7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169609"
---
# <a name="assembly-language-comments"></a>Comentarios en lenguaje de ensamblado

**Específicos de Microsoft**

Las instrucciones en un bloque `__asm` pueden utilizar comentarios en lenguaje de ensamblado:

```cpp
__asm mov ax, offset buff ; Load address of buff
```

Debido a que las macros de C se expanden en una única línea lógica, evite utilizar comentarios en lenguaje de ensamblado en las macros. (Consulte [definición de bloques de __asm como macros de C](../../assembler/inline/defining-asm-blocks-as-c-macros.md)). Un bloque `__asm` también puede contener comentarios de estilo C. para obtener más información, vea [uso de C++ C o en bloques de __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
