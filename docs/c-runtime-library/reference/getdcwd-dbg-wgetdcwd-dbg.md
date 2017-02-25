---
title: "_getdcwd_dbg, _wgetdcwd_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getdcwd_dbg"
  - "_wgetdcwd_dbg"
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
apitype: "DLLExport"
f1_keywords: 
  - "_getdcwd_dbg"
  - "getdcwd_dbg"
  - "_wgetdcwd_dbg"
  - "wgetdcwd_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_getdcwd_dbg (función)"
  - "_wgetdcwd_dbg (función)"
  - "directorio de trabajo actual"
  - "directorios [C++], de trabajo actuales"
  - "getdcwd_dbg (función)"
  - "wgetdcwd_dbg (función)"
  - "directorio de trabajo"
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _getdcwd_dbg, _wgetdcwd_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Depura versiones de las funciones [\_getdcwd, \_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md) \(disponible únicamente durante una depuración\).  
  
## Sintaxis  
  
```  
char *_getdcwd_dbg(    int drive,    char *buffer,    int maxlen,    int blockType,    const char *filename,    int linenumber  ); wchar_t *_wgetdcwd_dbg(    int drive,    wchar_t *buffer,    int maxlen,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### Parámetros  
 `drive`  
 Nombre de la unidad de disco.  
  
 `buffer`  
 Ubicación de almacenamiento de la ruta de acceso.  
  
 `maxlen`  
 Longitud máxima de la ruta de acceso en caracteres `char` para `_getdcwd_dbg`y `wchar_t`para `_wgetdcwd_dbg`.  
  
 `blockType`  
 Tipo de bloque de memoria solicitado: `_CLIENT_BLOCK` o `_NORMAL_BLOCK`.  
  
 `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o valor `NULL`.  
  
 `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o valor `NULL`.  
  
## Valor devuelto  
 Devuelve un puntero a `buffer`.  Un valor devuelto de `NULL` indica un error, y `errno` se establece en `ENOMEM`, que indica que no hay memoria suficiente para asignar los bytes de `maxlen` \(cuando un argumento de `NULL` se proporciona como `buffer`\), o en `ERANGE`, que indica que la ruta de acceso es más larga que los caracteres de `maxlen`.  Para obtener más información, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Las funciones `_getdcwd_dbg` y `_wgetdcwd_dbg` son idénticas a `_getdcwd` y `_wgetdcwd`, salvo que, si se define `_DEBUG`, estas funciones usan la versión de depuración de `malloc` y `_malloc_dbg` para asignar memoria si se pasa `NULL` como parámetro de `buffer`.  Para obtener más información, vea [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md).  
  
 En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría.  En lugar de ello, se puede definir la marca `_CRTDBG_MAP_ALLOC`.  Si se define `_CRTDBG_MAP_ALLOC`, las llamadas a `_getdcwd` y `_wgetdcwd` se reasignan a `_getdcwd_dbg` y `_wgetdcwd_dbg`, respectivamente, con el parámetro `blockType` establecido en `_NORMAL_BLOCK`.  Por consiguiente, no necesario llamar a estas funciones explícitamente a menos que se desee marcar los bloques del montón como `_CLIENT_BLOCK`.  Para obtener más información, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tgetdcwd_dbg`|`_getdcwd_dbg`|`_getdcwd_dbg`|`_wgetdcwd_dbg`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_getdcwd_dbg`|\<crtdbg.h\>|  
|`_wgetdcwd_dbg`|\<crtdbg.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## Equivalente en .NET Framework  
 <xref:System.Environment.CurrentDirectory%2A?displayProperty=fullName>  
  
## Vea también  
 [\_getdcwd, \_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)   
 [Control de directorio](../../c-runtime-library/directory-control.md)   
 [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)