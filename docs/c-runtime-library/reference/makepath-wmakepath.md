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
ms.openlocfilehash: 21cfcfb8a1c82fb351b85b0fb169a94dd3c2c5d4
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105099"
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

*path*<br/>
Búfer de la ruta de acceso completa.

*Unidad*<br/>
Contiene una letra (A, B, etc.) correspondiente a la unidad deseada y un signo de dos puntos final opcional. **_makepath** inserta los dos puntos automáticamente en la ruta de acceso compuesta si está presente. Si *unidad* es **NULL** o apunta a una cadena vacía, letra de unidad no aparece en la composición *ruta* cadena.

*dir*<br/>
Contiene la ruta de acceso de los directorios, sin incluir el designador de unidad ni el nombre de archivo real. La barra diagonal final es opcional y una barra diagonal (/) o una barra diagonal inversa (\\) o ambos se pueden utilizar en una sola *dir* argumento. Si no se especifica ninguna barra diagonal (/ o \\), se inserta automáticamente. Si *dir* es **NULL** o apunta a una cadena vacía, no hay ruta de acceso de directorio se insertará en la composición *ruta* cadena.

*fname*<br/>
Contiene el nombre de archivo base sin ninguna extensión de nombre de archivo. Si *fname* es **NULL** o apunta a una cadena vacía, ningún nombre de archivo se insertará en la composición *ruta* cadena.

*ext*<br/>
Contiene la extensión de nombre de archivo real, con o sin punto inicial (.). **_makepath** inserta el punto automáticamente si no aparece en *ext*. Si *ext* es **NULL** o apunta a una cadena vacía, sin extensión se insertará en la composición *ruta* cadena.

## <a name="remarks"></a>Comentarios

El **_makepath** función crea una cadena de ruta de acceso compuesta de componentes determinados y almacena el resultado en *ruta de acceso*. El *ruta* podría incluir una letra de unidad, ruta de acceso de directorio, nombre de archivo y extensión de nombre de archivo. **_wmakepath** es una versión con caracteres anchos de **_makepath**; los argumentos de **_wmakepath** son cadenas de caracteres anchos. **_wmakepath** y **_makepath** se comportan exactamente igual.

**Nota de seguridad** Use una cadena terminada en nulo. Para evitar la saturación del búfer, la cadena terminada en null no puede superar el tamaño de la *ruta* búfer. **_makepath** no garantiza que no supera la longitud de la cadena de ruta de acceso compuesta **_MAX_PATH**. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/desktop/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

El *ruta* argumento debe apuntar a un búfer vacío suficientemente grande para contener la ruta de acceso completa. El compuesto *ruta* debe ser no puede superar el **_MAX_PATH** constante, definida en Stdlib.h.

Si la ruta de acceso es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Además, **errno** está establecido en **EINVAL**. **NULL** se permiten valores para todos los demás parámetros.

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
