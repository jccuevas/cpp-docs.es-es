---
title: FpCsr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6ed0500d0382563878d0751ba5386e4cc637fdb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718294"
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