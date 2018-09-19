---
title: Error irrecuperable A1010 de ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1010
dev_langs:
- C++
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12b7e8698951e8ef59e0433134ec992af5d5f77f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676302"
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