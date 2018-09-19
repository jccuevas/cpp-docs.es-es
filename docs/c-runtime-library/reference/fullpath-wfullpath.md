---
title: _fullpath, _wfullpath | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fullpath
- _wfullpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wfullpath
- fullpath
- _wfullpath
- _fullpath
dev_langs:
- C++
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b472987b0cac41c57e5fd22b2eedecef522613b4
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451685"
---
# <a name="fullpath-wfullpath"></a>_fullpath, _wfullpath

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
Puntero a un búfer que contiene el nombre de ruta de acceso absoluta o completa, o **NULL**.

*relPath*<br/>
Nombre de ruta de acceso relativa.

*maxLength*<br/>
Longitud máxima del búfer de nombre de ruta de acceso absoluta (*absPath*). Esta longitud se muestra en bytes para **_fullpath** y en caracteres anchos (**wchar_t**) para **_wfullpath**.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero a un búfer que contiene el nombre de ruta de acceso absoluta (*absPath*). Si se produce un error (por ejemplo, si el valor pasado en *relPath* incluye una letra de unidad que no es válido o no se encuentra, o si la longitud del nombre de ruta de acceso absoluta creado (*absPath*) es mayor que *maxLength*), la función devuelve **NULL**.

## <a name="remarks"></a>Comentarios

El **_fullpath** función expande el nombre de ruta de acceso relativa en *relPath* a su ruta de acceso completa o absoluta y almacena este nombre en *absPath*. Si *absPath* es **NULL**, **malloc** se utiliza para asignar un búfer de longitud suficiente para contener el nombre de ruta de acceso. Es responsabilidad del autor de llamada liberar este búfer. Un nombre de ruta de acceso relativa especifica una ruta de acceso a otra ubicación desde la ubicación actual (como el directorio de trabajo actual: "."). Un nombre de ruta de acceso absoluta es la expansión de un nombre de ruta de acceso relativa que indica toda la ruta de acceso necesaria para llegar a la ubicación que se quiere desde la raíz del sistema de archivos. A diferencia de **_makepath**, **_fullpath** puede utilizarse para obtener el nombre de ruta de acceso absoluta para rutas de acceso relativas (*relPath*) que incluyen ". /"o".. / "en sus nombres.

Por ejemplo, para usar rutinas en tiempo de ejecución de C, la aplicación debe incluir los archivos de encabezado que contienen las declaraciones de las rutinas. Cada archivo de encabezado incluye una instrucción que hace referencia a la ubicación del archivo de forma relativa (desde el directorio de trabajo de la aplicación):

```C
#include <stdlib.h>
```

cuando la ruta de acceso absoluta (ubicación real del sistema de archivos) del archivo podría ser:

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath** controla automáticamente argumentos de cadena de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso. **_wfullpath** es una versión con caracteres anchos de **_fullpath**; los argumentos de cadena para **_wfullpath** son cadenas de caracteres anchos. **_wfullpath** y **_fullpath** se comportan exactamente igual, salvo que **_wfullpath** no controla las cadenas de caracteres multibyte.

Si **_DEBUG** y **_CRTDBG_MAP_ALLOC** son ambos definido, las llamadas a **_fullpath** y **_wfullpath** se reemplazan por llamadas a **_fullpath_dbg** y **_wfullpath_dbg** para permitir que las asignaciones de memoria de depuración. Para obtener más información, consulte [_fullpath_dbg, _wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md).

Esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md)si *maxlen* es menor o igual que 0. Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve **NULL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

Si el *absPath* búfer es **NULL**, **_fullpath** llamadas [malloc](malloc.md) para asignar un búfer y omite la *maxLength*  argumento. Es responsabilidad del autor de la llamada desasignar este búfer (mediante [free](free.md)) según corresponda. Si el *relPath* argumento especifica una unidad de disco, el directorio actual de esta unidad se combina con la ruta de acceso.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
