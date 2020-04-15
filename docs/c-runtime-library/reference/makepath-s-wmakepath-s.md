---
title: _makepath_s, _wmakepath_s
ms.date: 4/2/2020
api_name:
- _wmakepath_s
- _makepath_s
- _o__makepath_s
- _o__wmakepath_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
ms.openlocfilehash: 3a44651cb9ff8be806c45c6b6c5f41f810319a85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341604"
---
# <a name="_makepath_s-_wmakepath_s"></a>_makepath_s, _wmakepath_s

Crea un nombre de ruta de acceso de los componentes. Estas son versiones de [_makepath, _wmakepath](makepath-wmakepath.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _makepath_s(
   char *path,
   size_t sizeInBytes,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
errno_t _wmakepath_s(
   wchar_t *path,
   size_t sizeInWords,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
template <size_t size>
errno_t _makepath_s(
   char (&path)[size],
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
); // C++ only
template <size_t size>
errno_t _wmakepath_s(
   wchar_t (&path)[size],
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
); // C++ only
```

### <a name="parameters"></a>Parámetros

*path*<br/>
Búfer de la ruta de acceso completa.

*sizeInWords*<br/>
Tamaño del búfer en palabras.

*sizeInBytes*<br/>
Tamaño del búfer en bytes.

*Conducir*<br/>
Contiene una letra (A, B, etc.) correspondiente a la unidad deseada y un signo de dos puntos final opcional. **_makepath_s** inserta los dos puntos automáticamente en la ruta compuesta si falta. Si *la unidad* es **NULL** o apunta a una cadena vacía, no aparece ninguna letra de unidad en la cadena de ruta de *acceso* compuesta.

*dir*<br/>
Contiene la ruta de acceso de los directorios, sin incluir el designador de unidad ni el nombre de archivo real. La barra diagonal final es opcional y se puede utilizar\\una barra diagonal (/) o una barra diagonal inversa ( ) o ambas en un único argumento *dir.* Si no se especifica ninguna barra diagonal (/ o \\), se inserta automáticamente. Si *dir* es **NULL** o apunta a una cadena vacía, no se inserta ninguna ruta de acceso de directorio en la cadena de ruta de *acceso* compuesta.

*apellido*<br/>
Contiene el nombre de archivo base sin ninguna extensión de nombre de archivo. Si *fname* es **NULL** o apunta a una cadena vacía, no se inserta ningún nombre de archivo en la cadena de ruta de *acceso* compuesta.

*Ext*<br/>
Contiene la extensión de nombre de archivo real, con o sin punto inicial (.). **_makepath_s** inserta el período automáticamente si no aparece en *ext*. Si *ext* es **NULL** o apunta a una cadena vacía, no se inserta ninguna extensión en la cadena de ruta de *acceso* compuesta.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

### <a name="error-conditions"></a>Condiciones de error

|*path*|*sizeInWords* / *sizeInBytes*|Valor devuelto|Contenido de la *ruta*|
|------------|------------------------------------|------------|------------------------|
|**Null**|cualquiera|**EINVAL**|no modificado|
|cualquiera|<= 0|**EINVAL**|no modificado|

Si se produce alguna de las condiciones de error anteriores, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece **en EINVAL** y las funciones devuelven **EINVAL**. **SE** permite NULL para la *unidad*de parámetros , *fname*y *ext*. Para obtener información sobre el comportamiento cuando estos parámetros son punteros nulos o cadenas vacías, consulte la sección Comentarios.

## <a name="remarks"></a>Observaciones

La función **_makepath_s** crea una cadena de ruta de acceso compuesta a partir de componentes individuales, almacenando el resultado en la ruta de *acceso.* La ruta de *acceso* puede incluir una letra de unidad, una ruta de acceso de directorio, un nombre de archivo y una extensión de nombre de archivo. **_wmakepath_s** es una versión de caracteres anchos de **_makepath_s;** los argumentos para **_wmakepath_s** son cadenas de caracteres anchos. **_wmakepath_s** y **_makepath_s** comportarse de forma idéntica de lo contrario.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

El argumento *path* debe apuntar a un búfer vacío lo suficientemente grande como para contener la ruta de acceso completa. La *ruta* de acceso compuesta no debe ser mayor que la constante **_MAX_PATH,** definida en Stdlib.h.

Si path es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Además, **errno** se establece **en EINVAL**. Se permiten valores **NULL** para todos los demás parámetros.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

Las versiones de la biblioteca de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_makepath_s.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];
   errno_t err;

   err = _makepath_s( path_buffer, _MAX_PATH, "c", "\\sample\\crt\\",
                      "crt_makepath_s", "c" );
   if (err != 0)
   {
      printf("Error creating path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path created with _makepath_s: %s\n\n", path_buffer );
   err = _splitpath_s( path_buffer, drive, _MAX_DRIVE, dir, _MAX_DIR, fname,
                       _MAX_FNAME, ext, _MAX_EXT );
   if (err != 0)
   {
      printf("Error splitting the path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path extracted with _splitpath_s:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c

Path extracted with _splitpath_s:
   Drive: c:
   Dir: \sample\crt\
   Filename: crt_makepath_s
   Ext: .c
```

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
