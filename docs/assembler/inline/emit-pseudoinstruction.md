---
title: _emit (Pseudoinstrucción)
ms.date: 08/30/2018
f1_keywords:
- _emit
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
ms.openlocfilehash: f2a7c9c4dab97bc1aba3147b5d75f6abbdac951f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167171"
---
# <a name="emit-pseudoinstruction"></a>_emit (Pseudoinstrucción)

**Específicos de Microsoft**

El **_emit** pseudoinstrucción define un byte en la ubicación actual en el segmento de texto actual. El **_emit** pseudoinstrucción es similar a la [DB](../../assembler/masm/db.md) la directiva de MASM.

El fragmento siguiente coloca los bytes 0x4A, 0x43 y 0x4B en el código:

```cpp
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B
.
.
.
__asm {
    randasm
    }
```

> [!CAUTION]
> Si `_emit` genera instrucciones que modifican los registros y se compila la aplicación con optimizaciones, el compilador no puede determinar qué registros se ven afectados. Por ejemplo, si `_emit` genera una instrucción que modifica la **rax** register, el compilador no sabe que **rax** ha cambiado. y podría suponer incorrectamente el valor de ese registro después de la ejecución del código ensamblador alineado. Por consiguiente, la aplicación podría tener un comportamiento impredecible al ejecutarse.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>