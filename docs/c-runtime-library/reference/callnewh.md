---
title: _callnewh
ms.date: 11/04/2016
api_name:
- _callnewh
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 3e14450538807b164897c335f7e37d82d8562314
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939379"
---
# <a name="_callnewh"></a>_callnewh

Llama al *nuevo controlador* instalado actualmente.

## <a name="syntax"></a>Sintaxis

```cpp
int _callnewh(
   size_t size
   )
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Cantidad de memoria que el [nuevo operador](../../cpp/new-operator-cpp.md) ha intentado asignar.

## <a name="return-value"></a>Valor devuelto

|Valor|DESCRIPCIÓN|
|-----------|-----------------|
|0|Fallida No se instala ningún controlador nuevo o no hay ningún controlador nuevo activo.|
|1|Realizado El nuevo controlador está instalado y activo. Se puede volver a intentar asignar memoria.|

## <a name="exceptions"></a>Excepciones

Esta función genera [bad_alloc](../../standard-library/bad-alloc-class.md) si el *nuevo controlador* no se puede localizar.

## <a name="remarks"></a>Comentarios

Se llama al *nuevo controlador* si el [nuevo operador](../../cpp/new-operator-cpp.md) no asigna memoria correctamente. El controlador nuevo podría iniciar una acción adecuada, por ejemplo liberar memoria de modo que las asignaciones subsiguientes se realicen correctamente.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>Vea también

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
