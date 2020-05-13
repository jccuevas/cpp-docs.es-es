---
title: _rmdir, _wrmdir
ms.date: 4/2/2020
api_name:
- _wrmdir
- _rmdir
- _o__rmdir
- _o__wrmdir
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- trmdir
- _trmdir
- wrmdir
- _rmdir
- _wrmdir
helpviewer_keywords:
- _rmdir function
- directories [C++], deleting
- rmdir function
- directories [C++], removing
- trmdir function
- _trmdir function
- _wrmdir function
- wrmdir function
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
ms.openlocfilehash: c0c5055a499614f364370b7aa90697898dc510ab
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916926"
---
# <a name="_rmdir-_wrmdir"></a>_rmdir, _wrmdir

Elimina un directorio.

## <a name="syntax"></a>Sintaxis

```C
int _rmdir(
   const char *dirname
);
int _wrmdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Parámetros

*dirname*<br/>
Ruta de acceso del directorio que se va a quitar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve 0 si el directorio se elimina correctamente. Un valor devuelto de-1 indica un error y **errno** se establece en uno de los siguientes valores:

|valor de errno|Condición|
|-|-|
| **ENOTEMPTY** | La ruta de acceso especificada no es un directorio, el directorio no está vacío o el directorio es el directorio de trabajo actual o el directorio raíz. |
| **ENOENT** | La ruta de acceso no es válida. |
| **EACCES** | Un programa tiene un identificador abierto en el directorio. |

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_rmdir** elimina el directorio especificado por *dirname*. El directorio debe estar vacío y no debe ser el directorio de trabajo actual ni el directorio raíz.

**_wrmdir** es una versión con caracteres anchos de **_rmdir**; el argumento *dirname* para **_wrmdir** es una cadena de caracteres anchos. **_wrmdir** y **_rmdir** se comportan de manera idéntica.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_trmdir**|**_rmdir**|**_rmdir**|**_wrmdir**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_rmdir**|\<direct.h>|
|**_wrmdir**|\<direct.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_mkdir](mkdir-wmkdir.md).

## <a name="see-also"></a>Consulta también

[Control de directorio](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
