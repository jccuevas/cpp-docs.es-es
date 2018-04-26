---
title: _makepath_s, _wmakepath_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wmakepath_s
- _makepath_s
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
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
dev_langs:
- C++
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
caps.latest.revision: 29
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eecae2f0b3b8e3ee81fe83fa3041b81ca219f334
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="makepaths-wmakepaths"></a>_makepath_s, _wmakepath_s

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

*Unidad*<br/>
Contiene una letra (A, B, etc.) correspondiente a la unidad deseada y un signo de dos puntos final opcional. **_makepath_s** inserta automáticamente los dos puntos en la ruta de acceso compuesto si está presente. Si *unidad* es **NULL** o apunta a una cadena vacía, letra de unidad no aparecerá en la composición *ruta de acceso* cadena.

*dir*<br/>
Contiene la ruta de acceso de los directorios, sin incluir el designador de unidad ni el nombre de archivo real. La barra diagonal final es opcional y una barra diagonal (/) o una barra diagonal inversa (\\) o ambos podrían utilizarse en un único equipo *dir* argumento. Si no se especifica ninguna barra diagonal (/ o \\), se inserta automáticamente. Si *dir* es **NULL** o apunta a una cadena vacía, ninguna ruta de acceso de directorio se ha insertado en la composición *ruta de acceso* cadena.

*fname*<br/>
Contiene el nombre de archivo base sin ninguna extensión de nombre de archivo. Si *fname* es **NULL** o apunta a una cadena vacía, ningún nombre de archivo se ha insertado en la composición *ruta de acceso* cadena.

*ext*<br/>
Contiene la extensión de nombre de archivo real, con o sin punto inicial (.). **_makepath_s** inserta automáticamente el período si no aparece en *ext*. Si *ext* es **NULL** o apunta a una cadena vacía, sin extensión se ha insertado en la composición *ruta de acceso* cadena.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

### <a name="error-conditions"></a>Condiciones de error

|*path*|*sizeInWords* / *sizeInBytes*|Volver|Contenido de *ruta de acceso*|
|------------|------------------------------------|------------|------------------------|
|**NULL**|any|**EINVAL**|no modificado|
|any|<= 0|**EINVAL**|no modificado|

Si se produce alguna de las condiciones de error anteriores, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y las funciones devuelven **EINVAL**. **NULL** se permite para los parámetros *unidad*, *fname*, y *ext*. Para obtener información sobre el comportamiento que se produce cuando estos parámetros son punteros nulos o cadenas vacías, vea la sección Comentarios.

## <a name="remarks"></a>Comentarios

El **_makepath_s** función crea una cadena de ruta de acceso compuestos de componentes individuales, almacenar el resultado en *ruta de acceso*. El *ruta de acceso* podría incluir una letra de unidad, la ruta de acceso del directorio, el nombre de archivo y la extensión de nombre de archivo. **_wmakepath_s** es una versión con caracteres anchos de **_makepath_s**; los argumentos a **_wmakepath_s** son cadenas de caracteres anchos. **_wmakepath_s** y **_makepath_s** se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

El *ruta de acceso* argumento debe apuntar a un búfer vacío lo suficientemente grande como para contener la ruta de acceso completa. La composición *ruta de acceso* no debe ser mayor que el **_MAX_PATH** constante, definida en Stdlib.h.

Si la ruta de acceso es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Además, **errno** está establecido en **EINVAL**. **NULL** se permiten valores para todos los demás parámetros.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
