---
title: "__setusermatherr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__setusermatherr"
apilocation: 
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__setusermatherr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__setusermatherr"
ms.assetid: f306818d-381a-4d68-8739-71b92bacb5ea
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# __setusermatherr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica un rountine usuario\- proporcionado para controlar errores matemático, en lugar de la rutina de [\_matherr](../c-runtime-library/reference/matherr.md) .  
  
## Sintaxis  
  
```cpp  
void __setusermatherr(  
   _HANDLE_MATH_ERROR pf   
   )  
  
```  
  
#### Parámetros  
 `pf`  
 Puntero a una implementación de `_matherr` proporcionado por el usuario.  
  
 Declara el tipo de parámetro de `pf` como `typedef int (__cdecl * _HANDLE_MATH_ERROR)(struct _exception *)`.  
  
## Comentarios  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|\_\_setusermatherr|matherr.c|