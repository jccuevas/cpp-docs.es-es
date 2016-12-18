---
title: "_makepath_s, _wmakepath_s | Microsoft Docs"
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
  - "_wmakepath_s"
  - "_makepath_s"
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
  - "_wmakepath_s"
  - "makepath_s"
  - "_makepath_s"
  - "wmakepath_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_makepath_s (función)"
  - "wmakepath_s (función)"
  - "rutas de acceso"
  - "_wmakepath_s (función)"
  - "makepath_s (función)"
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
caps.latest.revision: 29
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _makepath_s, _wmakepath_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea un nombre de ruta de componentes.  Éstas son versiones de [\_makepath, \_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
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
  
#### Parámetros  
 \[out\] `path`  
 Búfer de la ruta de acceso completa.  
  
 \[in\] `sizeInWords`  
 Tamaño del búfer en palabras.  
  
 \[in\] `sizeInBytes`  
 Tamaño del búfer en bytes.  
  
 \[in\] `drive`  
 Contiene una letra \(A, b, etc.\) correspondiente a la unidad deseada y un signo de dos puntos final opcional.  `_makepath_s` inserta el dos puntos automáticamente en la ruta compuesta si falta.  Si `drive` es `NULL` o puntos en una cadena vacía, ninguna letra de unidad aparece en la cadena compuesta de `path` .  
  
 \[in\] `dir`  
 Contiene la ruta de acceso de los directorios, sin incluir el designador de unidad o el nombre del archivo.  La barra diagonal final es opcional, y una barra diagonal \(\/\) o una barra diagonal inversa \(\\\) o ambas podrían usar en un solo argumento de `dir` .  Si no se especifica ninguna barra diagonal final \(\/o \\\), se inserta automáticamente.  Si `dir` es `NULL` o puntos en una cadena vacía, no se inserta ninguna ruta de directorio en la cadena compuesta de `path` .  
  
 \[in\] `fname`  
 Contiene el nombre de archivo base sin ninguna extensiones.  Si `fname` es `NULL` o puntos en una cadena vacía, no se insertará ningún nombre de archivo en la cadena compuesta de `path` .  
  
 \[in\] `ext`  
 Contiene la extensión de nombre de archivo real, con o sin un punto principal \(.\).  `_makepath_s` inserta el período automáticamente si no aparece en `ext`.  Si `ext` es `NULL` o puntos en una cadena vacía, no se inserta extensiones en la cadena compuesta de `path` .  
  
## Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
### Condiciones de error  
  
|`path`|`sizeInWords` \/ `sizeInBytes`|Devolución|Contenido de `path`|  
|------------|------------------------------------|----------------|-------------------------|  
|`NULL`|any|`EINVAL`|no modificado|  
|any|\<\= 0|`EINVAL`|no modificado|  
  
 Si es un de los sobre condiciones de error, estas funciones se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se estableceen`EINVAL` y las funciones devuelven`EINVAL`**.** `NULL` se tienen en cuenta los parámetros `drive`, `fname`, y `ext`.  Para obtener información sobre el comportamiento cuando estos parámetros son punteros nulos o cadenas vacías, vea la sección comentarios.  
  
## Comentarios  
 La función de `_makepath_s` crea una cadena compuesta de la ruta de acceso de los componentes individuales, almacenar el resultado en `path`.  `path` podría incluir una letra de unidad, una ruta de acceso del directorio, un nombre de archivo, y una extensión de nombre de archivo.  `_wmakepath_s` es una versión con caracteres anchos de `_makepath_s`; los argumentos a `_wmakepath_s` son cadenas de caracteres anchos.  Por lo demás, `_wmakepath_s` y `_makepath_s` se comportan de forma idéntica.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tmakepath_s`|`_makepath_s`|`_makepath_s`|`_wmakepath_s`|  
  
 El argumento de `path` debe señalar a un búfer vacío suficientemente grande para contener la ruta completa.  `path` compuesto debe ser menor que la constante de `_MAX_PATH` , definida en Stdlib.h.  
  
 Si la ruta de acceso es `NULL`, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Además, `errno` se establece en `EINVAL`.  los valores de`NULL` se permiten todos los demás parámetros.  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
 Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD.  Para deshabilitar este comportamiento, use [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_makepath_s`|\<stdlib.h\>|  
|`_wmakepath_s`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
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
  
## Resultados  
  
```  
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c  
  
Path extracted with _splitpath_s:  
  Drive: c:  
  Dir: \sample\crt\  
  Filename: crt_makepath_s  
  Ext: .c  
```  
  
## Equivalente en .NET Framework  
 [System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_fullpath, \_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_splitpath\_s, \_wsplitpath\_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)   
 [\_makepath, \_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)