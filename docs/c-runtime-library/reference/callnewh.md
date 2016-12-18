---
title: "_callnewh | Microsoft Docs"
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
  - "_callnewh"
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
  - "_callnewh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_callnewh"
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _callnewh
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Llama al *nuevo controlador* instalado actualmente.  
  
## Sintaxis  
  
```cpp  
int _callnewh(  
   size_t size  
   )  
  
```  
  
#### Parámetros  
 `size`  
 Cantidad de memoria que el [nuevo operador](../../cpp/new-operator-cpp.md) intentó asignar.  
  
## Valor devuelto  
  
|Valor|Descripción|  
|-----------|-----------------|  
|0|Error: No se instala ningún controlador nuevo o no hay ningún controlador nuevo activo.|  
|1|Operación correcta: El controlador nuevo se instala y activa.  Se puede volver a intentar asignar memoria.|  
  
## Excepciones  
 Esta función genera [bad\_alloc](../../standard-library/bad-alloc-class.md) si el *controlador nuevo* no se puede localizar.  
  
## Comentarios  
 Se llama al *controlador nuevo* si [operador nuevo](../../cpp/new-operator-cpp.md) no asigna memoria correctamente.  El controlador nuevo podría iniciar una acción adecuada, por ejemplo liberar memoria de modo que las asignaciones subsiguientes se realicen correctamente.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|\_callnewh|internal.h|  
  
## Vea también  
 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md)   
 [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md)