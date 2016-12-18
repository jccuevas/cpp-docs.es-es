---
title: "_set_new_mode | Microsoft Docs"
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
  - "_set_new_mode"
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
  - "set_new_mode"
  - "_set_new_mode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_new_mode (función)"
  - "modos de controlador"
  - "set_new_mode (función)"
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_new_mode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece un nuevo modo de controlador para `malloc`.  
  
## Sintaxis  
  
```  
int _set_new_mode(  
   int newhandlermode   
);  
```  
  
#### Parámetros  
 `newhandlermode`  
 Nuevo modo de controlador para `malloc`; el valor válido es 0 o 1.  
  
## Valor devuelto  
 Devuelve el modo anterior de controlador establecido para `malloc`.  Devuelve un valor de 1 indica que, en el error asignar memoria, `malloc` denominado previamente la nueva rutina de controlador; devuelve un valor de 0 indica que no realizó.  Si el argumento de `newhandlermode` no es igual a 0 o 1, devuelve – 1.  
  
## Comentarios  
 La función de C\+\+ `_set_new_mode` establece el nuevo modo de controlador para [malloc](../../c-runtime-library/reference/malloc.md).  El nuevo modo de controlador indica si, en caso de error, `malloc` debe llamar a la nueva rutina de controlador como se establece por [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md).  De forma predeterminada, `malloc` no llama a la nueva rutina del controlador si no se puede asignar memoria.  Puede invalidar este comportamiento predeterminado para que, cuando `malloc` no puede asignar memoria, `malloc` llama a la nueva rutina de controlador de la misma manera que hace el operador `new` cuando produce errores por la misma razón.  Para obtener más información, vea operadores de [new](../../cpp/new-operator-cpp.md) y de [borrar](../../cpp/delete-operator-cpp.md) en *la referencia del lenguaje C\+\+*.  Para reemplazar el valor predeterminado, llame a:  
  
```  
_set_new_mode(1)  
```  
  
 al principio del programa o el vínculo con Newmode.obj \(vea [Opciones de vínculo](../../c-runtime-library/link-options.md)\).  
  
 Esta función valida su parámetro.  Si `newhandlermode` es algo distinto de 0 o de 1, la función invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, **\_**`set_new_mode` devuelve \-1 y establece `errno` a `EINVAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_set_new_mode`|\<new.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_query\_new\_handler](../../c-runtime-library/reference/query-new-handler.md)   
 [\_query\_new\_mode](../../c-runtime-library/reference/query-new-mode.md)