---
title: "_get_heap_handle | Microsoft Docs"
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
  - "_get_heap_handle"
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
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_get_heap_handle"
  - "get_heap_handle"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "funciones de montones"
  - "asignación de memoria, memoria de montón"
  - "_get_heap_handle (función)"
  - "get_heap_handle (función)"
ms.assetid: a4d05049-8528-494a-8281-a470d1e1115c
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_heap_handle
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el identificador del montón usado por el sistema en tiempo de ejecución de C.  
  
## Sintaxis  
  
```  
intptr_t _get_heap_handle( void );  
```  
  
## Valor devuelto  
 Devuelve el identificador del montón de Win32 usado por el sistema en tiempo de ejecución de C.  
  
## Comentarios  
 Use esta función si quiere llamar a [HeapSetInformation](http://msdn.microsoft.com/library/windows/desktop/aa366705) y habilitar el montón de baja fragmentación en el montón de CRT.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_get_heap_handle`|\<malloc.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_get_heap_handle.cpp  
// compile with: /MT  
#include <windows.h>  
#include <malloc.h>  
#include <stdio.h>  
  
int main(void)  
{  
    intptr_t hCrtHeap = _get_heap_handle();  
    ULONG ulEnableLFH = 2;  
    if (HeapSetInformation((PVOID)hCrtHeap,  
                           HeapCompatibilityInformation,  
                           &ulEnableLFH, sizeof(ulEnableLFH)))  
        puts("Enabling Low Fragmentation Heap succeeded");  
    else  
        puts("Enabling Low Fragmentation Heap failed");  
    return 0;  
}  
```  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)