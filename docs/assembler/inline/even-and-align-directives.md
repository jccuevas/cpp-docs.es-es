---
title: Directivas EVEN y ALIGN | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- align
- EVEN
dev_langs: C++
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5048e9f8c2991133ad0cf28720b9236232cc9337
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="even-and-align-directives"></a>Directivas EVEN y ALIGN
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Aunque el ensamblador alineado no es compatible con la mayoría de las directivas MASM, sí admite `EVEN` y **alinear**. Estas directivas colocan **NOP** (sin operación) las instrucciones en el código de ensamblado según sea necesario para ajustar las etiquetas a los límites específicos. Esto hace que las operaciones de búsqueda de instrucciones sean más eficaces en algunos procesadores.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)