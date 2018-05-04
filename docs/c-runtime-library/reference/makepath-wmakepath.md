---
title: _makepath, _wmakepath | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _makepath
- _wmakepath
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
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
dev_langs:
- C++
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c339ce6ad67186dc7a4f43d7006c5beb047c8f90
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="makepath-wmakepath"></a>_makepath, _wmakepath

Cree un nombre de ruta de acceso desde componentes. Hay disponibles versiones más seguras de estas funciones; vea [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

## <a name="syntax"></a>Sintaxis

```C
void _makepath(
   char *path,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
void _wmakepath(
   wchar_t *path,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
```

### <a name="parameters"></a>Parámetros

*ruta de acceso* búfer de la ruta de acceso completa.

*unidad* contiene una letra (A, B y así sucesivamente) correspondiente a la unidad deseada y un signo de dos puntos final opcional. **_makepath** inserta automáticamente los dos puntos en la ruta de acceso compuesto si está presente. Si *unidad* es **NULL** o apunta a una cadena vacía, letra de unidad no aparecerá en la composición *ruta de acceso* cadena.

*dir* contiene la ruta de acceso de directorios, sin incluir el designador de unidad o el nombre de archivo real. La barra diagonal final es opcional y una barra diagonal (/) o una barra diagonal inversa (\\) o ambos podrían utilizarse en un único equipo *dir* argumento. Si no se especifica ninguna barra diagonal (/ o \\), se inserta automáticamente. Si *dir* es **NULL** o apunta a una cadena vacía, ninguna ruta de acceso de directorio se ha insertado en la composición *ruta de acceso* cadena.

*fname* contiene el nombre de archivo base sin ninguna extensión de nombre de archivo. Si *fname* es **NULL** o apunta a una cadena vacía, ningún nombre de archivo se ha insertado en la composición *ruta de acceso* cadena.

*ext* contiene la extensión de nombre de archivo real, con o sin un punto (.). **_makepath** inserta automáticamente el período si no aparece en *ext*. Si *ext* es **NULL** o apunta a una cadena vacía, sin extensión se ha insertado en la composición *ruta de acceso* cadena.

## <a name="remarks"></a>Comentarios

El **_makepath** función crea una cadena de ruta de acceso compuestos de componentes individuales, almacenar el resultado en *ruta de acceso*. El *ruta de acceso* podría incluir una letra de unidad, la ruta de acceso del directorio, el nombre de archivo y la extensión de nombre de archivo. **_wmakepath** es una versión con caracteres anchos de **_makepath**; los argumentos a **_wmakepath** son cadenas de caracteres anchos. **_wmakepath** y **_makepath** se comportan exactamente igual.

**Nota de seguridad** Use una cadena terminada en nulo. Para evitar la saturación del búfer, la cadena terminada en null no debe superar el tamaño de la *ruta de acceso* búfer. **_makepath** no se asegura de que no supera la longitud de la cadena de ruta de acceso compuestos **_MAX_PATH**. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

El *ruta de acceso* argumento debe apuntar a un búfer vacío lo suficientemente grande como para contener la ruta de acceso completa. La composición *ruta de acceso* no debe ser mayor que el **_MAX_PATH** constante, definida en Stdlib.h.

Si la ruta de acceso es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Además, **errno** está establecido en **EINVAL**. **NULL** se permiten valores para todos los demás parámetros.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_makepath.c
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];

   _makepath( path_buffer, "c", "\\sample\\crt\\", "makepath", "c" ); // C4996
   // Note: _makepath is deprecated; consider using _makepath_s instead
   printf( "Path created with _makepath: %s\n\n", path_buffer );
   _splitpath( path_buffer, drive, dir, fname, ext ); // C4996
   // Note: _splitpath is deprecated; consider using _splitpath_s instead
   printf( "Path extracted with _splitpath:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath: c:\sample\crt\makepath.c

Path extracted with _splitpath:
   Drive: c:
   Dir: \sample\crt\
   Filename: makepath
   Ext: .c
```

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md)<br/>
