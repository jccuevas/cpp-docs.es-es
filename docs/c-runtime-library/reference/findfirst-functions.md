---
title: "_findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64 | Microsoft Docs"
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
  - "_findfirst"
  - "_wfindfirst"
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
  - "findfirst32i64"
  - "wfindfirst32i64"
  - "tfindfirst64"
  - "_findfirst64i32"
  - "_wfindfirst32i64"
  - "_wfindfirsti64"
  - "wfindfirst"
  - "_tfindfirsti64"
  - "findfirst32"
  - "_tfindfirst32"
  - "_findfirsti64"
  - "findfirst"
  - "wfindfirst64"
  - "wfindfirst32"
  - "tfindfirst32"
  - "_wfindfirst64i32"
  - "findfirst64i32"
  - "tfindfirst64i32"
  - "_wfindfirst"
  - "findfirsti64"
  - "_findfirst32i64"
  - "wfindfirst64i32"
  - "_wfindfirst32"
  - "_findfirst32"
  - "_tfindfirst32i64"
  - "tfindfirst"
  - "_tfindfirst64i32"
  - "findfirst64"
  - "_tfindfirst"
  - "_findfirst64"
  - "_tfindfirst64"
  - "tfindfirst32i64"
  - "_findfirst"
  - "_wfindfirst64"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tfindfirst64 (función)"
  - "_wfindfirst64i32 (función)"
  - "_wfindfirst32i64 (función)"
  - "wfindfirst32 (función)"
  - "_findfirst (función)"
  - "wfindfirst64 (función)"
  - "_wfindfirst (función)"
  - "_findfirst64i32 (función)"
  - "wfindfirst (función)"
  - "_findfirst64 (función)"
  - "tfindfirst32 (función)"
  - "_tfindfirst64i32 (función)"
  - "findfirst (función)"
  - "findfirst32i64 (función)"
  - "tfindfirst64 (función)"
  - "_tfindfirst32 (función)"
  - "tfindfirst32i64 (función)"
  - "tfindfirst64i32 (función)"
  - "_wfindfirsti64 (función)"
  - "_findfirst32i64 (función)"
  - "findfirst32 (función)"
  - "findfirsti64 (función)"
  - "findfirst64i32 (función)"
  - "tfindfirsti64 (función)"
  - "tfindfirst (función)"
  - "_wfindfirst32 (función)"
  - "wfindfirsti64 (función)"
  - "_tfindfirsti64 (función)"
  - "_tfindfirst (función)"
  - "_tfindfirst32i64 (función)"
  - "findfirst64 (función)"
  - "_findfirst32 (función)"
  - "_findfirsti64 (función)"
  - "wfindfirst32i64 (función)"
  - "wfindfirst64i32 (función)"
  - "_wfindfirst64 (función)"
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona información sobre la primera instancia de un nombre de archivo que coincida con el archivo especificado en el argumento de `filespec` .  
  
## Sintaxis  
  
