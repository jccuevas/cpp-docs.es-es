---
title: _makepath, _wmakepath
ms.date: 11/04/2016
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
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
ms.openlocfilehash: fab53d70df1c5361bc56bc0df16d0d2171f07a94
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499912"
---
# <a name="_makepath-_wmakepath"></a>_makepath, _wmakepath

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

*drive*<br/>
Contiene una letra (A, B, etc.) correspondiente a la unidad deseada y un signo de dos puntos final opcional. **_makepath** inserta los dos puntos automáticamente en la ruta de acceso compuesta si falta. Si la *unidad* es **null** o apunta a una cadena vacía, no aparece ninguna letra de unidad en la cadena de *ruta de acceso* compuesta.

*dir*<br/>
Contiene la ruta de acceso de los directorios, sin incluir el designador de unidad ni el nombre de archivo real. La barra diagonal final es opcional y se puede usar una barra diagonal (/) o una barra diagonal\\inversa (), o ambas, en un solo argumento *dir* . Si no se especifica ninguna barra diagonal (/ o \\), se inserta automáticamente. Si *dir* es **null** o apunta a una cadena vacía, no se insertará ninguna ruta de acceso de directorio en la cadena de *ruta de acceso* compuesta.

*fname*<br/>
Contiene el nombre de archivo base sin ninguna extensión de nombre de archivo. Si *fname* es **null** o apunta a una cadena vacía, no se inserta ningún nombre de archivo en la cadena de *ruta de acceso* compuesta.

*ext*<br/>
Contiene la extensión de nombre de archivo real, con o sin punto inicial (.). **_makepath** inserta el período automáticamente si no aparece en *ext*. Si *ext* es **null** o apunta a una cadena vacía, no se inserta ninguna extensión en la cadena de *ruta de acceso* compuesta.

## <a name="remarks"></a>Comentarios

La función **_makepath** crea una cadena de ruta de acceso compuesta a partir de componentes individuales y almacena el resultado en la *ruta de acceso*. La *ruta de acceso* puede incluir una letra de unidad, una ruta de directorio, un nombre de archivo y una extensión de nombre de archivo. **_wmakepath** es una versión con caracteres anchos de **_makepath**; los argumentos de **_wmakepath** son cadenas de caracteres anchos. **_wmakepath** y **_makepath** se comportan de manera idéntica.

**Nota de seguridad** Use una cadena terminada en nulo. Para evitar la saturación del búfer, la cadena terminada en NULL no debe superar el tamaño del búfer de *ruta de acceso* . **_makepath** no garantiza que la longitud de la cadena de ruta de acceso compuesta no supere el valor de _ **MAX_PATH**. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

El argumento *path* debe apuntar a un búfer vacío lo suficientemente grande como para contener la ruta de acceso completa. La *ruta de acceso* compuesta no debe ser mayor que la constante _ **MAX_PATH** , definida en stdlib. h.

Si path es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Además, **errno** se establece en **EINVAL**. Se permiten valores **null** para todos los demás parámetros.

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
