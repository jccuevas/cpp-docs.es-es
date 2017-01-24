---
title: "_tempnam_dbg, _wtempnam_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wtempnam_dbg"
  - "_tempnam_dbg"
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
  - "wtempnam_dbg"
  - "tempnam_dbg"
  - "_tempnam_dbg"
  - "_wtempnam_dbg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tempnam_dbg (función)"
  - "_wtempnam_dbg (función)"
  - "nombres de archivo [C++], crear temporales"
  - "nombres de archivo [C++], temporal"
  - "tempnam_dbg (función)"
  - "archivos temporales, crear"
  - "wtempnam_dbg (función)"
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _tempnam_dbg, _wtempnam_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Versiones de función de [\_tempnam, \_wtempnam, tmpnam, \_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) que usan la versión de depuración de `malloc, _malloc_dbg`.  
  
## Sintaxis  
  
```  
char *_tempnam_dbg(    const char *dir,    const char *prefix,    int blockType,    const char *filename,    int linenumber  ); wchar_t *_wtempnam_dbg(    const wchar_t *dir,    const wchar_t *prefix,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### Parámetros  
 `dir`  
 Ruta de acceso que se usa en el nombre de archivo si no hay variable de entorno TMP, o si TMP no es un directorio válido.  
  
 `prefix`  
 Cadena que se va a anteponer a los nombres devueltos por `_tempnam`.  
  
 `blockType`  
 Tipo de bloque de memoria solicitado: `_CLIENT_BLOCK` o `_NORMAL_BLOCK`.  
  
 `filename`  
 Puntero al nombre del archivo de código fuente que solicitó la operación de asignación o `NULL`.  
  
 `linenumber`  
 Número de línea del archivo de código fuente en la que se solicitó la operación de asignación o valor `NULL`.  
  
## Valor devuelto  
 Cada función devuelve un puntero al nombre generado o `NULL` si se produce un error.  Pueden surgir errores si existe un nombre de directorio no válido en la variable de entorno TMP y en el parámetro `dir`.  
  
> [!NOTE]
>  No es necesario llamar a `free` \(o `free_dbg`\) en el caso de los punteros asignados por `_tempnam_dbg` y `_wtempnam_dbg`.  
  
## Comentarios  
 Las funciones `_tempnam_dbg`y `_wtempnam_dbg`son idénticas a `_tempnam`y `_wtempnam`salvo que, si `_DEBUG`se define, estas funciones usan la versión de depuración de `malloc` y `_malloc_dbg` para asignar memoria si se pasa `NULL` como primer parámetro.  Para obtener más información, vea [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md).  
  
 En la mayoría de los casos, no es necesario llamar a estas funciones explícitamente en la mayoría.  En lugar de ello, se puede definir la marca `_CRTDBG_MAP_ALLOC`.  Si se define `_CRTDBG_MAP_ALLOC`, las llamadas a `_tempnam` y `_wtempnam` se reasignan a  `_tempnam_dbg` y `_wtempnam_dbg`, respectivamente, con el parámetro `blockType` establecido en `_NORMAL_BLOCK`.  Por consiguiente, no necesario llamar a estas funciones explícitamente a menos que se desee marcar los bloques del montón como `_CLIENT_BLOCK`.  Para obtener más información, vea [Tipos de bloques en el montón de depuración](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_ttempnam_dbg`|`_tempnam_dbg`|`_tempnam_dbg`|`_wtempnam_dbg`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_tempnam_dbg`, `_wtempnam_dbg`|\<crtdbg.h\>|  
  
 Para más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [\_tempnam, \_wtempnam, tmpnam, \_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [Versiones de depuración de las funciones de asignación del montón](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)