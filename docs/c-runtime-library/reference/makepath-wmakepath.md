---
title: "_makepath, _wmakepath | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_makepath"
  - "_wmakepath"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_wmakepath"
  - "_tmakepath"
  - "makepath"
  - "tmakepath"
  - "wmakepath"
  - "_makepath"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_makepath (función)"
  - "_tmakepath (función)"
  - "_wmakepath (función)"
  - "makepath (función)"
  - "rutas de acceso"
  - "tmakepath (función)"
  - "wmakepath (función)"
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _makepath, _wmakepath
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cree un nombre de ruta de componentes.  Hay disponibles versiones más seguras de estas funciones; vea [\_makepath\_s, \_wmakepath\_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md).  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `path`  
 Búfer de la ruta de acceso completa.  
  
 `drive`  
 Contiene una letra \(A, b, etc.\) correspondiente a la unidad deseada y un signo de dos puntos final opcional.  `_makepath` inserta el dos puntos automáticamente en la ruta compuesta si falta.  Si `drive` es `NULL` o puntos en una cadena vacía, ninguna letra de unidad aparece en la cadena compuesta de `path` .  
  
 `dir`  
 Contiene la ruta de acceso de los directorios, sin incluir el designador de unidad o el nombre del archivo.  La barra diagonal final es opcional, y una barra diagonal \(\/\) o una barra diagonal inversa \(\\\) o ambas podrían usar en un solo argumento de `dir` .  Si no se especifica ninguna barra diagonal final \(\/o \\\), se inserta automáticamente.  Si `dir` es `NULL` o puntos en una cadena vacía, no se inserta ninguna ruta de directorio en la cadena compuesta de `path` .  
  
 `fname`  
 Contiene el nombre de archivo base sin ninguna extensiones.  Si `fname` es `NULL` o puntos en una cadena vacía, no se insertará ningún nombre de archivo en la cadena compuesta de `path` .  
  
 `ext`  
 Contiene la extensión de nombre de archivo real, con o sin un punto principal \(.\).  `_makepath` inserta el período automáticamente si no aparece en `ext`.  Si `ext` es `NULL` o puntos en una cadena vacía, no se inserta extensiones en la cadena compuesta de `path` .  
  
## Comentarios  
 La función de `_makepath` crea una cadena compuesta de la ruta de acceso de los componentes individuales, almacenar el resultado en `path`.  `path` podría incluir una letra de unidad, una ruta de acceso del directorio, un nombre de archivo, y una extensión de nombre de archivo.  `_wmakepath` es una versión con caracteres anchos de `_makepath`; los argumentos a `_wmakepath` son cadenas de caracteres anchos.  Por lo demás, `_wmakepath` y `_makepath` se comportan de forma idéntica.  
  
 **Nota de seguridad** Utilice una cadena terminada en null.  Para evitar la saturación del búfer, la cadena terminada en null no debe superar el tamaño del búfer de `path` .  `_makepath` no garantiza que la longitud de la cadena compuesta de la ruta no supere `_MAX_PATH`.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tmakepath`|`_makepath`|`_makepath`|`_wmakepath`|  
  
 El argumento de `path` debe señalar a un búfer vacío suficientemente grande para contener la ruta completa.  `path` compuesto debe ser menor que la constante de `_MAX_PATH` , definida en Stdlib.h.  
  
 Si la ruta de acceso es `NULL`, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Además, `errno` se establece en `EINVAL`.  los valores de`NULL` se permiten todos los demás parámetros.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_makepath`|\<stdlib.h\>|  
|`_wmakepath`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
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
  
  **Trazado creado con el \_makepath: c:\\sample\\crt\\makepath.c**  
**Ruta extraída con el \_splitpath:**  
 **Unidad: c:**  
 **Dir: \\sample\\crt\\**  
 **Nombre de archivo: makepath**  
 **Ext: .c**   
## Equivalente en .NET Framework  
 [System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_fullpath, \_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_splitpath, \_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [\_makepath\_s, \_wmakepath\_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)