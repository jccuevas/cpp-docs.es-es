---
title: FpCsr | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15b7caebc99c4724c0e28b7812da8ef224184385
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fpcsr"></a>FpCsr
El estado del registro también incluye x87 palabra de control FPU. La convención de llamada dicta el registro para que sea no volátil.  
  
 X87 registro de palabras de control FPU se establece en los valores estándar siguientes al principio de la ejecución del programa:  
  
```  
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)  
FPCSR[7]: Reserved - 0  
FPCSR[8:9]: Precision Control - 10B (double precision)  
FPCSR[10:11]: Rounding  control - 0 (round to nearest)  
FPCSR[12]: Infinity control - 0 (not used)  
```  
  
 Un destinatario que modifica cualquiera de los campos dentro de FPCSR debe restaurarlos antes de devolver al llamador. Además, un llamador que haya modificado alguno de estos campos debe restaurarlos a sus valores estándares antes de invocar a un destinatario, a menos que el acuerdo, el destinatario espere los valores modificados.  
  
 Hay dos excepciones a las reglas relativas a no volátiles de los indicadores de control:  
  
1.  En funciones donde el propósito documentado de la función especificada es modificar el control FPCSR no volátiles marca.  
  
2.  Cuando es demostrado correcto que la infracción de estas reglas resulta en un programa que se comporta igual que un programa donde se infringen estas reglas no, por ejemplo, mediante el análisis de todo el programa.  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)