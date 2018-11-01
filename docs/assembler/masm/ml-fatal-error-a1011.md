---
title: Error irrecuperable A1011 de ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 591755a1d7066d8251f61d2a22b9601a9ccb9dcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520203"
---
# <a name="ml-fatal-error-a1011"></a>Error irrecuperable A1011 de ML

**Directiva debe estar en el bloque de control**

El ensamblador encontró una directiva de alto nivel donde no se esperaba. Se encontró una de las siguientes directivas:

- [. ELSE](../../assembler/masm/dot-else.md) sin [. IF](../../assembler/masm/dot-if.md)

- [. ENDIF](../../assembler/masm/dot-endif.md) sin [. IF](../../assembler/masm/dot-if.md)

- [. ENDW](../../assembler/masm/dot-endw.md) sin [. WHILE](../../assembler/masm/dot-while.md)

- [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md) sin [. REPITA](../../assembler/masm/dot-repeat.md)

- [. CONTINUAR](../../assembler/masm/dot-continue.md) sin [. MIENTRAS](../../assembler/masm/dot-while.md) o [. REPITA](../../assembler/masm/dot-repeat.md)

- [. INTERRUMPIR](../../assembler/masm/dot-break.md) sin [. MIENTRAS](../../assembler/masm/dot-while.md) o [. REPITA](../../assembler/masm/dot-repeat.md)

- [. ELSE](../../assembler/masm/dot-else.md) siguiente `.ELSE`

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>