---
title: Directivas EVEN y ALIGN | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- align
- EVEN
dev_langs:
- C++
helpviewer_keywords:
- EVEN directive
- directives, MASM
- MASM (Microsoft Macro Assembler), directives
- NOP (no operation instruction)
- ALIGN directive
ms.assetid: 7357ab2d-4a5c-43ca-accb-a5f21cdfcde5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 278794e0105ee054fdd4948967a78982a9d46d8c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="even-and-align-directives"></a>Directivas EVEN y ALIGN
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Aunque el ensamblador alineado no es compatible con la mayoría de las directivas MASM, sí admite `EVEN` y **alinear**. Estas directivas colocan **NOP** (sin operación) las instrucciones en el código de ensamblado según sea necesario para ajustar las etiquetas a los límites específicos. Esto hace que las operaciones de búsqueda de instrucciones sean más eficaces en algunos procesadores.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)