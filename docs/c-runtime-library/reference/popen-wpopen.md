---
title: _popen, _wpopen
description: Una referencia para las funciones de la biblioteca en tiempo de ejecución de Microsoft C (CRT) _popen y _wpopen.
ms.date: 01/28/2020
api_name:
- _popen
- _wpopen
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
no-loc:
- _popen
- _wpopen
- _tpopen
- _doserrno
- errno
- _sys_errlist
- _sys_nerr
- EINVAL
ms.openlocfilehash: 68531256fd688b50b659c885635ffa17d17773a5
ms.sourcegitcommit: 684181561490e0d1955cf601d222f67f09af6d00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2020
ms.locfileid: "76894325"
---
# <a name="_popen-_wpopen"></a>_popen, _wpopen

Crea una canalización y ejecuta un comando.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
FILE *_popen(
    const char *command,
    const char *mode
);
FILE *_wpopen(
    const wchar_t *command,
    const wchar_t *mode
);
```

### <a name="parameters"></a>Parameters

\ de *comandos*
Comando que se va a ejecutar.

\ *modo*
Modo del flujo devuelto.

## <a name="return-value"></a>Valor devuelto

Devuelve un flujo asociado a un extremo de la canalización creada. El otro extremo de la canalización se asocia a la entrada o salida estándar del comando generado. Las funciones devuelven **NULL** si se produce un error. Si el error se debe a un parámetro no válido, **errno** se establece en **EINVAL**. Vea los modos válidos en la sección de comentarios.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notas

La función **_popen** crea una canalización. A continuación, ejecuta de forma asincrónica una copia generada del procesador de comandos y usa el *comando* como línea de comandos. La cadena de caracteres *mode* especifica el tipo de acceso solicitado, como se indica a continuación.

|Modo de acceso|Descripción|
|-|-|
|**"r"**|El proceso de llamada puede leer la salida estándar del comando generado mediante el flujo devuelto.|
|**"w"**|El proceso de llamada puede escribir en la entrada estándar del comando generado mediante el flujo devuelto.|
|**"b"**|Abrir en modo binario.|
|**"t"**|Abrir en modo de texto.|

> [!NOTE]
> Si se usa en un programa de Windows, la función **_popen** devuelve un puntero de archivo no válido que hace que el programa deje de responder indefinidamente. **_popen** funciona correctamente en una aplicación de consola. Para crear una aplicación de Windows que redirija la entrada y la salida, vea [crear un proceso secundario con entrada y salida redirigidas](/windows/win32/ProcThread/creating-a-child-process-with-redirected-input-and-output) en el Windows SDK.

**_wpopen** es una versión con caracteres anchos de **_popen**; el argumento de *ruta de acceso* para **_wpopen** es una cadena de caracteres anchos. **_wpopen** y **_popen** se comportan de manera idéntica.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>Requisitos de

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_popen.c
/* This program uses _popen and _pclose to receive a
* stream of text from a system process.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{

   char   psBuffer[128];
   FILE   *pPipe;

        /* Run DIR so that it writes its output to a pipe. Open this
         * pipe with read text attribute so that we can read it
         * like a text file.
         */

   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )
      exit( 1 );

   /* Read pipe until end of file, or an error occurs. */

   while(fgets(psBuffer, 128, pPipe))
   {
      puts(psBuffer);
   }

   /* Close pipe and print return value of pPipe. */
   if (feof( pPipe))
   {
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );
   }
   else
   {
     printf( "Error: Failed to read the pipe to the end.\n");
   }
}
```

Esta salida supone que hay un solo archivo en el directorio actual que tiene una extensión de nombre de archivo `.c`.

```Output
Volume in drive C is CDRIVE
Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>Vea también

\ [de control de proceso y entorno](../../c-runtime-library/process-and-environment-control.md)
[_pclose](pclose.md)\
[_pipe](pipe.md)
