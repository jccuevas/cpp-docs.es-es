---
title: "_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wfindnext"
  - "_findnext"
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
  - "findnext"
  - "_wfindnext32i64"
  - "_tfindnext64i32"
  - "findnext32"
  - "findnext32i64"
  - "wfindnext64i32"
  - "_wfindnext"
  - "tfindnext64"
  - "findnexti64"
  - "_findnexti64"
  - "_tfindnexti64"
  - "_findnext64i32"
  - "tfindnexti64"
  - "tfindnext32"
  - "_wfindnext64i32"
  - "findnext64i32"
  - "_findnext"
  - "_tfindnext32i64"
  - "_wfindnext64"
  - "wfindnext"
  - "wfindnext32"
  - "tfindnext32i64"
  - "_findnext64"
  - "_tfindnext64"
  - "_wfindnext32"
  - "findnext64"
  - "_findnext32i64"
  - "tfindnext"
  - "wfindnexti64"
  - "tfindnext64i32"
  - "_tfindnext32"
  - "wfindnext32i64"
  - "wfindnext64"
  - "_wfindnexti64"
  - "_tfindnext"
  - "_findnext32"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_wfindnexti64 (función)"
  - "_tfindnext32 (función)"
  - "wfindnexti64 (función)"
  - "_wfindnext32i64 (función)"
  - "findnext32i64 (función)"
  - "tfindnext64i32 (función)"
  - "_tfindnext64i32 (función)"
  - "_findnext (función)"
  - "findnext64i32 (función)"
  - "_tfindnext (función)"
  - "findnext32 (función)"
  - "tfindnext32 (función)"
  - "_findnext32 (función)"
  - "_tfindnext32i64 (función)"
  - "_wfindnext (función)"
  - "tfindnext (función)"
  - "_findnext64 (función)"
  - "findnext64 (función)"
  - "_findnext64i32 (función)"
  - "wfindnext32i64 (función)"
  - "findnext (función)"
  - "wfindnext32 (función)"
  - "_wfindnext64i32 (función)"
  - "findnexti64 (función)"
  - "_wfindnext64 (función)"
  - "_findnext32i64 (función)"
  - "_findnexti64 (función)"
  - "_tfindnext64 (función)"
  - "wfindnext64i32 (función)"
  - "tfindnexti64 (función)"
  - "wfindnext64 (función)"
  - "wfindnext (función)"
  - "tfindnext64 (función)"
  - "_wfindnext32 (función)"
  - "tfindnext32i64 (función)"
  - "_tfindnexti64 (función)"
ms.assetid: 75d97188-5add-4698-a46c-4c492378f0f8
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Busque el siguiente nombre, si existe, que coincide con el argumento de `filespec` en una llamada anterior a [\_findfirst](../../c-runtime-library/reference/findfirst-functions.md)y, a continuación modifique el contenido de la estructura de `fileinfo` en consecuencia.  
  
## Sintaxis  
  
