---
title: Error irrecuperable A1010 de ML
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: 6ec82f7f6d559d977a9aa039ed91689a0ef4d49a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856883"
---
# <a name="ml-fatal-error-a1010"></a>Error irrecuperable A1010 de ML

**anidamiento de bloques sin coincidencia:**

Un bloque que empieza no tenía un extremo correspondiente o un extremo de bloque no tenía un principio coincidente. Uno de los siguientes puede ser implicado:

- Una directiva de alto nivel como [. Si](../../assembler/masm/dot-if.md)es, [. Repita el procedimiento](../../assembler/masm/dot-repeat.md)o [. WHILE](../../assembler/masm/dot-while.md).

- Una directiva de ensamblado condicional como [If](../../assembler/masm/if-masm.md), [REPEAT](../../assembler/masm/repeat.md)o **While**.

- Una definición de estructura o Unión.

- Definición de procedimiento.

- Definición de segmento.

- Una directiva [POPCONTEXT](../../assembler/masm/popcontext.md) .

- Una directiva de ensamblado condicional, como [else](../../assembler/masm/else-masm.md), [ELSEIF](../../assembler/masm/elseif-masm.md)o **endif** sin una coincidencia [If](../../assembler/masm/if-masm.md).

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>