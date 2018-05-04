---
title: _popen, _wpopen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _popen
- _wpopen
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
dev_langs:
- C++
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a7764e15b18249a9ee3ddd452ae792c8ad172f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="popen-wpopen"></a>_popen, _wpopen

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

### <a name="parameters"></a>Parámetros

*command*<br/>
Comando que se va a ejecutar.

*mode*<br/>
Modo del flujo devuelto.

## <a name="return-value"></a>Valor devuelto

Devuelve un flujo asociado a un extremo de la canalización creada. El otro extremo de la canalización se asocia a la entrada o salida estándar del comando generado. Las funciones devuelven **NULL** si se produce un error. Si el error es un parámetro no válido, por ejemplo, si *comando* o *modo* es un puntero nulo, o *modo* no es un modo válido, **errno** está establecido en **EINVAL**. Vea los modos válidos en la sección de comentarios.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_popen** función crea una canalización y ejecuta de forma asincrónica una copia generada del procesador de comandos con la cadena especificada de *comando*. La cadena de caracteres *mode* especifica el tipo de acceso solicitado, como se indica a continuación.

**"r"** el proceso de llamada puede leer la salida estándar del comando generado mediante la secuencia devuelta.

**"w"** el proceso de llamada puede escribir en la entrada estándar del comando generado mediante la secuencia devuelta.

**"b"** abierto en modo binario.

**"t"** abierto en modo de texto.

> [!NOTE]
> Si usa un programa de Windows, la **_popen** función devuelve un puntero de archivo no válido que hace que el programa deje de responder indefinidamente. **_popen** funciona correctamente en una aplicación de consola. Para crear una aplicación de Windows que redirija la entrada y salida, consulte [crear un proceso secundario con redirección de entrada y salida](http://msdn.microsoft.com/library/windows/desktop/ms682499) del SDK de Windows.

**_wpopen** es una versión con caracteres anchos de **_popen**; el *ruta de acceso* argumento pasado a **_wpopen** es una cadena de caracteres anchos. **_wpopen** y **_popen** se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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
      printf(psBuffer);
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

### <a name="sample-output"></a>Resultados del ejemplo

En este resultado se supone que solo hay un archivo en el directorio actual con la extensión de nombre de archivo .c.

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

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pclose](pclose.md)<br/>
[_pipe](pipe.md)<br/>
