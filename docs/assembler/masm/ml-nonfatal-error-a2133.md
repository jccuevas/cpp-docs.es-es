---
title: Error recuperable A2133 de ML
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: c2d13aefe02543129340bcc307771a1026776d61
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854620"
---
# <a name="ml-nonfatal-error-a2133"></a>Error recuperable A2133 de ML

**valor de registro sobrescrito por INVOKE**

Se pasó un registro como argumento a un procedimiento, pero el código generado por [INVOKE](../../assembler/masm/invoke.md) para pasar otros argumentos destruye el contenido del registro.

El ensamblador puede usar los registros AX, AL, AH, EAX, DX, DL, DH y EDX para realizar la conversión de datos.

Use un registro diferente.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>