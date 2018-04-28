---
title: Error irrecuperable A1010 de ML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: b622595b6994c4c4eaa74ed8f824f28dffe89b1a
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="ml-fatal-error-a1010"></a>Error irrecuperable A1010 de ML
**anidamiento de bloques no coincidentes:**  
  
 Un principio del bloque no tenía un end coincidente, o un final del bloque no tenía un principio coincidente. Puede estar implicado uno de los siguientes:  
  
-   Una directiva de alto nivel, como [. IF](../../assembler/masm/dot-if.md), [. Repita](../../assembler/masm/dot-repeat.md), o [. MIENTRAS](../../assembler/masm/dot-while.md).  
  
-   Una directiva condicional ensamblado como [IF](../../assembler/masm/if-masm.md), [repita](../../assembler/masm/repeat.md), o **mientras**.  
  
-   Una definición de estructura o unión.  
  
-   Una definición de procedimiento.  
  
-   Una definición de segmento.  
  
-   A [POPCONTEXT](../../assembler/masm/popcontext.md) directiva.  
  
-   Un ensamblado de condicional directivas, como un [ELSE](../../assembler/masm/else-masm.md), [ELSEIF](../../assembler/masm/elseif-masm.md), o **ENDIF** sin su correspondiente [IF](../../assembler/masm/if-masm.md).  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)