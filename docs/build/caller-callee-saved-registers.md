---
title: Registros guardados del llamador y destinatario | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f65e88c8609d6a2097e9e54c3f52cbd27dce36d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366801"
---
# <a name="callercallee-saved-registers"></a>Registros guardados del llamador y del destinatario
Los registros RAX, RCX, RDX, R8, R9, R10, R11 se consideran volátiles y deben tener en cuenta que se destruyen en llamadas a funciones (a menos que lo contrario seguridad-comprobable análisis como optimización completa del programa).  
  
 Los registros RBX, RBP, RDI, RSI, RSP, R12, R13, R14 y R15 se consideran no volátiles y deben guardarse y restaurarlos una función que los utilice.  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)