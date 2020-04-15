---
title: _fullpath, _wfullpath
ms.date: 4/2/2020
api_name:
- _fullpath
- _wfullpath
- _o__fullpath
- _o__wfullpath
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wfullpath
- fullpath
- _wfullpath
- _fullpath
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
ms.openlocfilehash: 0910cf4f39e00be84e683cd6f3b9afbeb3f2a749
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345484"
---
# <a name="_fullpath-_wfullpath"></a>_fullpath, _wfullpath

Crea un nombre de ruta de acceso absoluta o completa para el nombre de ruta de acceso relativa especificado.

## <a name="syntax"></a>Sintaxis

```C
char *_fullpath(
   char *absPath,
   const char *relPath,
   size_t maxLength
);
wchar_t *_wfullpath(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength
);
```

### <a name="parameters"></a>Parámetros

*absPath*<br/>
Puntero a un búfer que contiene el nombre de ruta de acceso absoluto o completo, o **NULL**.

*relPath*<br/>
Nombre de ruta de acceso relativa.

*maxLength*<br/>
Longitud máxima del búfer de nombre de ruta de acceso absoluto (*absPath*). Esta longitud está en bytes para **_fullpath** pero en caracteres anchos **(wchar_t**) para **_wfullpath**.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero a un búfer que contiene el nombre de ruta de acceso absoluta (*absPath*). Si hay un error (por ejemplo, si el valor pasado en *relPath* incluye una letra de unidad que no es válida o no se puede encontrar, o si la longitud del nombre de ruta de acceso absoluto creado (*absPath*) es mayor que *maxLength*), la función devuelve **NULL**.

## <a name="remarks"></a>Observaciones

La función **_fullpath** expande el nombre de ruta de acceso relativo en *relPath* a su ruta de acceso completa o absoluta y almacena este nombre en *absPath*. Si *absPath* es **NULL**, **malloc** se utiliza para asignar un búfer de longitud suficiente para contener el nombre de la ruta de acceso. Es responsabilidad del autor de llamada liberar este búfer. Un nombre de ruta de acceso relativa especifica una ruta de acceso a otra ubicación desde la ubicación actual (como el directorio de trabajo actual: "."). Un nombre de ruta de acceso absoluta es la expansión de un nombre de ruta de acceso relativa que indica toda la ruta de acceso necesaria para llegar a la ubicación que se quiere desde la raíz del sistema de archivos. A diferencia **de _makepath**, **_fullpath** se puede utilizar para obtener el nombre de ruta de acceso absoluto para rutas de acceso relativas (*relPath*) que incluyen "./" o ".. /" en sus nombres.

Por ejemplo, para usar rutinas en tiempo de ejecución de C, la aplicación debe incluir los archivos de encabezado que contienen las declaraciones de las rutinas. Cada archivo de encabezado incluye una instrucción que hace referencia a la ubicación del archivo de forma relativa (desde el directorio de trabajo de la aplicación):

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <stdlib.h>
```

cuando la ruta de acceso absoluta (ubicación real del sistema de archivos) del archivo podría ser:

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath** controla automáticamente los argumentos de cadena de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso. **_wfullpath** es una versión de caracteres anchos de **_fullpath;** los argumentos de cadena que **se _wfullpath** son cadenas de caracteres anchos. **_wfullpath** y _fullpath se comportan **de** forma idéntica, excepto que **_wfullpath** no controla cadenas de caracteres multibyte.

Si se definen **_DEBUG** y **_CRTDBG_MAP_ALLOC,** las llamadas a **_fullpath** y **_wfullpath** se reemplazan por llamadas a **_fullpath_dbg** y **_wfullpath_dbg** para permitir la depuración de asignaciones de memoria. Para obtener más información, consulte [_fullpath_dbg, _wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md).

Esta función invoca el controlador de parámetros no válidos, como se describe en [validación](../../c-runtime-library/parameter-validation.md)de parámetros , si *maxlen* es menor o igual que 0. Si la ejecución puede continuar, esta función establece **errno en** **EINVAL** y devuelve **NULL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

Si el búfer *absPath* es **NULL**, **_fullpath** llama a [malloc](malloc.md) para asignar un búfer e ignora el argumento *maxLength.* Es responsabilidad del autor de la llamada desasignar este búfer (mediante [free](free.md)) según corresponda. Si el argumento *relPath* especifica una unidad de disco, el directorio actual de esta unidad se combina con la ruta de acceso.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fullpath.c
// This program demonstrates how _fullpath
// creates a full path from a partial path.

#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
#include <direct.h>

void PrintFullPath( char * partialPath )
{
   char full[_MAX_PATH];
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )
      printf( "Full path is: %s\n", full );
   else
      printf( "Invalid path\n" );
}

int main( void )
{
   PrintFullPath( "test" );
   PrintFullPath( "\\test" );
   PrintFullPath( "..\\test" );
}
```

```Output
Full path is: C:\Documents and Settings\user\My Documents\test
Full path is: C:\test
Full path is: C:\Documents and Settings\user\test
```

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
