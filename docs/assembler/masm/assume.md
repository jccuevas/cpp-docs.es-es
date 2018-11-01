---
title: ASSUME
ms.date: 08/30/2018
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 97a57cc8a1acccf70572ff963e496aa79fa3ab43
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500573"
---
# <a name="assume"></a>ASSUME

Habilita la comprobación de errores para los valores de registro.

## <a name="syntax"></a>Sintaxis

> Supongamos que *segregister*:*nombre* [[, *segregister*:*nombre*]]...<br/>
> Supongamos que *dataregister*:*tipo* [[, *dataregister*:*tipo*]]...<br/>
> Supongamos que *registrar*: ERROR [[, *registrar*: ERROR]]...<br/>
> Supongamos que [[*registrar*:]] nada [[, *registrar*: nada]]...

## <a name="remarks"></a>Comentarios

Después de un `ASSUME` se entra en vigor, el ensamblador inspecciona cambios en los valores de los registros determinados. **ERROR** genera un error si se usa el registro. **No hay nada** quita registrar la comprobación de errores. Puede combinar diferentes tipos de supuestos en una sola instrucción.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>