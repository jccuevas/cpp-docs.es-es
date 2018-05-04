---
title: MxCsr | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9df2225526c20463bdbd618322d031c3245d9493
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="mxcsr"></a>MxCsr
El estado del registro también incluye MxCsr. La convención de llamada divide este registro en una parte volátil y una parte no volátil. La parte variable está compuesta de los indicadores de 6 estado, MXCSR [0:5], mientras que el resto del registro, MXCSR [6:15], se considera no volátil.  
  
 La parte no variable se establece en los valores estándar siguientes al principio de la ejecución del programa:  
  
```  
MXCSR[6]         : Denormals are zeros - 0  
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)  
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)  
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)  
```  
  
 Un destinatario que modifica cualquiera de los campos no volátiles de MXCSR debe restaurarlos antes de devolver al llamador. Además, un llamador que haya modificado alguno de estos campos debe restaurarlos a sus valores estándares antes de invocar a un destinatario, a menos que el acuerdo, el destinatario espere los valores modificados.  
  
 Hay dos excepciones a las reglas relativas a no volátiles de los indicadores de control:  
  
-   En funciones donde el propósito documentado de la función especificada es modificar el MxCsr no variables de marcas.  
  
-   Cuando es demostrado correcto que la infracción de estas reglas resulta en un programa que se comporta igual que un programa donde se infringen estas reglas no, por ejemplo, mediante el análisis de todo el programa.  
  
 No se pueden hacer suposiciones sobre el estado de la parte variable de MXCSR en un límite de función, a menos que se describen específicamente en la documentación de una función.  
  
## <a name="see-also"></a>Vea también  
 [Convención de llamada](../build/calling-convention.md)