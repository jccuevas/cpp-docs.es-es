---
title: Error recuperable A2133 de ML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2133
dev_langs:
- C++
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f240ed6f2e8330017e56334dfcc41be478537c7b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="ml-nonfatal-error-a2133"></a>Error recuperable A2133 de ML
**registrar valor sobrescrito INVOKE**  
  
 Un registro se pasó como argumento a un procedimiento, pero el código generado por [INVOKE](../../assembler/masm/invoke.md) pasar otros argumentos destruye el contenido del registro.  
  
 Los registros AX, AL, AH, EAX, DX, DL, DH y EDX pueden utilizarse el ensamblador para realizar la conversión de datos.  
  
 Use un registro diferente.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)