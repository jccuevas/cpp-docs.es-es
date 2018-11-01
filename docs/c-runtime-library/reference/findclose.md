---
title: _findclose
ms.date: 11/04/2016
apiname:
- _findclose
apilocation:
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
apitype: DLLExport
f1_keywords:
- _findclose
- findclose
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
ms.openlocfilehash: 29010f8a502d463eeb6ca98837a1b7dae9f5ae6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538117"
---
# <a name="findclose"></a>_findclose

Cierra el identificador de búsqueda especificado y libera los recursos asociados.

## <a name="syntax"></a>Sintaxis

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
Identificador de búsqueda devuelto por una llamada anterior a **_findfirst**.

## <a name="return-value"></a>Valor devuelto

Si es correcto, **_findclose** devuelve 0. En caso contrario, devuelve -1 y establece **errno** a **ENOENT**, que indica que no más archivos coincidentes se encontró.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_findclose**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Llamadas del sistema](../../c-runtime-library/system-calls.md)<br/>
[Funciones de búsqueda de nombre de archivo](../../c-runtime-library/filename-search-functions.md)<br/>
