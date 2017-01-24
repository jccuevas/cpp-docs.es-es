---
title: "_get_pgmptr | Microsoft Docs"
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
  - "_get_pgmptr"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "get_pgmptr"
  - "_get_pgmptr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_pgmptr (función)"
  - "_pgmptr (variable global)"
  - "get_pgmptr (función)"
  - "pgmptr (variable global)"
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_pgmptr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene el valor actual de la variable globalde `_pgmptr`.  
  
## Sintaxis  
  
```  
errno_t _get_pgmptr(   
   char **pValue   
);  
```  
  
#### Parámetros  
 \[out\] `pValue`  
 Un puntero a una cadena se rellene con el valor actual de la variable de `_pgmptr` .  
  
## Valor devuelto  
 Devuelve cero si correctamente; un código de error del error.  Si `pValue` es `NULL`, se invoca el controlador no válido del parámetro tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EINVAL`.  
  
## Comentarios  
 La variableglobal de `_pgmptr`contiene la ruta de acceso completa al archivo ejecutable asociada al proceso.  Para obtener más información, vea [\_pgmptr, \_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_get_pgmptr`|\<stdlib.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente de .NET Framework  
 No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [\_get\_wpgmptr](../../c-runtime-library/reference/get-wpgmptr.md)