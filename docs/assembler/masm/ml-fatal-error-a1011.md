---
title: Error irrecuperable A1011 de ML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1011
dev_langs: C++
helpviewer_keywords: A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 470340e76897394e5b8ecb042ff97562b0c94c2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ml-fatal-error-a1011"></a>Error irrecuperable A1011 de ML
**Directiva debe estar en el bloque de control**  
  
 El ensamblador encontró una directiva de alto nivel donde no se esperaba. Se encontró una de las siguientes directivas:  
  
-   [. ELSE](../../assembler/masm/dot-else.md) sin [. IF](../../assembler/masm/dot-if.md)  
  
-   [. ENDIF](../../assembler/masm/dot-endif.md) sin [. IF](../../assembler/masm/dot-if.md)  
  
-   [. ENDW](../../assembler/masm/dot-endw.md) sin [. WHILE](../../assembler/masm/dot-while.md)  
  
-   [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md) sin [. REPITA](../../assembler/masm/dot-repeat.md)  
  
-   [. CONTINUAR](../../assembler/masm/dot-continue.md) sin [. MIENTRAS](../../assembler/masm/dot-while.md) o [. REPITA](../../assembler/masm/dot-repeat.md)  
  
-   [. INTERRUMPIR](../../assembler/masm/dot-break.md) sin [. MIENTRAS](../../assembler/masm/dot-while.md) o [. REPITA](../../assembler/masm/dot-repeat.md)  
  
-   [. ELSE](../../assembler/masm/dot-else.md) siguiente`.ELSE`  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)