```  
int _findnext(  
   intptr_t handle,  
   struct _finddata_t *fileinfo   
);  
int _findnext32(  
   intptr_t handle,  
   struct _finddata32_t *fileinfo   
);  
int _findnext64(  
   intptr_t handle,  
   struct __finddata64_t *fileinfo   
);  
int _findnexti64(  
   intptr_t handle,  
   struct __finddatai64_t *fileinfo   
);  
int _findnext32i64(  
   intptr_t handle,  
   struct _finddata32i64_t *fileinfo   
);  
int _findnext64i32(  
   intptr_t handle,  
   struct _finddata64i32_t *fileinfo   
);  
int _wfindnext(  
   intptr_t handle,  
   struct _wfinddata_t *fileinfo   
);  
int _wfindnext32(  
   intptr_t handle,  
   struct _wfinddata32_t *fileinfo   
);  
int _wfindnext64(  
   intptr_t handle,  
   struct _wfinddata64_t *fileinfo   
);  
int _wfindnexti64(  
   intptr_t handle,  
   struct _wfinddatai64_t *fileinfo   
);  
int _wfindnext32i64(  
   intptr_t handle,  
   struct _wfinddatai64_t *fileinfo   
);  
int _wfindnext64i32(  
   intptr_t handle,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### Parámetros  
 `handle`  
 Busque el identificador devuelto por una llamada anterior a `_findfirst`.  
  
 `fileinfo`  
 Búfer de información de archivo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve 0.  De lo contrario, devuelve – 1 y establece `errno` a un valor que indica la naturaleza del error.  Los códigos de error posibles se muestran en la tabla siguiente.  
  
 `EINVAL`  
 Parámetro no válido: `fileinfo` era `NULL`.  O, el sistema operativo devolvió un error inesperado.  
  
 `ENOENT`  
 No más de archivos coincidentes podrían ser encontrados.  
  
 `ENOMEM`  
 Memoria insuficiente o la longitud del nombre de archivo supera `MAX_PATH`.  
  
 Si se pasa un parámetro no válido en, estas funciones se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
## Comentarios  
 Debe llamar a [\_findclose](../../c-runtime-library/reference/findclose.md) cuando haya terminado de `_findfirst` o la función de `_findnext` \(o cualquier variantes\).  Esto libera los recursos utilizados por estas funciones en la aplicación.  
  
 Las variaciones de estas funciones con el prefijo de `w` son versiones de carácter ancho; si no, son idénticas a las funciones correspondientes de solo\- byte.  
  
 Las variaciones de estas funciones admiten tipos de 32 bits o de 64 bits de tiempo y tamaños de archivo de 32 bits o de 64 bits.  El primer sufijo numérico \(`32` o `64`\) indica el tamaño del tipo de tiempo utilizado; el segundo sufijo es `i32` o `i64`, que indica si el tamaño de archivo está representado como un entero de 32 bits o de 64 bits.  Para obtener información sobre las versiones admiten tipos de 32 bits y 64 bits del tiempo y tamaños de archivo, vea la tabla siguiente.  Las variaciones que utilizan un tipo de 64 bits de tiempo permiten que las fechas de creación de archivos se expresadas hacia arriba con 23:59: 59, el 31 de diciembre, 3000, hora UTC; mientras que los mediante tipos de 32 bits de tiempo representan sólo las fechas con 19:14: 7 de enero de 18, 2038, La hora UTC.  La medianoche, el 1 de enero de 1970, es el límite inferior del intervalo de fechas para todas estas funciones.  
  
 A menos que tenga una razón concreta para usar las versiones que especifica el tamaño de tiempo explícitamente, el uso `_findnext` o `_wfindnext` o, si necesita los tamaños mayor de 3 GB de archivo auxiliar, utiliza `_findnexti64` o `_wfindnexti64`.  Todas estas funciones utilizan el tipo de 64 bits del tiempo.  En versiones anteriores, estas funciones se utilizó un tipo de 32 bits del tiempo.  Si éste es un cambio importante para una aplicación, puede definir `_USE_32BIT_TIME_T` para obtener el comportamiento antiguo.  Si se define `_USE_32BIT_TIME_T` , `_findnext`, `_finnexti64` y sus correspondientes versiones de Unicode utilizan un plazo de 32 bits.  
  
### El tipo y el archivo Length de tiempo escriben variaciones de \_findnext  
  
|Funciones|¿`_USE_32BIT_TIME_T` definió?|Tipo de tiempo|Tipo de la longitud del archivo|  
|---------------|-----------------------------------|--------------------|-------------------------------------|  
|`_findnext`, `_wfindnext`|No definido|64 bits|32 bits|  
|`_findnext`, `_wfindnext`|Definido|32 bits|32 bits|  
|`_findnext32`, `_wfindnext32`|No se ve afectado por la definición de macro|32 bits|32 bits|  
|`_findnext64`, `_wfindnext64`|No se ve afectado por la definición de macro|64 bits|64 bits|  
|`_findnexti64`, `_wfindnexti64`|No definido|64 bits|64 bits|  
|`_findnexti64`, `_wfindnexti64`|Definido|32 bits|64 bits|  
|`_findnext32i64`, `_wfindnext32i64`|No se ve afectado por la definición de macro|32 bits|64 bits|  
|`_findnext64i32`, `_wfindnext64i32`|No se ve afectado por la definición de macro|64 bits|32 bits|  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tfindnext`|`_findnext`|`_findnext`|`_wfindnext`|  
|`_tfindnext32`|`_findnext32`|`_findnext32`|`_wfindnext32`|  
|`_tfindnext64`|`_findnext64`|`_findnext64`|`_wfindnext64`|  
|`_tfindnexti64`|`_findnexti64`|`_findnexti64`|`_wfindnexti64`|  
|`_tfindnext32i64`|`_findnext32i64`|`_findnext32i64`|`_wfindnext32i64`|  
|`_tfindnext64i32`|`_findnext64i32`|`_findnext64i32`|`_wfindnext64i32`|  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_findnext`|\<io.h\>|  
|`_findnext32`|\<io.h\>|  
|`_findnext64`|\<io.h\>|  
|`_findnexti64`|\<io.h\>|  
|`_findnext32i64`|\<io.h\>|  
|`_findnext64i32`|\<io.h\>|  
|`_wfindnext`|\<io.h o\> wchar.h \<\>|  
|`_wfindnext32`|\<io.h o\> wchar.h \<\>|  
|`_wfindnext64`|\<io.h o\> wchar.h \<\>|  
|`_wfindnexti64`|\<io.h o\> wchar.h \<\>|  
|`_wfindnext32i64`|\<io.h o\> wchar.h \<\>|  
|`_wfindnext64i32`|\<io.h o\> wchar.h \<\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Llamadas del sistema](../../c-runtime-library/system-calls.md)   
 [Funciones de búsqueda de nombre de archivo](../../c-runtime-library/filename-search-functions.md)