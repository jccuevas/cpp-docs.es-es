---
title: _findclose
ms.date: 11/04/2016
api_name:
- _findclose
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _findclose
- findclose
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
ms.openlocfilehash: c67336cc12bcdee754edd40b91078faa83a17984
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957318"
---
# <a name="_findclose"></a>_findclose

Cierra el identificador de búsqueda especificado y libera los recursos asociados.

## <a name="syntax"></a>Sintaxis

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>Parámetros

*handle*<br/>
Identificador de búsqueda devuelto por una llamada anterior a **_findfirst**.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **_findclose** devuelve 0. De lo contrario, devuelve-1 y establece **errno** en **ENOENT**, lo que indica que no se encontraron más archivos coincidentes.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_findclose**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Llamadas del sistema](../../c-runtime-library/system-calls.md)<br/>
[Funciones de búsqueda de nombre de archivo](../../c-runtime-library/filename-search-functions.md)<br/>
