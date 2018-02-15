---
title: Error recuperable A2133 de ML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A2133
dev_langs:
- C++
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: adc1929f14b5264717936f1a4aebb8dabd2e439d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="ml-nonfatal-error-a2133"></a>Error recuperable A2133 de ML
**registrar valor sobrescrito INVOKE**  
  
 Un registro se pasó como argumento a un procedimiento, pero el código generado por [INVOKE](../../assembler/masm/invoke.md) pasar otros argumentos destruye el contenido del registro.  
  
 Los registros AX, AL, AH, EAX, DX, DL, DH y EDX pueden utilizarse el ensamblador para realizar la conversión de datos.  
  
 Use un registro diferente.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)