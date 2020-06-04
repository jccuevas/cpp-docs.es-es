---
title: _unlink, _wunlink
ms.date: 4/2/2020
api_name:
- _unlink
- _wunlink
- _o__unlink
- _o__wunlink
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
- _tunlink
- _unlink
- wunlink
- _wunlink
helpviewer_keywords:
- files [C++], deleting
- _wunlink function
- wunlink function
- unlink function
- _unlink function
- tunlink function
- files [C++], removing
- _tunlink function
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
ms.openlocfilehash: af6fd6c7065529b43f5e275ce1d745d0031ddfb7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909277"
---
# <a name="_unlink-_wunlink"></a>_unlink, _wunlink

Elimine un archivo.

## <a name="syntax"></a>Sintaxis

```C
int _unlink(
   const char *filename
);
int _wunlink(
   const wchar_t *filename
);
```

### <a name="parameters"></a>Parámetros

*extensión*<br/>
Nombre del archivo que se va a quitar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve 0 si se realiza correctamente. De lo contrario, la función devuelve-1 y establece **errno** en **EACCES**, lo que significa que la ruta de acceso especifica un archivo de solo lectura o un directorio, o **ENOENT**, lo que significa que no se encuentra el archivo o la ruta de acceso.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.

## <a name="remarks"></a>Observaciones

La función **_unlink** elimina el archivo especificado por *filename*. **_wunlink** es una versión con caracteres anchos de **_unlink**; el argumento *filename* para **_wunlink** es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tunlink**|**_unlink**|**_unlink**|**_wunlink**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_unlink**|\<io.h> y \<stdio.h>|
|**_wunlink**|\<io.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="code-example"></a>Ejemplo de código

Este programa usa _unlink para eliminar CRT_UNLINK.TXT.

```C
// crt_unlink.c

#include <stdio.h>

int main( void )
{
   if( _unlink( "crt_unlink.txt" ) == -1 )
      perror( "Could not delete 'CRT_UNLINK.TXT'" );
   else
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );
}
```

### <a name="input-crt_unlinktxt"></a>Entrada: crt_unlink.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>Salida de ejemplo

```Output
Deleted 'CRT_UNLINK.TXT'
```

## <a name="see-also"></a>Consulta también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[remove, _wremove](remove-wremove.md)<br/>
