---
title: _CItan | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CItan
apilocation:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- _CItan
- CItan
dev_langs:
- C++
helpviewer_keywords:
- CItan intrinsic
- _CItan intrinsic
ms.assetid: d1ea3113-50a2-45a6-b6bc-680fcdcc0928
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcbd7f4258447df6f60f464b4c0a24080155fa9c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="citan"></a>_CItan

Calcula la tangente del valor superior de la pila de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
void __cdecl _CItan();
```

## <a name="remarks"></a>Comentarios

Esta versión de la función [tan](../c-runtime-library/reference/tan-tanf-tanl.md) tiene una convención de llamada especializada que el compilador entiende. La función acelera la ejecución porque evita que se generen copias y ayuda con la asignación de registros.

El valor resultante se inserta en la parte superior de la pila de punto flotante.

## <a name="requirements"></a>Requisitos

**Plataforma:** x86

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[tan, tanf, tanl](../c-runtime-library/reference/tan-tanf-tanl.md)<br/>
