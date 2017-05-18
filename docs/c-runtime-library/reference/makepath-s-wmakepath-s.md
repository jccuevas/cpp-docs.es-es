---
title: _makepath_s, _wmakepath_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 0d3ac02a0ac8dfa7f681c8585be7e1b6f41f0f82
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="makepaths-wmakepaths"></a>_makepath_s, _wmakepath_s
Crea un nombre de ruta de acceso de los componentes. Estas son versiones de [_makepath, _wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
#### <a name="parameters"></a>Parámetros  
 [out] `path`  
 Búfer de la ruta de acceso completa.  
  
 [in] `sizeInWords`  
 Tamaño del búfer en palabras.  
  
 [in] `sizeInBytes`  
 Tamaño del búfer en bytes.  
  
 [in] `drive`  
 Contiene una letra (A, B, etc.) correspondiente a la unidad deseada y un signo de dos puntos final opcional. Si no están, `_makepath_s` inserta los dos puntos automáticamente en la ruta de acceso compuesta. Si `drive` es `NULL` o apunta a una cadena vacía, no aparecerá ninguna letra de unidad en la cadena compuesta `path`.  
  
 [in] `dir`  
 Contiene la ruta de acceso de los directorios, sin incluir el designador de unidad ni el nombre de archivo real. La barra diagonal final es opcional, y en un argumento `dir` se puede usar tanto una barra diagonal (/) como una barra diagonal inversa (\\), o ambos. Si no se especifica ninguna barra diagonal (/ o \\), se inserta automáticamente. Si `dir` es `NULL` o apunta a una cadena vacía, no se insertará ninguna ruta de acceso de directorio en la cadena compuesta `path`.  
  
 [in] `fname`  
 Contiene el nombre de archivo base sin ninguna extensión de nombre de archivo. Si `fname` es `NULL` o apunta a una cadena vacía, no se insertará ningún nombre de archivo en la cadena compuesta `path`.  
  
 [in] `ext`  
 Contiene la extensión de nombre de archivo real, con o sin punto inicial (.). `_makepath_s` inserta el punto automáticamente si no aparece en `ext`. Si `ext` es `NULL` o apunta a una cadena vacía, no se insertará ninguna extensión en la cadena compuesta `path`.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`path`|`sizeInWords` / `sizeInBytes`|Volver|Contenido de `path`|  
|------------|------------------------------------|------------|------------------------|  
|`NULL`|cualquiera|`EINVAL`|no modificado|  
|any|<= 0|`EINVAL`|no modificado|  
  
 Si se produce alguna de las condiciones de error anteriores, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `EINVAL`. `NULL` está admitido para los parámetros `drive`, `fname` y `ext`. Para obtener información sobre el comportamiento que se produce cuando estos parámetros son punteros nulos o cadenas vacías, vea la sección Comentarios.  
  
## <a name="remarks"></a>Comentarios  
 La función `_makepath_s` crea una cadena de ruta de acceso compuesta a partir de componentes determinados y almacena el resultado en `path`. `path` puede incluir una letra de unidad, una ruta de directorio, el nombre de archivo y la extensión. `_wmakepath_s` es una versión con caracteres anchos de `_makepath_s`; los argumentos a `_wmakepath_s` son cadenas de caracteres anchos. Por lo demás, `_wmakepath_s` y `_makepath_s` se comportan de forma idéntica.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmakepath_s`|`_makepath_s`|`_makepath_s`|`_wmakepath_s`|  
  
 El argumento `path` debe apuntar a un búfer vacío suficientemente grande para incluir la ruta de acceso completa. La `path` compuesta no debe ser mayor que la constante `_MAX_PATH`, definida en Stdlib.h.  
  
 Si la ruta de acceso es `NULL`, se invoca el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Además, `errno` está establecido en `EINVAL`. Los valores `NULL` están permitidos para los demás parámetros.  
  
 En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
 Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_makepath_s`|\<stdlib.h>|  
|`_wmakepath_s`|\<stdlib.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
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
   printf( "  Drive: %s\n", drive );  
   printf( "  Dir: %s\n", dir );  
   printf( "  Filename: %s\n", fname );  
   printf( "  Ext: %s\n", ext );  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c  
  
Path extracted with _splitpath_s:  
  Drive: c:  
  Dir: \sample\crt\  
  Filename: crt_makepath_s  
  Ext: .c  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [_fullpath, _wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_splitpath_s, _wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)   
 [_makepath, _wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)