```  
intptr_t _findfirst(  
   const char *filespec,  
   struct _finddata_t *fileinfo   
);  
intptr_t _findfirst32(  
   const char *filespec,  
   struct _finddata32_t *fileinfo   
);  
intptr_t _findfirst64(  
   const char *filespec,  
   struct _finddata64_t *fileinfo   
);  
intptr_t _findfirsti64(  
   const char *filespec,  
   struct _finddatai64_t *fileinfo   
);  
intptr_t _findfirst32i64(  
   const char *filespec,  
   struct _finddata32i64_t *fileinfo   
);  
intptr_t _findfirst64i32(  
   const char *filespec,  
   struct _finddata64i32_t *fileinfo   
);  
intptr_t _wfindfirst(  
   const wchar_t *filespec,  
   struct _wfinddata_t *fileinfo   
);  
intptr_t _wfindfirst32(  
   const wchar_t *filespec,  
   struct _wfinddata32_t *fileinfo   
);  
intptr_t _wfindfirst64(  
   const wchar_t *filespec,  
   struct _wfinddata64_t *fileinfo   
);  
intptr_t _wfindfirsti64(  
   const wchar_t *filespec,  
   struct _wfinddatai64_t *fileinfo   
);  
intptr_t _wfindfirst32i64(  
   const wchar_t *filespec,  
   struct _wfinddata32i64_t *fileinfo   
);  
intptr_t _wfindfirst64i32(  
   const wchar_t *filespec,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### Parámetros  
 `filespec`  
 Especificación del archivo de destino \(puede incluir caracteres comodín\).  
  
 `fileinfo`  
 Búfer de información de archivo.  
  
## Valor devuelto  
 Si es correcto, `_findfirst` devuelve un identificador único de la búsqueda que identifica el archivo o el grupo de archivos que coinciden con la especificación de `filespec` , que se puede utilizar en una llamada subsiguiente a [\_findnext](../../c-runtime-library/reference/findnext-functions.md) o a `_findclose`.  Si no, `_findfirst` vuelve – 1 y establece `errno` en uno de los siguientes valores.  
  
 `EINVAL`  
 Parámetro no válido: `filespec` o `fileinfo` era `NULL`.  O, el sistema operativo devolvió un error inesperado.  
  
 `ENOENT`  
 Especificación de archivo que no se pudo coincidente.  
  
 `ENOMEM`  
 Memoria insuficiente.  
  
 `EINVAL`  
 La especificación no válida del nombre o el nombre de archivo dado era mayor que `MAX_PATH`.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Si se pasa un parámetro no válido en, estas funciones se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
## Comentarios  
 Debe llamar a [\_findclose](../../c-runtime-library/reference/findclose.md) cuando haya con `_findfirst` o la función de `_findnext` \(o cualquier variantes\).  Esto libera los recursos utilizados por estas funciones en la aplicación.  
  
 Las variaciones de estas funciones que tienen el prefijo de `w` son versiones de carácter ancho; si no, son idénticas a las funciones correspondientes de solo\- byte.  
  
 Las variaciones de estas funciones admiten tipos de 32 bits o de 64 bits de tiempo y tamaños de archivo de 32 bits o de 64 bits.  El primer sufijo numérico \(`32` o `64`\) indica el tamaño del tipo de tiempo; el segundo sufijo es `i32` o `i64`, e indica si el tamaño de archivo está representado como un entero de 32 bits o de 64 bits.  Para obtener información sobre las versiones admiten tipos de 32 bits y 64 bits del tiempo y tamaños de archivo, vea la tabla siguiente.  Se omite el sufijo de `i32` o de `i64` si es igual que el tamaño del tipo de tiempo, por lo que `_findfirst64` también admite longitudes de 64 bits del archivo y `_findfirst32` solo admite longitudes de 32 bits del archivo.  
  
 Estas funciones utilizan las diversas formas de la estructura de `_finddata_t` para el parámetro de `fileinfo` .  Para obtener más información sobre la estructura, vea [Funciones de búsqueda de nombre de archivo](../../c-runtime-library/filename-search-functions.md).  
  
 Las variaciones que utilizan un tipo de 64 bits de tiempo habilitan las fechas de creación de archivos que se expresarán hacia arriba con 23:59: 59, el 31 de diciembre, 3000, la hora UTC.  Los que utilizan tipos de 32 bits de tiempo representan las fechas sólo con 19:14: 7 de enero de 18, 2038, La hora UTC.  La medianoche, el 1 de enero de 1970, es el límite inferior del intervalo de fechas para todas estas funciones.  
  
 A menos que tenga una razón concreta para usar las versiones que especifica el tamaño de tiempo explícitamente, el uso `_findfirst` o `_wfindfirst` o, si necesita los tamaños de 3 GB de mayor tamaño de archivo auxiliar, utiliza `_findfirsti64` o `_wfindfirsti64`.  Todas estas funciones utilizan el tipo de 64 bits del tiempo.  En versiones anteriores, estas funciones se utilizó un tipo de 32 bits del tiempo.  Si éste es un cambio importante para una aplicación, puede definir `_USE_32BIT_TIME_T` para revertir al comportamiento anterior.  Si se define `_USE_32BIT_TIME_T` , `_findfirst`, `_finfirsti64`, y sus correspondientes versiones de Unicode utilizan un plazo de 32 bits.  
  
### El tipo y el archivo Length de tiempo escriben variaciones de \_findfirst  
  
|Funciones|¿`_USE_32BIT_TIME_T` definió?|Tipo de tiempo|Tipo de la longitud del archivo|  
|---------------|-----------------------------------|--------------------|-------------------------------------|  
|`_findfirst`, `_wfindfirst`|No definido|64 bits|32 bits|  
|`_findfirst`, `_wfindfirst`|Definido|32 bits|32 bits|  
|`_findfirst32`, `_wfindfirst32`|No se ve afectado por la definición de macro|32 bits|32 bits|  
|`_findfirst64`, `_wfindfirst64`|No se ve afectado por la definición de macro|64 bits|64 bits|  
|`_findfirsti64`, `_wfindfirsti64`|No definido|64 bits|64 bits|  
|`_findfirsti64`, `_wfindfirsti64`|Definido|32 bits|64 bits|  
|`_findfirst32i64`, `_wfindfirst32i64`|No se ve afectado por la definición de macro|32 bits|64 bits|  
|`_findfirst64i32`, `_wfindfirst64i32`|No se ve afectado por la definición de macro|64 bits|32 bits|  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tfindfirst`|`_findfirst`|`_findfirst`|`_wfindfirst`|  
|`_tfindfirst32`|`_findfirst32`|`_findfirst32`|`_wfindfirst32`|  
|`_tfindfirst64`|`_findfirst64`|`_findfirst64`|`_wfindfirst64`|  
|`_tfindfirsti64`|`_findfirsti64`|`_findfirsti64`|`_wfindfirsti64`|  
|`_tfindfirst32i64`|`_findfirst32i64`|`_findfirst32i64`|`_wfindfirst32i64`|  
|`_tfindfirst64i32`|`_findfirst64i32`|`_findfirst64i32`|`_wfindfirst64i32`|  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_findfirst`|\<io.h\>|  
|`_findfirst32`|\<io.h\>|  
|`_findfirst64`|\<io.h\>|  
|`_findfirsti64`|\<io.h\>|  
|`_findfirst32i64`|\<io.h\>|  
|`_findfirst64i32`|\<io.h\>|  
|`_wfindfirst`|\<io.h o\> wchar.h \<\>|  
|`_wfindfirst32`|\<io.h o\> wchar.h \<\>|  
|`_wfindfirst64`|\<io.h o\> wchar.h \<\>|  
|`_wfindfirsti64`|\<io.h o\> wchar.h \<\>|  
|`_wfindfirst32i64`|\<io.h o\> wchar.h \<\>|  
|`_wfindfirst64i32`|\<io.h o\> wchar.h \<\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 [System::IO::DirectoryInfo::GetFiles](https://msdn.microsoft.com/en-us/library/system.io.directoryinfo.getfiles.aspx)  
  
## Vea también  
 [Llamadas del sistema](../../c-runtime-library/system-calls.md)   
 [Funciones de búsqueda de nombre de archivo](../../c-runtime-library/filename-search-functions.md)