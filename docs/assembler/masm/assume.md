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
ms.openlocfilehash: 6fbba50e56ae06dc3afb64582d4a131bba75a6c8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055858"
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