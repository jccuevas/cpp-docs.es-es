---
title: __uncaught_exception
ms.date: 11/04/2016
api_name:
- __uncaught_exception
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __uncaught_exception
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: 0130776ec2511aefd42d1700f950d97738e9fb14
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945949"
---
# <a name="__uncaught_exception"></a>__uncaught_exception

Indica si se han producido una o más excepciones, pero que aún no se han controlado por el bloque **catch** correspondiente de una instrucción [try-catch](../../cpp/try-throw-and-catch-statements-cpp.md) .

## <a name="syntax"></a>Sintaxis

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>Valor devuelto

**true** desde el momento en que se produce una excepción en un bloque **try** hasta que se inicializa el bloque **catch** correspondiente; en caso contrario, **false**.

## <a name="remarks"></a>Comentarios

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>Vea también

[Instrucciones try, throw y catch (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
