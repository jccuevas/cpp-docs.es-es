---
title: getenv, _wgetenv
ms.date: 11/04/2016
api_name:
- getenv
- _wgetenv
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
ms.openlocfilehash: 7cacd8588bcc74c6d064da370ce6254aada56c12
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955059"
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

*varname*<br/>
Nombre de la variable de entorno.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la entrada de la tabla de entorno que contiene *varname*. No es seguro modificar el valor de la variable de entorno con el puntero devuelto. Utilice la función [_putenv](putenv-wputenv.md) para modificar el valor de una variable de entorno. El valor devuelto es **null** si *varname* no se encuentra en la tabla de entorno.

## <a name="remarks"></a>Comentarios

La función **getenv** busca la lista de variables de entorno para *varname*. **getenv** no distingue entre mayúsculas y minúsculas en el sistema operativo Windows. **getenv** y **_putenv** usan la copia del entorno al que apunta la variable global **_environ** para tener acceso al entorno. **getenv** solo funciona en las estructuras de datos a las que puede tener acceso la biblioteca en tiempo de ejecución y no en el "segmento" del entorno que el sistema operativo crea para el proceso. Por lo tanto, los programas que usan el argumento *envp* en [Main](../../cpp/main-program-startup.md) o [wmain](../../cpp/main-program-startup.md) pueden recuperar información no válida.

Si *varname* es **null**, esta función invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve **null**.

**_wgetenv** es una versión con caracteres anchos de **getenv**; el argumento y el valor devuelto de **_wgetenv** son cadenas de caracteres anchos. La variable global **_wenviron** es una versión con caracteres anchos de **_environ**.

En un programa MBCS (por ejemplo, en un programa de ANSI de SBCS), **_wenviron** inicialmente es **null** porque el entorno se compone de cadenas de caracteres multibyte. A continuación, en la primera llamada a [_wputenv](putenv-wputenv.md), o en la primera llamada a **_wgetenv** si ya existe un entorno (MBCS), se crea un entorno de cadena de caracteres anchos correspondiente, al que apunta **_wenviron**.

De forma similar en un programa de Unicode ( **_wmain**), **_Environ** es inicialmente **null** porque el entorno se compone de cadenas de caracteres anchos. Después, en la primera llamada a **_putenv**, o en la primera llamada a **getenv** si ya existe un entorno (Unicode), se crea un entorno de MBCS correspondiente y, a continuación, **_environ**apunta a él.

Si dos copias del entorno (MBCS y Unicode) existen simultáneamente en un programa, el sistema en tiempo de ejecución debe mantener las dos copias, lo que ralentiza el tiempo de ejecución. Por ejemplo, cada vez que llame a **_putenv**, también se ejecuta automáticamente una llamada a **_wputenv** , de modo que se correspondan las dos cadenas de entorno.

> [!CAUTION]
> En raras ocasiones, cuando el sistema en tiempo de ejecución mantiene una versión Unicode y una versión multibyte del entorno, las dos versiones del entorno podrían no corresponderse exactamente. La razón es que, aunque cualquier cadena de caracteres multibyte se asigna a una cadena de Unicode única, la asignación de una cadena de Unicode única a una cadena de caracteres multibyte no es necesariamente única. Para obtener más información, vea [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Las familias de funciones **_putenv** y **_getenv** no son seguras para subprocesos. **_getenv** podría devolver un puntero de cadena mientras **_putenv** está modificando la cadena, lo que provoca errores aleatorios. Asegúrese de que las llamadas a estas funciones están sincronizadas.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv**|**getenv**|**getenv**|**_wgetenv**|

Para comprobar o cambiar el valor de la variable de entorno **TZ** , use **getenv**, **_putenv** y **_tzset** según sea necesario. Para obtener más información sobre **TZ**, vea [_tzset](tzset.md) y [_daylight, timezone y _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

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
