---
title: ___setlc_active_func, ___unguarded_readlc_active_add_func
ms.date: 11/04/2016
api_name:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
api_location:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___unguarded_readlc_active_add_func
- ___setlc_active_func
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
ms.openlocfilehash: a7dd7d74992aeddffead1c6ef0d52cbc69848dad
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957286"
---
# <a name="___setlc_active_func-___unguarded_readlc_active_add_func"></a>___setlc_active_func, ___unguarded_readlc_active_add_func

OBSOLETO. CRT exporta estas funciones internas únicamente para conservar la compatibilidad binaria.

## <a name="syntax"></a>Sintaxis

```cpp
int ___setlc_active_func(void);
int * ___unguarded_readlc_active_add_func(void);
```

## <a name="return-value"></a>Valor devuelto

El valor devuelto no es significativo.

## <a name="remarks"></a>Comentarios

Las funciones de CRT internas `___setlc_active_func` y `___unguarded_readlc_active_add_func` están obsoletas y ya no se usan, pero la biblioteca de CRT las puede exportar para conservar la compatibilidad binaria. La finalidad primera de `___setlc_active_func` era devolver el número de llamadas activas actualmente a la función `setlocale`. La finalidad primera de `___unguarded_readlc_active_add_func` era devolver el número de funciones que hacían referencia a la configuración local sin bloquearla.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|ninguna|

## <a name="see-also"></a>Vea también

[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
