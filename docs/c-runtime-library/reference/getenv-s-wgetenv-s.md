---
title: getenv_s, _wgetenv_s
description: Describe la biblioteca getenv_s en tiempo de ejecución _wgetenv_s de Microsoft C y las funciones.
ms.date: 4/2/2020
api_name:
- getenv_s
- _wgetenv_s
- _o__wgetenv_s
- _o_getenv_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- getenv_s
- _tgetenv_s
- _wgetenv_s
helpviewer_keywords:
- _tgetenv_s function
- wgetenv_s function
- _wgetenv_s function
- getenv_s function
- environment variables
- tgetenv_s function
ms.assetid: c3ae1ffe-d4cd-4bae-bcb1-3afa754c613a
no-loc:
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
ms.openlocfilehash: 0713ed5735916c31edaab1a178a5e9b1b7cf5377
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913681"
---
# <a name="getenv_s-_wgetenv_s"></a>getenv_s, _wgetenv_s

Obtiene un valor del entorno actual. Estas versiones de [getenv, _wgetenv](getenv-wgetenv.md) incluyen mejoras de seguridad, tal como se describe en [Características de seguridad en CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t getenv_s(
   size_t *pReturnValue,
   char* buffer,
   size_t numberOfElements,
   const char *varname
);
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *varname
);
template <size_t size>
errno_t getenv_s(
   size_t *pReturnValue,
   char (&buffer)[size],
   const char *varname
); // C++ only
template <size_t size>
errno_t _wgetenv_s(
   size_t *pReturnValue,
   wchar_t (&buffer)[size],
   const wchar_t *varname
); // C++ only
```

### <a name="parameters"></a>Parámetros

*pReturnValue*<br/>
El tamaño del búfer necesario o 0 si no se encuentra la variable.

*búfer*<br/>
El búfer para almacenar el valor de la variable de entorno.

*numberOfElements*<br/>
Tamaño del *búfer*.

*insertar*<br/>
Nombre de la variable de entorno.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto; en caso contrario, un código de error si se produce un error.

### <a name="error-conditions"></a>Condiciones de error

|*pReturnValue*|*búfer*|*numberOfElements*|*insertar*|Valor devuelto|
|--------------------|--------------|------------------------|---------------|------------------|
|**ACEPTA**|cualquiera|cualquiera|cualquiera|**EINVAL**|
|cualquiera|**ACEPTA**|>0|cualquiera|**EINVAL**|
|cualquiera|cualquiera|cualquiera|**ACEPTA**|**EINVAL**|

Cualquiera de estas condiciones de error invoca un controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones establecen **errno** en **EINVAL** y devuelven **EINVAL**.

Además, si el búfer es demasiado pequeño, estas funciones devuelven **ERANGE**. No invocan un controlador de parámetros no válido. Escriben el tamaño de búfer necesario en *pReturnValue*y, por tanto, permiten que los programas llamen de nuevo a la función con un búfer mayor.

## <a name="remarks"></a>Observaciones

La función **getenv_s** busca la lista de variables de entorno para *varname*. **getenv_s** no distingue entre mayúsculas y minúsculas en el sistema operativo Windows. **getenv_s** y [_putenv_s](putenv-s-wputenv-s.md) usar la copia del entorno a la que apunta la variable global **_environ** para tener acceso al entorno. **getenv_s** solo funciona en las estructuras de datos a las que puede tener acceso la biblioteca en tiempo de ejecución y no en el "segmento" del entorno que el sistema operativo crea para el proceso. Por lo tanto, los programas que usan el argumento *envp* en [Main](../../cpp/main-function-command-line-args.md) o [wmain](../../cpp/main-function-command-line-args.md) podrían recuperar información no válida.

**_wgetenv_s** es una versión con caracteres anchos de **getenv_s**; el argumento y el valor devuelto de **_wgetenv_s** son cadenas de caracteres anchos. La variable global **_wenviron** es una versión con caracteres anchos de **_environ**.

En un programa MBCS (por ejemplo, en un programa de ASCII de SBCS), **_wenviron** inicialmente es **null** porque el entorno se compone de cadenas de caracteres multibyte. Después, en la primera llamada a [_wputenv](putenv-wputenv.md), o en la primera llamada a **_wgetenv_s**, si ya existe un entorno (MBCS), se crea un entorno de cadena de caracteres anchos correspondiente y, a continuación, se señala mediante **_wenviron**.

De forma similar en un programa de Unicode (**_wmain**), **_Environ** es inicialmente **null** porque el entorno se compone de cadenas de caracteres anchos. Después, en la primera llamada a [_putenv](putenv-wputenv.md), o en la primera llamada a **getenv_s** si ya existe un entorno (Unicode), se crea un entorno de MBCS correspondiente y, a continuación, se señala mediante **_environ**.

Si dos copias del entorno (MBCS y Unicode) existen simultáneamente en un programa, el sistema en tiempo de ejecución debe mantener las dos copias, lo que ralentiza el tiempo de ejecución. Por ejemplo, al llamar a **_putenv**, también se ejecuta automáticamente una llamada a **_wputenv** para que se correspondan las dos cadenas de entorno.

> [!CAUTION]
> En raras ocasiones, cuando el sistema en tiempo de ejecución mantiene una versión Unicode y una versión multibyte del entorno, las dos versiones del entorno podrían no corresponderse exactamente. La razón es que, aunque cualquier cadena de caracteres multibyte se asigna a una cadena de Unicode única, la asignación de una cadena de Unicode única a una cadena de caracteres multibyte no es necesariamente única. Para obtener más información, vea [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Las familias de funciones de **_putenv_s** y **_getenv_s** no son seguras para subprocesos. **_getenv_s** podría devolver un puntero de cadena mientras **_putenv_s** modifica la cadena y, por tanto, se producen errores aleatorios. Asegúrese de que las llamadas a estas funciones están sincronizadas.

En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir automáticamente la longitud del búfer, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tgetenv_s**|**getenv_s**|**getenv_s**|**_wgetenv_s**|

Para comprobar o cambiar el valor de la variable de entorno **TZ** , use **getenv_s**, **_putenv**y **_tzset**, según sea necesario. Para obtener más información sobre **TZ**, vea [_tzset](tzset.md) y [_daylight, _dstbias, _timezone y _tzname](../../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**getenv_s**|\<stdlib.h>|
|**_wgetenv_s**|\<stdlib.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_getenv_s.c
// This program uses getenv_s to retrieve
// the LIB environment variable and then uses
// _putenv to change it to a new value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* libvar;
   size_t requiredSize;

   getenv_s( &requiredSize, NULL, 0, "LIB");
   if (requiredSize == 0)
   {
      printf("LIB doesn't exist!\n");
      exit(1);
   }

   libvar = (char*) malloc(requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "Original LIB variable is: %s\n", libvar );

   // Attempt to change path. Note that this only affects
   // the environment variable of the current process. The command
   // processor's environment is not changed.
   _putenv_s( "LIB", "c:\\mylib;c:\\yourlib" );

   getenv_s( &requiredSize, NULL, 0, "LIB");

   libvar = (char*) realloc(libvar, requiredSize * sizeof(char));
   if (!libvar)
   {
      printf("Failed to allocate memory!\n");
      exit(1);
   }

   // Get the new value of the LIB environment variable.
   getenv_s( &requiredSize, libvar, requiredSize, "LIB" );

   printf( "New LIB variable is: %s\n", libvar );

   free(libvar);
}
```

```Output
Original LIB variable is: c:\vctools\lib;c:\vctools\atlmfc\lib;c:\vctools\PlatformSDK\lib;c:\vctools\Visual Studio SDKs\DIA Sdk\lib;c:\vctools\Visual Studio SDKs\BSC Sdk\lib
New LIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Consulte también

[Control de proceso y entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[Constantes de entorno](../../c-runtime-library/environmental-constants.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_dupenv_s, _wdupenv_s](dupenv-s-wdupenv-s.md)<br/>
