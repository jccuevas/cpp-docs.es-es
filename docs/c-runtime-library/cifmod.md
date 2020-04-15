---
title: _CIfmod
ms.date: 4/2/2020
api_name:
- _CIfmod
- _o__CIfmod
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CIfmod
- CIfmod
helpviewer_keywords:
- CIfmod intrinsic
- _CIfmod intrinsic
ms.assetid: 7c050653-7ec6-4810-b3a7-7a0057ea65ed
ms.openlocfilehash: 8f1a78da3ed210ef37c3295adbd5d55f0215e7ff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349568"
---
# <a name="_cifmod"></a>_CIfmod

Calcula el resto del punto flotante de los dos valores superiores de la pila.

## <a name="syntax"></a>Sintaxis

```
void __cdecl _CIfmod();
```

## <a name="remarks"></a>Observaciones

Esta versión de la función `fmod` tiene una convención de llamada especializada que el compilador entiende. Acelera la ejecución porque evita que se generen copias y ayuda con la asignación de registros.

El valor resultante se inserta en la parte superior de la pila.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](global-state.md).

## <a name="requirements"></a>Requisitos

**Plataforma:** x86

## <a name="see-also"></a>Consulte también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[fmod, fmodf](../c-runtime-library/reference/fmod-fmodf.md)
