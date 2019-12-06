---
title: Error irrecuperable A1011 de ML
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 0d8d3896f7788aa3f51605651ee1b728b0e1d60a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856857"
---
# <a name="ml-fatal-error-a1011"></a>Error irrecuperable A1011 de ML

**la Directiva debe estar en el bloque de control**

El ensamblador encontró una directiva de alto nivel en la que no se esperaba una. Se encontró una de las siguientes directivas:

- [. ELSE](../../assembler/masm/dot-else.md) sin [. Si](../../assembler/masm/dot-if.md) es

- [. ENDIF](../../assembler/masm/dot-endif.md) sin [. Si](../../assembler/masm/dot-if.md) es

- [. ENDW](../../assembler/masm/dot-endw.md) sin [. WHILE](../../assembler/masm/dot-while.md)

- [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md) sin [. REPETIR](../../assembler/masm/dot-repeat.md)

- [. Continúe](../../assembler/masm/dot-continue.md) sin [. WHILE](../../assembler/masm/dot-while.md) o [. REPETIR](../../assembler/masm/dot-repeat.md)

- [. INTERRUMPIr](../../assembler/masm/dot-break.md) sin [. WHILE](../../assembler/masm/dot-while.md) o [. REPETIR](../../assembler/masm/dot-repeat.md)

- [. ](../../assembler/masm/dot-else.md)De lo contrario `.ELSE`

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>