---
title: Error irrecuperable A1010 de ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: eb4d77b856e93a8d64ee6c51bec63ceae59b22e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449132"
---
# <a name="ml-fatal-error-a1010"></a>Error irrecuperable A1010 de ML

**anidamiento de bloques no coincidentes:**

Un principio del bloque no tenía un end correspondiente, o un final del bloque no tenía un principio coincidente. Uno de los siguientes puede estar implicado:

- Una directiva de alto nivel como [. IF](../../assembler/masm/dot-if.md), [. Repita](../../assembler/masm/dot-repeat.md), o [. MIENTRAS](../../assembler/masm/dot-while.md).

- Una directiva condicional de ensamblado como [IF](../../assembler/masm/if-masm.md), [repita](../../assembler/masm/repeat.md), o **mientras**.

- Una definición de estructura o unión.

- Una definición de procedimiento.

- Una definición de segmento.

- Un [POPCONTEXT](../../assembler/masm/popcontext.md) directiva.

- Un ensamblado de condicional de la directiva, como un [ELSE](../../assembler/masm/else-masm.md), [ELSEIF](../../assembler/masm/elseif-masm.md), o **ENDIF** sin coincidencia [IF](../../assembler/masm/if-masm.md).

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>