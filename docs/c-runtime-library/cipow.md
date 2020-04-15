---
title: _CIpow
ms.date: 4/2/2020
api_name:
- _CIpow
- _o__CIpow
api_location:
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr90.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIpow
- _CIpow
helpviewer_keywords:
- CIpow intrinsic
- _CIpow intrinsic
ms.assetid: 477aaf0c-ac58-4252-89dd-9f3e35d47536
ms.openlocfilehash: 1b0c900fbd9cb3070f7666a3b032ee7e44f9f881
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349416"
---
# <a name="_cipow"></a>_CIpow

Calcula *x* elevado a la potencia de *y* en función de los valores superiores de la pila.

## <a name="syntax"></a>Sintaxis

```
void __cdecl _CIpow();
```

## <a name="remarks"></a>Observaciones

Esta versión de la función `pow` tiene una convención de llamada especializada que el compilador entiende. Acelera la ejecución porque evita que se generen copias y ayuda con la asignación de registros.

El valor resultante se inserta en la parte superior de la pila.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](global-state.md).

## <a name="requirements"></a>Requisitos

**Plataforma:** x86

## <a name="see-also"></a>Consulte también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[pow, powf, powl](../c-runtime-library/reference/pow-powf-powl.md)
