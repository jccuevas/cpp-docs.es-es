---
title: __dllonexit
ms.date: 11/04/2016
api_name:
- __dllonexit
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __dllonexit
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
ms.openlocfilehash: 61d63c751dd755bf8a7680c674681e114945814b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940441"
---
# <a name="__dllonexit"></a>__dllonexit

Registra una rutina que se llama a la hora de salida.

## <a name="syntax"></a>Sintaxis

```
_onexit_t __dllonexit(   _onexit_t func,
   _PVFV **  pbegin,
   _PVFV **  pend
   )
```

#### <a name="parameters"></a>Parámetros

*func*<br/>
Puntero a una función que se ejecuta al salir.

*pbegin*<br/>
Puntero a una variable que señala al comienzo de una lista de funciones que se ejecutan al desasociar.

*pend*<br/>
Puntero a una variable que señala al final de una lista de funciones que se ejecutan al desasociar.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un puntero a la función del usuario. En caso contrario, un puntero **NULL**.

## <a name="remarks"></a>Comentarios

La función `__dllonexit` es análoga a la función [_onexit](../c-runtime-library/reference/onexit-onexit-m.md) excepto en que esta rutina no puede ver las variables globales que usa esa función. En lugar de variables globales, esta función usa los parámetros `pbegin` y `pend`.

Las funciones `_onexit` y `atexit` en un archivo DLL vinculado con MSVCRT.LIB deben mantener su propia lista atexit/_onexit. Esta rutina es el proceso de trabajo al que llaman estos archivos DLL.

El tipo `_PVFV` se define como `typedef void (__cdecl *_PVFV)(void)`.

## <a name="requirements"></a>Requisitos

|Rutina|Archivo necesario|
|-------------|-------------------|
|__dllonexit|onexit.c|

## <a name="see-also"></a>Vea también

[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
