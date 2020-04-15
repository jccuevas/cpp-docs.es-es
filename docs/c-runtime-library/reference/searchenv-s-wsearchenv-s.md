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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 3d526c546e1496b3b13b14a12c9025cbd0347cd2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332402"
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

*Nombre*<br/>
Nombre del archivo que se va a buscar.

*Varname*<br/>
Entorno en el que se va a buscar.

*Ruta*<br/>
Búfer en el que se va a almacenar la ruta de acceso completa.

*numberOfElements*<br/>
Tamaño del búfer *pathname.*

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

Si *filename* es una cadena vacía, el valor devuelto es **ENOENT**.

### <a name="error-conditions"></a>Condiciones de error

|*Nombre*|*Varname*|*Ruta*|*numberOfElements*|Valor devuelto|Contenido del nombre de *ruta*|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|cualquiera|cualquiera|**Null**|cualquiera|**EINVAL**|N/D|
|**Null**|cualquiera|cualquiera|cualquiera|**EINVAL**|no cambia|
|cualquiera|cualquiera|cualquiera|<= 0|**EINVAL**|no cambia|

Si se da alguna de estas condiciones de error, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno en** **EINVAL** y devuelven **EINVAL**.

## <a name="remarks"></a>Observaciones

El **_searchenv_s** busca el archivo de destino en el dominio especificado. La variable *varname* puede ser cualquier entorno o variable definida por el usuario que especifique una lista de rutas de directorio, como **PATH**, **LIB**e **INCLUDE**. Dado que **_searchenv_s** distingue mayúsculas de minúsculas, *varname* debe coincidir con el caso de la variable de entorno. Si *varname* no coincide con el nombre de una variable de entorno definida en el entorno del proceso, la función devuelve cero y la variable *pathname* no cambia.

La rutina busca el archivo primero en el directorio de trabajo actual. Si no encuentra el archivo, busca en los directorios especificados por la variable de entorno. Si el archivo de destino está en uno de esos directorios, la ruta de acceso recién creada se copia en *pathname*. Si no se encuentra el archivo de nombre de *archivo,* *pathname* contiene una cadena vacía terminada en null.

El búfer *pathname* debe tener al menos **_MAX_PATH** caracteres de longitud para dar cabida a la longitud completa del nombre de ruta de acceso construido. De lo contrario, **_searchenv_s** podría invadición del búfer *pathname,* lo que provocará un comportamiento inesperado.

**_wsearchenv_s** es una versión de caracteres anchos de **_searchenv_s;** los argumentos para **_wsearchenv_s** son cadenas de caracteres anchos. **_wsearchenv_s** y _searchenv_s comportarse **de** forma idéntica de lo contrario.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

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
