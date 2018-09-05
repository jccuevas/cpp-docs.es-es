---
title: Error irrecuperable A1011 de ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1011
dev_langs:
- C++
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32949773b869d189516a381ca7df941760a1e4e4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690813"
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