---
title: getenv, _wgetenv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- getenv
- _wgetenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wgetenv
- getenv
- _tgetenv
dev_langs:
- C++
helpviewer_keywords:
- getenv function
- tgetenv function
- wgetenv function
- environment values
- environment variables
- _tgetenv function
- _wgetenv function
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2e68ca55d9e33995df583719e4797a6880d34ca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403991"
---
# <a name="getenv-wgetenv"></a>getenv, _wgetenv

Obtiene un valor del entorno actual. Hay disponibles versiones más seguras de estas funciones; vea [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
char *getenv(
   const char *varname
);
wchar_t *_wgetenv(
   const wchar_t *varname
);
```

### <a name="parameters"></a>Parámetros

*VarName*<br/>
Nombre de la variable de entorno.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la entrada de tabla entorno que contiene *varname*. No es seguro modificar el valor de la variable de entorno con el puntero devuelto. Use la [_putenv](putenv-wputenv.md) función para modificar el valor de una variable de entorno. El valor devuelto es **NULL** si *varname* no se encuentra en la tabla de entorno.

## <a name="remarks"></a>Comentarios

El **getenv** función busca en la lista de variables de entorno para *varname*. **getenv** no distingue mayúsculas de minúsculas en el sistema operativo Windows. **getenv** y **_putenv** usan la copia del entorno indicado por la variable global **_environ** para tener acceso al entorno. **getenv** solo funciona en las estructuras de datos puede tener acceso a la biblioteca de tiempo de ejecución y no en el entorno "segmento" creada para el proceso por el sistema operativo. Por lo tanto, los programas que utilizan el *envp* argumento pasado a [principal](../../cpp/main-program-startup.md) o [wmain](../../cpp/main-program-startup.md) puede recuperar información no válida.

Si *varname* es **NULL**, esta función invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve **NULL**.

**_wgetenv** es una versión con caracteres anchos de **getenv**; el argumento y el valor devuelto de **_wgetenv** son cadenas de caracteres anchos. El **_wenviron** (variable global) es una versión con caracteres anchos de **_environ**.

En un programa MBCS (por ejemplo, en un programa ASCII de SBCS), **_wenviron** es inicialmente **NULL** porque el entorno está formado por cadenas de caracteres multibyte. A continuación, en la primera llamada a [_wputenv](putenv-wputenv.md), o en la primera llamada a **_wgetenv** si ya existe un entorno (MBCS), un entorno correspondiente de cadena de caracteres anchos se crea y, a continuación, apunta **_wenviron**.

De forma similar en Unicode (**_wmain**) programa, **_environ** es inicialmente **NULL** porque el entorno está formado por cadenas de caracteres anchos. A continuación, en la primera llamada a **_putenv**, o en la primera llamada a **getenv** si ya existe un entorno (Unicode), un entorno de MBCS correspondiente, se crea y, a continuación, apunta a **_ Environ**.

Si dos copias del entorno (MBCS y Unicode) existen simultáneamente en un programa, el sistema en tiempo de ejecución debe mantener las dos copias, lo que ralentiza el tiempo de ejecución. Por ejemplo, cada vez que se llama a **_putenv**, una llamada a **_wputenv** también se ejecuta automáticamente, por lo que se correspondan las dos cadenas de entorno.

> [!CAUTION]
> En raras ocasiones, cuando el sistema en tiempo de ejecución mantiene una versión Unicode y una versión multibyte del entorno, las dos versiones del entorno podrían no corresponderse exactamente. La razón es que, aunque cualquier cadena de caracteres multibyte se asigna a una cadena de Unicode única, la asignación de una cadena de Unicode única a una cadena de caracteres multibyte no es necesariamente única. Para obtener más información, vea [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> El **_putenv** y **_getenv** familias de funciones no son seguras para subprocesos. **_getenv** podría devolver un puntero de cadena mientras **_putenv** modifica la cadena, lo que provoca errores aleatorios. Asegúrese de que las llamadas a estas funciones están sincronizadas.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv**|**getenv**|**_wgetenv**|

Para comprobar o cambiar el valor de la **TZ** uso de variable de entorno **getenv**, **_putenv** y **_tzset** según sea necesario. Para obtener más información acerca de **TZ**, consulte [_tzset](tzset.md) y [_daylight, timezone y _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**getenv**|\<stdlib.h>|
|**_wgetenv**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_getenv.c
// compile with: /W3
// This program uses getenv to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *libvar;

   // Get the value of the LIB environment variable.
   libvar = getenv( "LIB" ); // C4996
   // Note: getenv is deprecated; consider using getenv_s instead

   if( libvar != NULL )
      printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects the environment
   // variable of the current process. The command processor's
   // environment is not changed.
   _putenv( "LIB=c:\\mylib;c:\\yourlib" ); // C4996
   // Note: _putenv is deprecated; consider using putenv_s instead

   // Get new value.
   libvar = getenv( "LIB" ); // C4996

   if( libvar != NULL )
      printf( "New LIB variable is: %s\n", libvar );
}
```

```Output
Original LIB variable is: C:\progra~1\devstu~1\vc\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[Constantes de entorno](../../c-runtime-library/environmental-constants.md)<br/>
