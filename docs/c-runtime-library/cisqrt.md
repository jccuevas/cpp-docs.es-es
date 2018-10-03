---
title: _CIsqrt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _CIsqrt
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _CIsqrt
- CIsqrt
dev_langs:
- C++
helpviewer_keywords:
- CIsqrt intrinsic
- _CIsqrt intrinsic
ms.assetid: 663548ea-398c-48ee-8397-a787c6ebb937
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb57de60736d55875206ead1eabc5fbd3c3c2c0e
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235917"
---
# <a name="cisqrt"></a>_CIsqrt

Calcula la raíz cuadrada del valor superior de la pila.

## <a name="syntax"></a>Sintaxis

```
void __cdecl _CIsqrt();
```

## <a name="remarks"></a>Comentarios

Esta versión de la función `sqrt` tiene una convención de llamada especializada que el compilador entiende. Acelera la ejecución porque evita que se generen copias y ayuda con la asignación de registros.

El valor resultante se inserta en la parte superior de la pila.

## <a name="requirements"></a>Requisitos

**Plataforma:** x86

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)