---
title: _abnormal_termination
ms.date: 11/04/2016
api_name:
- _abnormal_termination
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _abnormal_termination
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
ms.openlocfilehash: b66cf0df998b4e33a9f3425fdf0f260d163f423b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944711"
---
# <a name="_abnormal_termination"></a>_abnormal_termination

Indica si el bloque `__finally` de una [instrucción try-finally](../cpp/try-finally-statement.md) se especifica mientras el sistema ejecuta una lista interna de controladores de terminación.

## <a name="syntax"></a>Sintaxis

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>Valor devuelto

**true** si el sistema *desenreda* la pila; en caso contrario, **false**.

## <a name="remarks"></a>Comentarios

Se trata de una función interna que se usa para administrar las excepciones de desenredado y no está pensada para que se llame desde el código de usuario.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>Vea también

[try-finally (Instrucción)](../cpp/try-finally-statement.md)
