---
title: _chdir, _wchdir
ms.date: 11/04/2016
api_name:
- _wchdir
- _chdir
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
- tchdir
- _chdir
- _wchdir
- _tchdir
- wchdir
helpviewer_keywords:
- _tchdir function
- _chdir function
- _wchdir function
- tchdir function
- wchdir function
- chdir function
- directories [C++], changing
ms.assetid: 85e9393b-62ac-45d5-ab2a-fa2217f6152e
ms.openlocfilehash: 2b54e0978626779be21900e543a546bfae05efe2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939373"
---
# <a name="_chdir-_wchdir"></a>_chdir, _wchdir

Cambia el directorio de trabajo actual.

## <a name="syntax"></a>Sintaxis

```C
int _chdir(
   const char *dirname
);
int _wchdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Parámetros

*dirname*<br/>
Ruta de acceso del nuevo directorio de trabajo.

## <a name="return-value"></a>Valor devuelto

Estas funciones devuelven un valor de 0 si se ejecutan correctamente. Un valor devuelto de-1 indica un error. Si no se encuentra la ruta de acceso especificada, **errno** se establece en **ENOENT**. Si *dirname* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve-1.

## <a name="remarks"></a>Comentarios

La función **_chdir** cambia el directorio de trabajo actual al directorio especificado por *dirname*. El parámetro *dirname* debe hacer referencia a un directorio existente. Esta función puede cambiar el directorio de trabajo actual de cualquier unidad. Si se especifica una nueva letra de unidad en *dirname*, la letra de unidad predeterminada también se cambia. Por ejemplo, si A es la letra de unidad predeterminada y \BIN es el directorio de trabajo actual, la siguiente llamada cambia el directorio de trabajo actual a la unidad C y establece C como nueva unidad predeterminada:

```C
_chdir("c:\temp");
```

Al usar el carácter de barra diagonal inversa opcional **&#92;** () en las rutas de acceso, debe colocar dos barras **&#92;** diagonales inversas () en un literal de cadena de C **&#92;** para representar una sola barra diagonal inversa ().

**_wchdir** es una versión con caracteres anchos de **_chdir**; el argumento *dirname* para **_wchdir** es una cadena de caracteres anchos. **_wchdir** y **_chdir** se comportan de manera idéntica.

### <a name="generic-text-routine-mapping"></a>Asignación de rutina de texto genérico:

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchdir**|**_chdir**|**_chdir**|**_wchdir**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_chdir**|\<direct.h>|\<errno.h>|
|**_wchdir**|\<direct.h> o \<wchar.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_chdir.c
// arguments: C:\WINDOWS

/* This program uses the _chdir function to verify
   that a given directory exists. */

#include <direct.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( int argc, char *argv[] )
{

   if(_chdir( argv[1] ) )
   {
      switch (errno)
      {
      case ENOENT:
         printf( "Unable to locate the directory: %s\n", argv[1] );
         break;
      case EINVAL:
         printf( "Invalid buffer.\n");
         break;
      default:
         printf( "Unknown error.\n");
      }
   }
   else
      system( "dir *.exe");
}
```

```Output
Volume in drive C has no label.
Volume Serial Number is 2018-08A1

Directory of c:\windows

08/29/2002  04:00 AM         1,004,032 explorer.exe
12/17/2002  04:43 PM            10,752 hh.exe
03/03/2003  09:24 AM            33,792 ieuninst.exe
10/29/1998  04:45 PM           306,688 IsUninst.exe
08/29/2002  04:00 AM            66,048 NOTEPAD.EXE
03/03/2003  09:24 AM            33,792 Q330994.exe
08/29/2002  04:00 AM           134,144 regedit.exe
02/28/2003  06:26 PM            46,352 setdebug.exe
08/29/2002  04:00 AM            15,360 TASKMAN.EXE
08/29/2002  04:00 AM            49,680 twunk_16.exe
08/29/2002  04:00 AM            25,600 twunk_32.exe
08/29/2002  04:00 AM           256,192 winhelp.exe
08/29/2002  04:00 AM           266,752 winhlp32.exe
              13 File(s)      2,249,184 bytes
               0 Dir(s)  67,326,029,824 bytes free
```

## <a name="see-also"></a>Vea también

[Control de directorio](../../c-runtime-library/directory-control.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
