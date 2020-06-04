---
title: _emit (Pseudoinstrucción)
ms.date: 08/30/2018
f1_keywords:
- _emit
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
ms.openlocfilehash: 8be250aadf20dc4a7dee6a0b565ece21840339d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169479"
---
# <a name="_emit-pseudoinstruction"></a>_emit (Pseudoinstrucción)

**Específicos de Microsoft**

El **_emit** Emit (define un byte en la ubicación actual del segmento de texto actual. El **_emit** Emit (se asemeja a la directiva [dB](../../assembler/masm/db.md) de MASM.

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
> Si `_emit` genera instrucciones que modifican los registros y se compila la aplicación con optimizaciones, el compilador no puede determinar qué registros se ven afectados. Por ejemplo, si `_emit` genera una instrucción que modifica el registro **Rax** , el compilador no sabe que **Rax** ha cambiado. y podría suponer incorrectamente el valor de ese registro después de la ejecución del código ensamblador alineado. Por consiguiente, la aplicación podría tener un comportamiento impredecible al ejecutarse.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
