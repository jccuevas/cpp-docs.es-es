---
title: Error recuperable A2133 de ML | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 0df094f5e7135ffb3b9a5f09383e03e411755de3
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678071"
---
# <a name="ml-nonfatal-error-a2133"></a>Error recuperable A2133 de ML

**registrar valor sobrescrito INVOKE**

Un registro que se pasó como argumento a un procedimiento, pero el código generado por [INVOKE](../../assembler/masm/invoke.md) pasar otros argumentos destruye el contenido del registro.

Los registros AX, AL, AH, EAX, DX, DL, DH y EDX pueden utilizarse el ensamblador para realizar la conversión de datos.

Use un registro diferente.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>