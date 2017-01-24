---
title: "_stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wstat64"
  - "_stati64"
  - "_stat32"
  - "_stat32i64"
  - "_stat"
  - "_wstati64"
  - "_wstat32"
  - "_wstat64i32"
  - "_wstat"
  - "_stat64"
  - "_stat64i32"
  - "_wstat32i64"
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
  - "tstat32"
  - "tstat"
  - "_tstat64i32"
  - "tstati64"
  - "_wstat64"
  - "_wstat32"
  - "wstati64"
  - "tstat64"
  - "_stati64"
  - "_wstat"
  - "wstat64i32"
  - "stat32i64"
  - "tstat32i64"
  - "_tstat"
  - "_wstati64"
  - "_tstati64"
  - "_wstat32i64"
  - "wstat32"
  - "_wstat64i32"
  - "_stat"
  - "_tstat32"
  - "stat64i32"
  - "wstat64"
  - "stat"
  - "_stat32i64"
  - "_stat32"
  - "stati64"
  - "wstat"
  - "_stat64i32"
  - "stat32"
  - "_tstat32i64"
  - "tstat64i32"
  - "_tstat64"
  - "_stat64"
  - "stat/_stat"
  - "stat/_stat32"
  - "stat/_stat64"
  - "stat/_stati64"
  - "stat/_stat32i64"
  - "stat/_stat64i32"
  - "stat/_wstat"
  - "stat/_wstat32"
  - "stat/_wstat64"
  - "stat/_wstati64"
  - "stat/_wstat32i64"
  - "stat/_wstat64i32"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "archivos [C++], información de estado"
  - "_stat (función)"
  - "_wstat (función)"
  - "_stat64i32 (función)"
  - "tstat (función)"
  - "_tstat64i32 (función)"
  - "_stati64 (función)"
  - "_stat64 (función)"
  - "tstati64 (función)"
  - "wstati64 (función)"
  - "wstat64 (función)"
  - "_wstat64i32 (función)"
  - "_tstat32i64 (función)"
  - "_stat32i64 (función)"
  - "stat (función)"
  - "estado de archivos"
  - "_tstat32 (función)"
  - "tstat64 (función)"
  - "_wstat64 (función)"
  - "_tstat (función)"
  - "_stat32 (función)"
  - "wstat (función)"
  - "_wstat32i64 (función)"
  - "_tstati64 (función)"
  - "_wstat32 (función)"
  - "stat64 (función)"
  - "stati64 (función)"
  - "_wstati64 (función)"
  - "_tstat64 (función)"
  - "archivos [C++], obtener información de estado"
ms.assetid: 99a75ae6-ff26-47ad-af70-5ea7e17226a5
caps.latest.revision: 26
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtenga información de estado sobre un archivo.  
  
## Sintaxis  
  
```  
int _stat(  
   const char *path,  
   struct _stat *buffer   
);  
int _stat32(  
   const char *path,  
   struct __stat32 *buffer   
);  
int _stat64(  
   const char *path,  
   struct __stat64 *buffer   
);  
int _stati64(  
   const char *path,  
   struct _stati64 *buffer   
);  
int _stat32i64(  
   const char *path,  
   struct _stat32i64 *buffer   
);  
int _stat64i32(  
   const char *path,  
   struct _stat64i32 *buffer   
);  
int _wstat(  
   const wchar_t *path,  
   struct _stat *buffer   
);  
int _wstat32(  
   const wchar_t *path,  
   struct __stat32 *buffer   
);  
int _wstat64(  
   const wchar_t *path,  
   struct __stat64 *buffer   
);  
int _wstati64(  
   const wchar_t *path,  
   struct _stati64 *buffer   
);  
int _wstat32i64(  
   const wchar_t *path,  
   struct _stat32i64 *buffer   
);  
int _wstat64i32(  
   const wchar_t *path,  
   struct _stat64i32 *buffer   
);  
```  
  
#### Parámetros  
 `path`  
 Puntero a una cadena que contiene la ruta de acceso del directorio o el archivo existente.  
  
 `buffer`  
 Puntero a la estructura que almacena los resultados.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve 0 si se obtiene la información de estado de archivo. Un valor devuelto de –1 indica un error, en cuyo caso `errno` se establece en `ENOENT`, que indica que no se encontró el nombre de archivo o la ruta de acceso. Un valor devuelto de `EINVAL` indica un parámetro no válido; `errno` también se establece en `EINVAL` en este caso.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre este y otros códigos de retorno.  
  
 Si es posterior a la medianoche del 1 de enero de 1970 y antes de 23:59:59, el 31 de diciembre de 3000, UTC, a menos que utilice la marca de fecha en un archivo que se puede representar `_stat32` o `_wstat32`, o se ha definido `_USE_32BIT_TIME_T`, en cuyo caso se puede representar la fecha hasta las 23:59:59 del 18 de enero de 2038, hora UTC.  
  
