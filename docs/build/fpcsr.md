---
title: FpCsr
ms.date: 11/04/2016
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
ms.openlocfilehash: 018ce39a194d5153f73fa452990844362190e6bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472829"
---
# <a name="fpcsr"></a>FpCsr

El estado del registro también incluye x87 palabra de control FPU. La convención de llamada dicta el registro para que sea permanente.

X87 registro de palabra de control FPU se establece en los valores estándar siguientes al principio de la ejecución del programa:

```
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)
FPCSR[7]: Reserved - 0
FPCSR[8:9]: Precision Control - 10B (double precision)
FPCSR[10:11]: Rounding  control - 0 (round to nearest)
FPCSR[12]: Infinity control - 0 (not used)
```

Un destinatario que modifica cualquiera de los campos dentro de FPCSR debe restaurarlos antes de devolver al llamador. Además, un llamador que se ha modificado alguno de estos campos debe restaurarlos a sus valores estándares antes de invocar a un destinatario a menos que el contrato, el destinatario espere los valores modificados.

Existen dos excepciones a las reglas sobre no volátiles de las marcas de control:

1. En funciones donde es el propósito documentado de la función especificada modificar el control FPCSR no volátiles marcas.

1. Cuando es probablemente una correcta que da como resultado la infracción de estas reglas en los programas que se comporta igual que un programa que estas reglas no se infringen, por ejemplo, mediante el análisis de todo el programa.

## <a name="see-also"></a>Vea también

[Convención de llamada](../build/calling-convention.md)