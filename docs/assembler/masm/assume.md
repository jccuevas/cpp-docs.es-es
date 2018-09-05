---
title: SUPONGA | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- ASSUME
dev_langs:
- C++
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a0e43548292d2ffecbebdaead6aa12d6dacc352
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693813"
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