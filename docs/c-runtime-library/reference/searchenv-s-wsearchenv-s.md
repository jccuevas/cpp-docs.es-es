---
title: _searchenv_s, _wsearchenv_s
ms.date: 4/2/2020
api_name:
- _wsearchenv_s
- _searchenv_s
- _o__searchenv_s
- _o__wsearchenv_s
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
- _searchenv_s
- _wsearchenv_s
- wsearchenv_s
- searchenv_s
helpviewer_keywords:
- tsearchenv_s function
- files [C++], finding
- buffers [C++], buffer overruns
- environment paths, searching for files
- wsearchenv_s function
- searchenv_s function
- _tsearchenv_s function
- buffer overruns
- buffers [C++], avoiding overruns
- _wsearchenv_s function
- _searchenv_s function
- environment paths
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
ms.openlocfilehash: 5dd21013c8910ba07e2d23606af49bc80458dbc6
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918995"
---
# <a name="_searchenv_s-_wsearchenv_s"></a>_searchenv_s, _wsearchenv_s

Busca un archivo mediante rutas de acceso del entorno. Estas versiones de [_searchenv, _wsearchenv](searchenv-wsearchenv.md) incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char *pathname,
   size_t numberOfElements
);
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname,
   size_t numberOfElements
);
template <size_t size>
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t (&pathname)[size]
); // C++ only
```

### <a name="parameters"></a>Parámetros

*extensión*<br/>
Nombre del archivo que se va a buscar.

*insertar*<br/>
Entorno en el que se va a buscar.

*Ruta*<br/>
Búfer en el que se va a almacenar la ruta de acceso completa.

*numberOfElements*<br/>
Tamaño del búfer de *ruta de directorio* .

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

Si *filename* es una cadena vacía, el valor devuelto es **ENOENT**.

### <a name="error-conditions"></a>Condiciones de error

|*extensión*|*insertar*|*Ruta*|*numberOfElements*|Valor devuelto|Contenido de *PathName*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|cualquiera|cualquiera|**ACEPTA**|cualquiera|**EINVAL**|N/D|
|**ACEPTA**|cualquiera|cualquiera|cualquiera|**EINVAL**|no cambia|
|cualquiera|cualquiera|cualquiera|<= 0|**EINVAL**|no cambia|

Si se da alguna de estas condiciones de error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** en **EINVAL** y devuelven **EINVAL**.

## <a name="remarks"></a>Observaciones

La rutina **_searchenv_s** busca el archivo de destino en el dominio especificado. La *variable varname* puede ser cualquier variable de entorno o definida por el usuario que especifique una lista de rutas de **acceso**de directorio, como Path, **lib**e **include**. Dado que **_searchenv_s** distingue entre mayúsculas y minúsculas, *varname* debe coincidir con las mayúsculas y minúsculas de la variable de entorno. Si *varname* no coincide con el nombre de una variable de entorno definida en el entorno del proceso, la función devuelve cero y la variable *PathName* no cambia.

La rutina busca el archivo primero en el directorio de trabajo actual. Si no encuentra el archivo, busca en los directorios especificados por la variable de entorno. Si el archivo de destino se encuentra en uno de esos directorios, la ruta de acceso recién creada se copia en el *directorio*. Si no se encuentra el archivo *filename* , *PathName* contiene una cadena terminada en NULL vacía.

El *búfer del nombre de ruta de* acceso debe tener al menos **_MAX_PATH** caracteres para dar cabida a la longitud total del nombre de ruta de acceso construido. De lo contrario, **_searchenv_s** podría saturar el búfer de *ruta de nombres* , lo que produce un comportamiento inesperado.

**_wsearchenv_s** es una versión con caracteres anchos de **_searchenv_s**; los argumentos para **_wsearchenv_s** son cadenas de caracteres anchos. **_wsearchenv_s** y **_searchenv_s** se comportan de manera idéntica.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_searchenv_s**|\<stdlib.h>|
|**_wsearchenv_s**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_searchenv_s.c
/* This program searches for a file in
* a directory specified by an environment variable.
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";
   errno_t err;

   /* Search for file in PATH environment variable: */
   err = _searchenv_s( searchfile, envvar, pathbuffer, _MAX_PATH );
   if (err != 0)
   {
      printf("Error searching the path. Error code: %d\n", err);
   }
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 2010\VC\BIN\CL.EXE
```

## <a name="see-also"></a>Consulte también

[Control de directorio](../../c-runtime-library/directory-control.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
