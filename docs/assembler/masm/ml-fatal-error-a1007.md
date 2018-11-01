---
title: Error irrecuperable A1007 de ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: 98933c3a24da22f447174a3b51c4855690aba83e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603403"
---
# <a name="ml-fatal-error-a1007"></a>Error irrecuperable A1007 de ML

**nivel de anidamiento demasiado profundo**

El ensamblador alcanzó su límite de anidamiento. El límite es de 20 niveles excepto donde se indique lo contrario.

Uno de estos procedimientos se están demasiado anidado:

- Una directiva de alto nivel como [. IF](../../assembler/masm/dot-if.md), [. Repita](../../assembler/masm/dot-repeat.md), o [. MIENTRAS](../../assembler/masm/dot-while.md).

- Una definición de estructura.

- Una directiva condicional de ensamblado.

- Una definición de procedimiento.

- Un [PUSHCONTEXT](../../assembler/masm/pushcontext.md) directiva (el límite son 10).

- Una definición de segmento.

- Un archivo de inclusión.

- Una macro.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>