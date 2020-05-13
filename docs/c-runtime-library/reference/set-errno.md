---
title: _set_errno
ms.date: 4/2/2020
api_name:
- _set_errno
- _o__set_errno
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_errno
- _set_errno
helpviewer_keywords:
- errno global variable
- set_errno function
- _set_errno function
ms.assetid: d338914a-1894-4cf3-ae45-f2c4eb26590b
ms.openlocfilehash: e889f8e2dabfffbcc69ff796fb21570b66b57fb0
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913053"
---
# <a name="_set_errno"></a>_set_errno

Establezca el valor de la variable global **errno** .

## <a name="syntax"></a>Sintaxis

```C
errno_t _set_errno( int error_value );
```

### <a name="parameters"></a>Parámetros

*error_value*<br/>
Nuevo valor de **errno**.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si es correcto.

## <a name="remarks"></a>Observaciones

Los valores posibles se definen en Errno.h. Vea también [errno (Constantes)](../../c-runtime-library/errno-constants.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="example"></a>Ejemplo

```C
// crt_set_errno.c
#include <stdio.h>
#include <errno.h>

int main()
{
   _set_errno( EILSEQ );
   perror( "Oops" );
}
```

```Output
Oops: Illegal byte sequence
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_set_errno**|\<stdlib.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[_get_errno](get-errno.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
