---
title: _CIcos
ms.date: 04/11/2018
api_name:
- _CIcos
api_location:
- msvcr90.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIcos
- _CIcos
helpviewer_keywords:
- _CIcos intrinsic
- CIcos intrinsic
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
ms.openlocfilehash: 5a57e948a73b8c4243ebe5a8a12f62cc55a40f3b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940539"
---
# <a name="_cicos"></a>_CIcos

Calcula el coseno del valor superior de la pila de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
void __cdecl _CIcos();
```

## <a name="remarks"></a>Comentarios

Esta versión de la función [cos](../c-runtime-library/reference/cos-cosf-cosl.md) tiene una convención de llamada especializada que el compilador entiende. Acelera la ejecución porque evita que se generen copias y ayuda con la asignación de registros.

El valor resultante se inserta en la parte superior de la pila de punto flotante.

## <a name="requirements"></a>Requisitos

**Plataforma:** x86

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[cos, cosf, cosl](../c-runtime-library/reference/cos-cosf-cosl.md)<br/>
