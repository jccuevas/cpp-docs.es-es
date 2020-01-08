---
title: Error recuperable A2133 de ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: 1ffdf5fb6577dbd4e24312b3c57a4186173ddcf6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312643"
---
# <a name="ml-nonfatal-error-a2133"></a>Error recuperable A2133 de ML

**valor de registro sobrescrito por INVOKE**

Se pasó un registro como argumento a un procedimiento, pero el código generado por [INVOKE](invoke.md) para pasar otros argumentos destruye el contenido del registro.

El ensamblador puede usar los registros AX, AL, AH, EAX, DX, DL, DH y EDX para realizar la conversión de datos.

Use un registro diferente.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](ml-error-messages.md)
