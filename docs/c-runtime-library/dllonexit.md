---
title: "__dllonexit | Microsoft Docs"
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
  - "__dllonexit"
apilocation: 
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr120_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__dllonexit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__dllonexit"
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __dllonexit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Registra una rutina que se llama en el tiempo de salida.  
  
## Sintaxis  
  
```  
_onexit_t __dllonexit(  
   _onexit_t func,  
   _PVFV **  pbegin,   
   _PVFV **  pend   
   )  
```  
  
#### Parámetros  
 `func`  
 Puntero a una función que se ejecuta a la salida.  
  
 `pbegin`  
 El puntero a una variable que señala al principio de una lista de funciones para ejecutarse en desasocia.  
  
 `pend`  
 El puntero a la variable que apunta al final de una lista de funciones para ejecutarse en desasocia.  
  
## Valor devuelto  
 Si es correcto, un puntero a la función de usuario.  Si no, un puntero NULL.  
  
## Comentarios  
 La función de `__dllonexit` es análoga a la función de [\_onexit](../c-runtime-library/reference/onexit-onexit-m.md) salvo que las variables globales utilizadas por la función no son visibles para esta rutina.  En lugar de variables globales, esta función utiliza los parámetros de `pbegin` y de `pend` .  
  
 Las funciones de `_onexit` y de `atexit` en DLL vinculado con MSVCRT.LIB deben mantener su propia lista de atexit\/\_onexit.  Esta rutina es el trabajo que obtiene denominado por esos archivos DLL.  
  
 Define el tipo de `_PVFV` como `typedef void (__cdecl *_PVFV)(void)`.  
  
## Requisitos  
  
|Rutina|Archivo obligatorio|  
|------------|-------------------------|  
|\_\_dllonexit|onexit.c|  
  
## Vea también  
 [\_onexit, \_onexit\_m](../c-runtime-library/reference/onexit-onexit-m.md)