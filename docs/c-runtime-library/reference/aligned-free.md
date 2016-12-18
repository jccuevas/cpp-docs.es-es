---
title: "_aligned_free | Microsoft Docs"
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
  - "_aligned_free"
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
  - "aligned_free"
  - "_aligned_free"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_aligned_free (función)"
  - "aligned_free (función)"
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _aligned_free
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Libera un bloque de memoria que fue asignado con [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [\_aligned\_offset\_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md).  
  
## Sintaxis  
  
```  
void _aligned_free (  
   void *memblock  
);  
```  
  
#### Parámetros  
 `memblock`  
 Un puntero al bloque de memoria que se devuelve a la función de `_aligned_malloc` o de `_aligned_offset_malloc` .  
  
## Comentarios  
 `_aligned_free` es `__declspec(noalias)`marcado, lo que significa que la función está garantizada para no modificar variables globales.  Para obtener más información, vea [noalias](../../cpp/noalias.md).  
  
 Esta función no valida su parámetro, a diferencia de las demás funciones \_aligned CRT.  Si `memblock` es un puntero de `NULL` , esta función no realiza simplemente ninguna acción.  No cambia `errno` y no invoca el controlador no válido del parámetro.  Si se produce un error en la función debido no mediante funciones \_aligned a previamente asignar el bloque de memoria o una desalineación de memoria se produce debido a alguna calamidad imprevista, la función genera un informe de depuración de [\_RPT, \_RPTF, \_RPTW, \_RPTFW \(Macros\)](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_aligned_free`|\<malloc.h\>|  
  
## Ejemplo  
 Para obtener más información, vea [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Alineación de datos](../../c-runtime-library/data-alignment.md)