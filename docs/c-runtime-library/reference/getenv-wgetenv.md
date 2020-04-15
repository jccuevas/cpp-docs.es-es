---
title: getenv, _wgetenv
description: Describe la biblioteca getenv en _wgetenv tiempo de ejecución de Microsoft C y las funciones.
ms.date: 4/2/2020
api_name:
- getenv
- _wgetenv
- _o__wgetenv
- _o_getenv
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wgetenv
- getenv
- _tgetenv
helpviewer_keywords:
- getenv function
- tgetenv function
- wgetenv function
- environment values
- environment variables
- _tgetenv function
- _wgetenv function
ms.assetid: 3b9cb9ab-a126-4e0e-a44f-6c5a7134daf4
no-loc:
- getenv
- _wgetenv
- getenv_s
- _wgetenv_s
- _putenv_s
- main
- wmain
- errno
- EINVAL
- ERANGE
- _environ
- _wenviron
- _putenv
- _wputenv
- _tgetenv_s
- _tzset
- _dupenv_s
- _wdupenv_s
ms.openlocfilehash: c9d7f7e1a2c5d6b15aee2f7f972a30cc0c90115c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344250"
---
# <a name="getenv-_wgetenv"></a>getenv, _wgetenv

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

*Varname*<br/>
Nombre de la variable de entorno.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la entrada de tabla de entorno que contiene *varname*. No es seguro modificar el valor de la variable de entorno con el puntero devuelto. Utilice la función [_putenv](putenv-wputenv.md) para modificar el valor de una variable de entorno. El valor devuelto es **NULL** si *varname* no se encuentra en la tabla de entorno.

## <a name="remarks"></a>Observaciones

La función **getenv** busca *varname*en la lista de variables de entorno. **getenv** no distingue mayúsculas de minúsculas en el sistema operativo Windows. **getenv** y **_putenv** utilizan la copia del entorno a la que apunta la variable global **_environ** para acceder al entorno. **getenv** solo funciona en las estructuras de datos accesibles para la biblioteca en tiempo de ejecución y no en el "segmento" del entorno creado para el proceso por el sistema operativo. Por lo tanto, los programas que utilizan el argumento *envp* para [main](../../cpp/main-function-command-line-args.md) o [wmain](../../cpp/main-function-command-line-args.md) pueden recuperar información no válida.

Si *varname* es **NULL**, esta función invoca un controlador de parámetros no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno en** **EINVAL** y devuelve **NULL**.

**_wgetenv** es una versión de caracteres anchos de **getenv**; el argumento y el valor devuelto de **_wgetenv** son cadenas de caracteres anchos. La variable global **_wenviron** es una versión de caracteres anchos de **_environ**.

En un programa MBCS (por ejemplo, en un programa ASCII SBCS), **_wenviron** es inicialmente **NULL** porque el entorno se compone de cadenas de caracteres multibyte. A continuación, en la primera llamada a [_wputenv](putenv-wputenv.md), o en la primera llamada a **_wgetenv** si ya existe un entorno (MBCS), se crea un entorno de cadena de caracteres anchos correspondiente y, a continuación, se señala a **_wenviron**.

De forma similar en un programa Unicode (**_wmain**), **_environ** es inicialmente **NULL** porque el entorno se compone de cadenas de caracteres anchos. A continuación, en la primera llamada a **_putenv**, o en la primera llamada a **getenv** si ya existe un entorno (Unicode), se crea un entorno MBCS correspondiente y, a continuación, se señala a **_environ**.

Si dos copias del entorno (MBCS y Unicode) existen simultáneamente en un programa, el sistema en tiempo de ejecución debe mantener las dos copias, lo que ralentiza el tiempo de ejecución. Por ejemplo, cada vez que se llama a **_putenv**, una llamada a **_wputenv** también se ejecuta automáticamente, de modo que las dos cadenas de entorno corresponden.

> [!CAUTION]
> En raras ocasiones, cuando el sistema en tiempo de ejecución mantiene una versión Unicode y una versión multibyte del entorno, las dos versiones del entorno podrían no corresponderse exactamente. La razón es que, aunque cualquier cadena de caracteres multibyte se asigna a una cadena de Unicode única, la asignación de una cadena de Unicode única a una cadena de caracteres multibyte no es necesariamente única. Para obtener más información, vea [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Las **_putenv** y **_getenv** familias de funciones no son seguras para subprocesos. **_getenv** podría devolver un puntero de cadena mientras **_putenv** está modificando la cadena, lo que provoca errores aleatorios. Asegúrese de que las llamadas a estas funciones están sincronizadas.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv**|**getenv**|**_wgetenv**|

Para comprobar o cambiar el valor de la variable de entorno **TZ,** utilice **getenv**, **_putenv** y **_tzset** según sea necesario. Para obtener más información acerca de **TZ**, consulte [_tzset](tzset.md) y [_daylight, zona horaria y _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**getenv**|\<stdlib.h>|
|**_wgetenv**|\<stdlib.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[Constantes de entorno](../../c-runtime-library/environmental-constants.md)<br/>
