---
title: _get_errno
ms.date: 4/2/2020
api_name:
- _get_errno
- _o__get_errno
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_errno
helpviewer_keywords:
- get_errno function
- errno global variable
- _get_errno function
ms.assetid: b3fd5ebc-f41b-4314-a2f4-2f2d79d6e740
ms.openlocfilehash: f693655ecd1eb0122577446e39d4188703674419
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345178"
---
# <a name="_get_errno"></a>_get_errno

Obtiene el valor actual de la variable global errno.

## <a name="syntax"></a>Sintaxis

```C
errno_t _get_errno(
   int * pValue
);
```

### <a name="parameters"></a>Parámetros

*pValue*<br/>
Puntero a un entero que se va a rellenar con el valor actual de la variable **errno.**

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error. Si *pValue* es **NULL**, se invoca el controlador de parámetros no válidos como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno en** **EINVAL** y devuelve **EINVAL**.

## <a name="remarks"></a>Observaciones

Los valores posibles de **errno** se definen en Errno.h. Vea también [errno (Constantes)](../../c-runtime-library/errno-constants.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="example"></a>Ejemplo

```C
// crt_get_errno.c
#include <stdio.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <share.h>
#include <errno.h>

int main()
{
   errno_t err;
   int pfh;
   _sopen_s( &pfh, "nonexistent.file", _O_WRONLY, _SH_DENYNO, _S_IWRITE );
   _get_errno( &err );
   printf( "errno = %d\n", err );
   printf( "fyi, ENOENT = %d\n", ENOENT );
}
```

```Output
errno = 2
fyi, ENOENT = 2
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_get_errno**|\<stdlib.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[_set_errno](set-errno.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