## Comentarios  
 La función `_stat` obtiene información sobre el archivo o el directorio especificado por `path` y lo almacena en la estructura que señala `buffer`.`_stat` controla automáticamente argumentos de cadenas de caracteres multibyte según corresponda, reconociendo secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso.  
  
 `_wstat` es una versión con caracteres anchos de `_stat`; el argumento `path` para `_wstat` es una cadena de caracteres anchos.`_wstat` y `_stat` se comportan de manera idéntica, salvo que `_wstat` no controla las cadenas de caracteres multibyte.  
  
 Variaciones de estas funciones admiten tipos de tiempo de 32 o 64 bits, y longitudes de archivos de 32 o 64 bits. El primer sufijo numérico \(`32` o `64`\) indica el tamaño del tipo de tiempo usado; el segundo sufijo es `i32` o `i64`, lo que indica si el tamaño del archivo se representa como un entero de 32 o 64 bits.  
  
 `_stat` es equivalente a `_stat64i32`, y `struct``_stat` contiene una hora de 64 bits. Esto es así a menos que `_USE_32BIT_TIME_T` se define, en cuyo caso el comportamiento anterior está en vigor; `_stat` usa uno de 32 bits, y `struct``_stat` contiene una hora de 32 bits. Lo mismo ocurre para `_stati64`.  
  
