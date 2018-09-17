---
title: Registro de MxCsr | Microsoft Docs
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
ms.openlocfilehash: 0d18a4247d36e6894230d74322d52cd5854e42fb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726510"
---
# <a name="mxcsr"></a>MxCsr

El estado del registro también incluye MxCsr. La convención de llamada divide este registro en una parte volátil y una parte permanente. La parte variable consta de las marcas de 6 estado, MXCSR [0:5], mientras que el resto del registro, MXCSR [6:15], se considera no volátil.

La parte no variable se establece en los valores estándar siguientes al principio de la ejecución del programa:

```
MXCSR[6]         : Denormals are zeros - 0
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)
```

Un destinatario que modifica cualquiera de los campos no volátiles dentro de MXCSR debe restaurarlos antes de devolver al llamador. Además, un llamador que se ha modificado alguno de estos campos debe restaurarlos a sus valores estándares antes de invocar a un destinatario a menos que el contrato, el destinatario espere los valores modificados.

Existen dos excepciones a las reglas sobre no volátiles de las marcas de control:

- En funciones donde es el propósito documentado de la función especificada modificar el registro de MxCsr no volátil marcas.

- Cuando es probablemente una correcta que da como resultado la infracción de estas reglas en los programas que se comporta igual que un programa que estas reglas no se infringen, por ejemplo, mediante el análisis de todo el programa.

Se pueden hacer ninguna suposición sobre el estado de la parte variable de MXCSR a través de un límite de función, a menos que se describen específicamente en la documentación de la función.

## <a name="see-also"></a>Vea también

[Convención de llamada](../build/calling-convention.md)