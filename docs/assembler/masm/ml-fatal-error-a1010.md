---
title: Error irrecuperable A1010 de ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: b3141f8819a33281c70e34bd7772d4475886e557
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312591"
---
# <a name="ml-fatal-error-a1010"></a>Error irrecuperable A1010 de ML

**anidamiento de bloques sin coincidencia:**

Un bloque que empieza no tenía un extremo correspondiente o un extremo de bloque no tenía un principio coincidente. Uno de los siguientes puede ser implicado:

- Una directiva de alto nivel como [. Si](dot-if.md)es, [. Repita el procedimiento](dot-repeat.md)o [. WHILE](dot-while.md).

- Una directiva de ensamblado condicional como [If](if-masm.md), [REPEAT](repeat.md)o **While**.

- Una definición de estructura o Unión.

- Definición de procedimiento.

- Definición de segmento.

- Una directiva [POPCONTEXT](popcontext.md) .

- Una directiva de ensamblado condicional, como [else](else-masm.md), [ELSEIF](elseif-masm.md)o **endif** sin una coincidencia [If](if-masm.md).

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](ml-error-messages.md)
