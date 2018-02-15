---
title: Error irrecuperable A1007 de ML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A1007
dev_langs:
- C++
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d1ef99cebab226a3af5e7e685acc5a5485872d1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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