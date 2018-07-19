---
title: Error irrecuperable A1007 de ML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1007
dev_langs:
- C++
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10b883fad01943cd8cff71b3da9dee66407ccc93
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055734"
---
# <a name="ml-fatal-error-a1007"></a>Error irrecuperable A1007 de ML
**nivel de anidamiento demasiado profundo**  
  
 El ensamblador alcanzó su límite de anidamiento. El límite es de 20 niveles excepto donde se indique lo contrario.  
  
 Uno de los siguientes se están demasiado anidado:  
  
-   Una directiva de alto nivel, como [. IF](../../assembler/masm/dot-if.md), [. Repita](../../assembler/masm/dot-repeat.md), o [. MIENTRAS](../../assembler/masm/dot-while.md).  
  
-   Una definición de estructura.  
  
-   Una directiva condicional ensamblado.  
  
-   Una definición de procedimiento.  
  
-   A [PUSHCONTEXT](../../assembler/masm/pushcontext.md) directiva (el límite son 10).  
  
-   Una definición de segmento.  
  
-   Un archivo de inclusión.  
  
-   Una macro.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)