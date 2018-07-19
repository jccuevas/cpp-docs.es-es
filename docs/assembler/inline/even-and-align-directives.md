---
title: Directivas EVEN y ALIGN | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a43425a4038ffb140eeaa0a9d111a39fc5c11ff0
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32057960"
---
# <a name="even-and-align-directives"></a>Directivas EVEN y ALIGN
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Aunque el ensamblador alineado no es compatible con la mayoría de las directivas MASM, sí admite `EVEN` y **alinear**. Estas directivas colocan **NOP** (sin operación) las instrucciones en el código de ensamblado según sea necesario para ajustar las etiquetas a los límites específicos. Esto hace que las operaciones de búsqueda de instrucciones sean más eficaces en algunos procesadores.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)