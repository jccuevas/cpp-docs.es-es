---
title: "_strdup_dbg, _wcsdup_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strdup_dbg"
  - "_wcsdup_dbg"
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
  - "_wcsdup_dbg"
  - "strdup_dbg"
  - "_strdup_dbg"
  - "wcsdup_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strdup_dbg (función)"
  - "_wcsdup_dbg (función)"
  - "copiar cadenas"
  - "duplicar cadenas"
  - "stdup_dbg (función)"
  - "cadenas [C++], copiar"
  - "cadenas [C++], duplicar"
  - "wcsdup_dbg (función)"
ms.assetid: 681db70c-d124-43ab-b83e-5eeea9035097
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _strdup_dbg, _wcsdup_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Versiones de [\_strdup y \_wcsdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md) que usan la versión de depuración de `malloc`.  
  
## Sintaxis  
  
```  
char *_strdup_dbg(    const char *strSource,    int blockType,    const char *filename,    int linenumber  ); wchar_t *_wcsdup_dbg(    const wchar_t *strSource,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### Parámetros  
 `strSource`  
 Cadena de origen terminada en NULL.  
  
 `blockType`  
 Tipo de bloque de memoria solicitado: `_CLIENT_BLOCK` o `_NORMAL_BLOCK`.  
  
 `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o NULL.  
  
 `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o valor NULL.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un puntero a la ubicación de almacenamiento para la cadena copiada o `NULL` si no se puede asignar almacenamiento.  
  
## Comentarios  
 Las funciones `_strdup_dbg` y `_wcsdup_dbg` son idénticas a `_strdup` y `_wcsdup`, salvo que, si se define `_DEBUG`, estas funciones usan la versión de depuración de `malloc`, `_malloc_dbg`, para asignar memoria para la cadena duplicada.  Para más información sobre las características de depuración de `_malloc_dbg`, vea [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md).  
  
 En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría.  En lugar de ello, se puede definir la marca `_CRTDBG_MAP_ALLOC`.  Si se define `_CRTDBG_MAP_ALLOC`, las llamadas a `_strdup` y `_wcsdup` se reasignan a `_strdup_dbg` y `_wcsdup_dbg`, respectivamente, con el parámetro `blockType` establecido en `_NORMAL_BLOCK`.  Por consiguiente, no necesario llamar a estas funciones explícitamente a menos que se desee marcar los bloques del montón como `_CLIENT_BLOCK`.  Para más información sobre los tipos de bloques, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsdup_dbg`|`_strdup_dbg`|`_mbsdup`|`_wcsdup_dbg`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strdup_dbg`, `_wcsdup_dbg`|\<crtdbg.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 [System::String::Clone](https://msdn.microsoft.com/en-us/library/system.string.clone.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strdup, \_wcsdup, \_mbsdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)   
 [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)