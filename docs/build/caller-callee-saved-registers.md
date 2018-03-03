---
title: Registros guardados del llamador y destinatario | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 61e8d57c177ded8102f257cf84adedc0de0e312a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="callercallee-saved-registers"></a>Registros guardados del llamador y del destinatario
Los registros RAX, RCX, RDX, R8, R9, R10, R11 se consideran volátiles y deben tener en cuenta que se destruyen en llamadas a funciones (a menos que lo contrario seguridad-comprobable análisis como optimización completa del programa).  
  
 Los registros RBX, RBP, RDI, RSI, RSP, R12, R13, R14 y R15 se consideran no volátiles y deben guardarse y restaurarlos una función que los utilice.  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)