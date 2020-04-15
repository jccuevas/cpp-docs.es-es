---
title: _callnewh
ms.date: 4/2/2020
api_name:
- _callnewh
- _o__callnewh
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: d93de7f963a370810ed3b30af04d6d602abf6313
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333659"
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

*Tamaño*<br/>
Cantidad de memoria que el [nuevo operador](../../cpp/new-operator-cpp.md) ha intentado asignar.

## <a name="return-value"></a>Valor devuelto

|Value|Descripción|
|-----------|-----------------|
|0|Error: No se instala ningún controlador nuevo o no hay ningún controlador nuevo activo.|
|1|Operación correcta: El controlador nuevo se instala y activa. Se puede volver a intentar asignar memoria.|

## <a name="exceptions"></a>Excepciones

Esta función genera [bad_alloc](../../standard-library/bad-alloc-class.md) si el *nuevo controlador* no se puede localizar.

## <a name="remarks"></a>Observaciones

Se llama al *nuevo controlador* si el [nuevo operador](../../cpp/new-operator-cpp.md) no asigna memoria correctamente. El controlador nuevo podría iniciar una acción adecuada, por ejemplo liberar memoria de modo que las asignaciones subsiguientes se realicen correctamente.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>Consulte también

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
