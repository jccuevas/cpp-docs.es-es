---
title: "_fullpath_dbg, _wfullpath_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wfullpath_dbg"
  - "_fullpath_dbg"
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
  - "wfullpath_dbg"
  - "_wfullpath_dbg"
  - "_fullpath_dbg"
  - "fullpath_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fullpath_dbg (función)"
  - "_wfullpath_dbg (función)"
  - "rutas de acceso absolutas"
  - "fullpath_dbg (función)"
  - "rutas de acceso de archivo relativas"
  - "wfullpath_dbg (función)"
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# _fullpath_dbg, _wfullpath_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Versiones de [\_fullpath, \_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md) que usan la versión de depuración de `malloc` para asignar memoria.  
  
## Sintaxis  
  
```  
char *_fullpath_dbg(     char *absPath,    const char *relPath,    size_t maxLength,    int blockType,    const char *filename,    int linenumber  ); wchar_t *_wfullpath_dbg(     wchar_t *absPath,    const wchar_t *relPath,    size_t maxLength,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### Parámetros  
 `absPath`  
 Puntero al búfer que contiene el nombre de ruta de acceso absoluta o completa, o bien `NULL`.  
  
 `relPath`  
 Nombre de ruta de acceso relativa.  
  
 `maxLength`  
 Longitud máxima del búfer de nombre de ruta de acceso absoluta \(`absPath`\).  Esta longitud se muestra en bytes para `_fullpath` y en caracteres anchos \(`wchar_t`\) para `_wfullpath`.  
  
 `blockType`  
 Tipo de bloque de memoria solicitado: `_CLIENT_BLOCK` o `_NORMAL_BLOCK`.  
  
 `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación de asignación, o bien `NULL`.  
  
 `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o valor `NULL`.  
  
## Valor devuelto  
 Cada función devuelve un puntero al búfer que contiene el nombre de ruta de acceso absoluta \(`absPath`\).  Si se produce un error, por ejemplo, el valor que se pasa en `relPath` incluye una letra de unidad que no es válida o no se puede encontrar, o si la longitud del nombre de ruta de acceso absoluta creado \(`absPath`\) es mayor que `maxLength`, la función devuelve `NULL`.  
  
## Comentarios  
 Las funciones `_fullpath_dbg` y `_wfullpath_dbg` son idénticas a `_fullpath` y `_wfullpath`, salvo que, si **\_**`DEBUG` se define, estas funciones usan la versión de depuración de `malloc`, `_malloc_dbg`, para asignar memoria si se pasa NULL como primer parámetro.  Para obtener información sobre las características de depuración de `_malloc_dbg`, vea [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md).  
  
 En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría.  En lugar de ello, se puede definir la marca `_CRTDBG_MAP_ALLOC`.  Si se define `_CRTDBG_MAP_ALLOC`, las llamadas a `_fullpath` y `_wfullpath`se reasignan a `_fullpath_dbg` y `_wfullpath_dbg` respectivamente, con el parámetro `blockType` establecido en `_NORMAL_BLOCK`.  Por consiguiente, no necesario llamar a estas funciones explícitamente a menos que se desee marcar los bloques del montón como `_CLIENT_BLOCK`.  Para obtener más información, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tfullpath_dbg`|`_fullpath_dbg`|`_fullpath_dbg`|`_wfullpath_dbg`|  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_fullpath_dbg`|\<crtdbg.h\>|  
|`_wfullpath_dbg`|\<crtdbg.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## Equivalente en .NET Framework  
 <xref:System.IO.File.Create%2A>  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [\_fullpath, \_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)