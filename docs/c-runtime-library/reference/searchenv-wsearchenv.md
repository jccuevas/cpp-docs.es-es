---
title: _searchenv, _wsearchenv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _searchenv
- _wsearchenv
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
- _wsearchenv
- _tsearchenv
- wsearchenv
- _searchenv
- searchenv
dev_langs:
- C++
helpviewer_keywords:
- _wsearchenv function
- files [C++], finding
- _searchenv function
- tsearchenv function
- environment paths, searching for files
- _tsearchenv function
- wsearchenv function
- searchenv function
- environment paths
ms.assetid: 9c944a27-d326-409b-aee6-410e8762d9d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62e0fea9154801f850640234355af53dc1154160
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="searchenv-wsearchenv"></a>_searchenv, _wsearchenv

Usa las rutas de acceso de entorno para buscar un archivo. Hay disponibles versiones más seguras de estas funciones; vea [_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
void _searchenv(
   const char *filename,
   const char *varname,
   char *pathname
);
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname
);
template <size_t size>
void _searchenv(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t (&pathname)[size]
); // C++ only
```

### <a name="parameters"></a>Parámetros

*nombre de archivo* nombre del archivo que se buscará.

*VarName* entorno para buscar.

*ruta de acceso* búfer para almacenar la ruta de acceso completa.

## <a name="remarks"></a>Comentarios

El **_searchenv** búsquedas rutinarias para el archivo de destino en el dominio especificado. El *varname* variable puede ser cualquier variable definida por el usuario o el entorno, por ejemplo, **ruta de acceso**, **LIB**, o **INCLUDE**, que especifica un lista de rutas de acceso de directorio. Dado que **_searchenv** distingue mayúsculas de minúsculas, *varname* debe coincidir con el caso de la variable de entorno.

En primer lugar, la rutina busca el archivo en el directorio de trabajo actual. Si no lo encuentra aquí, lo busca en los directorios que especifica la variable de entorno. Si el archivo de destino está en uno de esos directorios, la ruta de acceso creada recientemente se copia en *pathname*. Si el *filename* no se encuentra el archivo, *pathname* contiene una cadena vacía terminada en null.

El *pathname* búfer debe ser al menos **_MAX_PATH** caracteres de longitud para dar cabida a la longitud total del nombre de ruta de acceso construido. En caso contrario, **_searchenv** puede saturar el *pathname* almacene en búfer y provocar un comportamiento inesperado.

**_wsearchenv** es una versión con caracteres anchos de **_searchenv**y los argumentos para **_wsearchenv** son cadenas de caracteres anchos. **_wsearchenv** y **_searchenv** se comportan exactamente igual.

Si *filename* es una cadena vacía, estas funciones devuelven **ENOENT**.

Si *filename* o *pathname* es un **NULL** se invoca el puntero, el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establecen **errno** a **EINVAL**.

Para obtener más información acerca de **errno** y códigos de error, vea [errno constantes](../../c-runtime-library/errno-constants.md).

En C++, estas funciones tienen sobrecargas de plantilla que invocan a los homólogos más recientes y seguros de dichas funciones. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_searchenv.c
// compile with: /W3
// This program searches for a file in
// a directory that's specified by an environment variable.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";

   // Search for file in PATH environment variable:
   _searchenv( searchfile, envvar, pathbuffer ); // C4996
   // Note: _searchenv is deprecated; consider using _searchenv_s
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 8\VC\BIN\CL.EXE
```

## <a name="see-also"></a>Vea también

[Control de directorio](../../c-runtime-library/directory-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_putenv, _wputenv](putenv-wputenv.md)<br/>
[_searchenv_s, _wsearchenv_s](searchenv-s-wsearchenv-s.md)<br/>
