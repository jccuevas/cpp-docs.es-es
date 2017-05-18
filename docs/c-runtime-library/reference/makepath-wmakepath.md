---
title: _makepath, _wmakepath | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: deb4333b36bf0b3eb2080d838ef3f23a052cf262
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="makepath-wmakepath"></a>_makepath, _wmakepath
Cree un nombre de ruta de acceso desde componentes. Hay disponibles versiones más seguras de estas funciones; vea [_makepath_s, _wmakepath_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
#### <a name="parameters"></a>Parámetros  
 `path`  
 Búfer de la ruta de acceso completa.  
  
 `drive`  
 Contiene una letra (A, B, etc.) correspondiente a la unidad deseada y un signo de dos puntos final opcional. Si no están, `_makepath` inserta los dos puntos automáticamente en la ruta de acceso compuesta. Si `drive` es `NULL` o apunta a una cadena vacía, no aparecerá ninguna letra de unidad en la cadena compuesta `path`.  
  
 `dir`  
 Contiene la ruta de acceso de los directorios, sin incluir el designador de unidad ni el nombre de archivo real. La barra diagonal final es opcional, y en un argumento `dir` se puede usar tanto una barra diagonal (/) como una barra diagonal inversa (\\), o ambos. Si no se especifica ninguna barra diagonal (/ o \\), se inserta automáticamente. Si `dir` es `NULL` o apunta a una cadena vacía, no se insertará ninguna ruta de acceso de directorio en la cadena compuesta `path`.  
  
 `fname`  
 Contiene el nombre de archivo base sin ninguna extensión de nombre de archivo. Si `fname` es `NULL` o apunta a una cadena vacía, no se insertará ningún nombre de archivo en la cadena compuesta `path`.  
  
 `ext`  
 Contiene la extensión de nombre de archivo real, con o sin punto inicial (.). `_makepath` inserta el punto automáticamente si no aparece en `ext`. Si `ext` es `NULL` o apunta a una cadena vacía, no se insertará ninguna extensión en la cadena compuesta `path`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_makepath` crea una cadena de ruta de acceso compuesta a partir de componentes determinados y almacena el resultado en `path`. `path` puede incluir una letra de unidad, una ruta de directorio, el nombre de archivo y la extensión. `_wmakepath` es una versión con caracteres anchos de `_makepath`; los argumentos a `_wmakepath` son cadenas de caracteres anchos. Por lo demás, `_wmakepath` y `_makepath` se comportan de forma idéntica.  
  
 **Nota de seguridad** Use una cadena terminada en un valor nulo. Para evitar la saturación del búfer, el tamaño de la cadena terminada en un valor nulo no debe ser mayor que el del búfer `path`. `_makepath` no se asegura de que la longitud de la cadena de la ruta de acceso compuesta no supere `_MAX_PATH`. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmakepath`|`_makepath`|`_makepath`|`_wmakepath`|  
  
 El argumento `path` debe apuntar a un búfer vacío suficientemente grande para incluir la ruta de acceso completa. La `path` compuesta no debe ser mayor que la constante `_MAX_PATH`, definida en Stdlib.h.  
  
 Si la ruta de acceso es `NULL`, se invoca el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Además, `errno` está establecido en `EINVAL`. Los valores `NULL` están permitidos para los demás parámetros.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_makepath`|\<stdlib.h>|  
|`_wmakepath`|\<stdlib.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
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
   printf( "  Drive: %s\n", drive );  
   printf( "  Dir: %s\n", dir );  
   printf( "  Filename: %s\n", fname );  
   printf( "  Ext: %s\n", ext );  
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
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [_fullpath, _wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_splitpath, _wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [_makepath_s, _wmakepath_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)
