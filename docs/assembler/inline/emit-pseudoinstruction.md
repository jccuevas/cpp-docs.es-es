---
title: _emit (pseudoinstrucción) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- _emit
dev_langs:
- C++
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 569e3a078109e66df7dcf5cbf314817ce0786899
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061931"
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