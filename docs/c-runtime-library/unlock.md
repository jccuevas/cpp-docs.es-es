---
title: "_unlock | Microsoft Docs"
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
  - "_unlock"
apilocation: 
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr120_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "unlock"
  - "_unlock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unlock (función)"
  - "_unlock (función)"
ms.assetid: 2eda2507-a134-4997-aa12-f2f8cb319e14
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _unlock
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Libera un bloqueo multiproceso.  
  
> [!IMPORTANT]
>  Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.  
  
## Sintaxis  
  
```  
void __cdecl _unlock(  
   int locknum  
);  
```  
  
#### Parámetros  
 \[in\] `locknum`  
 El identificador del bloqueo que se liberará.  
  
## Requisitos  
 **Origen:** mlock.c  
  
## Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [\_lock](../c-runtime-library/lock.md)