> [!NOTE]
>  `_wstat` no funciona con vínculos simbólicos [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. En estos casos, `_wstat` siempre notificará un tamaño de archivo de 0.`_stat` funciona correctamente con vínculos simbólicos.  
  
 Esta función valida sus parámetros. Si `path` o `buffer` es `NULL`, se invoca el controlador de parámetros no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
### Tipo de tiempo y variaciones de tipo de longitud de archivo de \_stat  
  
|Funciones|¿\_USE\_32BIT\_TIME\_T definida?|Tipo de tiempo|Tipo de longitud de archivo|  
|---------------|--------------------------------------|--------------------|---------------------------------|  
|`_stat`, `_wstat`|No definida|64 bits|32 bits|  
|`_stat`, `_wstat`|Definido|32 bits|32 bits|  
|`_stat32`, `_wstat32`|No se ve afectada por la definición de macro|32 bits|32 bits|  
|`_stat64`, `_wstat64`|No se ve afectada por la definición de macro|64 bits|64 bits|  
|`_stati64`, `_wstati64`|No definida|64 bits|64 bits|  
|`_stati64`, `_wstati64`|Definido|32 bits|64 bits|  
|`_stat32i64`, `_wstat32i64`|No se ve afectada por la definición de macro|32 bits|64 bits|  
|`_stat64i32`, `_wstat64i32`|No se ve afectada por la definición de macro|64 bits|32 bits|  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tstat`|`_stat`|`_stat`|`_wstat`|  
|`_tstat64`|`_stat64`|`_stat64`|`_wstat64`|  
|`_tstati64`|`_stati64`|`_stati64`|`_wstati64`|  
|`_tstat32i64`|`_stat32i64`|`_stat32i64`|`_wstat32i64`|  
|`_tstat64i32`|`_stat64i32`|`_stat64i32`|`_wstat64i32`|  
  
 La estructura `_stat`, definida en SYS\\STAT.H, incluye los siguientes campos:  
  
 `st_gid`  
 Identificador numérico del grupo que posee el archivo \(específico de UNIX\). Este campo siempre será cero en sistemas Windows. Un archivo redirigido se clasifica como archivo Windows.  
  
 `st_atime`  
 Hora del último acceso del archivo. Válido en NTFS, pero no en unidades de disco con formato FAT.  
  
 `st_ctime`  
 Hora de creación del archivo. Válido en NTFS, pero no en unidades de disco con formato FAT.  
  
 `st_dev`  
 Número de unidad del disco que contiene el archivo \(igual que `st_rdev`\).  
  
 `st_ino`  
 Número del nodo de información \(`inode`\) para el archivo \(específico de UNIX\). En sistemas de archivos UNIX, `inode` describe la fecha del archivo y las marcas de tiempo, los permisos y el contenido. Cuando los archivos se vinculan físicamente entre sí, comparten el mismo `inode`.`inode` y, por tanto, `st_ino`, no tiene ningún significado en los sistemas de archivos FAT, HPFS o NTFS.  
  
 `st_mode`  
 Máscara de bits para información de modo de archivo. El bit `_S_IFDIR` se establece si `path` especifica un directorio; el bit `_S_IFREG` se establece si `path` especifica un archivo normal o un dispositivo. Los bits de lectura y escritura de usuario se establecen según el modo de permiso del archivo; los bits de ejecución de usuario se establecen según la extensión del nombre de archivo.  
  
 `st_mtime`  
 Hora de la última modificación del archivo.  
  
 `st_nlink`  
 Siempre 1 en sistemas de archivos que no son NTFS.  
  
 `st_rdev`  
 Número de unidad del disco que contiene el archivo \(igual que `st_dev`\).  
  
 `st_size`  
 Tamaño del archivo en bytes; entero de 64 bits para variaciones con el sufijo `i64`**.**  
  
 `st_uid`  
 Identificador numérico del usuario propietario del archivo \(específico de UNIX\). Este campo siempre será cero en los sistemas Windows. Un archivo redirigido se clasifica como archivo Windows.  
  
 Si `path` hace referencia a un dispositivo,  `st_size`, varios campos de tiempo, `st_dev` y los campos `st_rdev` de la estructura `_stat` no tienen sentido. Dado que STAT. H usa el tipo [\_dev\_t](../../c-runtime-library/standard-types.md) que se define en TYPES.H, debe incluir TYPES.H antes de STAT.H en su código.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezados opcionales|  
|------------|--------------------------|----------------------------|  
|`_stat`, `_stat32`, `_stat64`, `_stati64`, `_stat32i64`, `_stat64i32`|\<sys\/types.h\> seguido de \<sys\/stat.h\>|\<errno.h\>|  
|`_wstat`, `_wstat32`, `_wstat64`, `_wstati64`, `_wstat32i64`, `_wstat64i32`|\<sys\/types.h\> seguido de \<sys\/stat.h\> o \<wchar.h\>|\<errno.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_stat.c  
// This program uses the _stat function to  
// report information about the file named crt_stat.c.  
  
#include <time.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
   struct _stat buf;  
   int result;  
   char timebuf[26];  
   char* filename = "crt_stat.c";  
   errno_t err;  
  
   // Get data associated with "crt_stat.c":   
   result = _stat( filename, &buf );  
  
   // Check if statistics are valid:   
   if( result != 0 )  
   {  
      perror( "Problem getting information" );  
      switch (errno)  
      {  
         case ENOENT:  
           printf("File %s not found.\n", filename);  
           break;  
         case EINVAL:  
           printf("Invalid parameter to _stat.\n");  
           break;  
         default:  
           /* Should never be reached. */  
           printf("Unexpected error in _stat.\n");  
      }  
   }  
   else  
   {  
      // Output some of the statistics:   
      printf( "File size     : %ld\n", buf.st_size );  
      printf( "Drive         : %c:\n", buf.st_dev + 'A' );  
      err = ctime_s(timebuf, 26, &buf.st_mtime);  
      if (err)  
      {  
         printf("Invalid arguments to ctime_s.");  
         exit(1);  
      }  
      printf( "Time modified : %s", timebuf );  
   }  
}  
```  
  
```Output  
Tamaño de archivo     : 732 Unidad         : C: Hora de modificación: Jue 07 Feb 14:39:36 2002  
```  
  
## Equivalente en .NET Framework  
  
-   [System::IO::File::GetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.getattributes.aspx)  
  
-   [System::IO::File::GetCreationTime](https://msdn.microsoft.com/en-us/library/system.io.file.getcreationtime.aspx)  
  
-   [System::IO::File::GetLastAccessTime](https://msdn.microsoft.com/en-us/library/system.io.file.getlastaccesstime.aspx)  
  
-   [System::IO::File::GetLastWriteTime](https://msdn.microsoft.com/en-us/library/system.io.file.getlastwritetime.aspx)  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_access, \_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [\_fstat, \_fstat32, \_fstat64, \_fstati64, \_fstat32i64, \_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)