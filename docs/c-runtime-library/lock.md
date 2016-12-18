---
title: "_lock | Microsoft Docs"
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
  - "_lock"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr120_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "lock"
  - "_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock (función)"
  - "_lock (función)"
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lock
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Adquiere un bloqueo multiproceso.  
  
> [!IMPORTANT]
>  Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.  
  
## Sintaxis  
  
```  
void __cdecl _lock  
   int locknum  
);  
```  
  
#### Parámetros  
 \[in\] `locknum`  
 El identificador del bloqueo que se adquirirá.  
  
## Comentarios  
 Si ya se adquirió el bloqueo, este método obtiene el bloqueo de todas formas y produce un error interno en tiempo de ejecución de C \(CRT\). Si el método no puede adquirir un bloqueo, se cierra con un error irrecuperable y establece el código de error en `_RT_LOCK`.  
  
## Requisitos  
 **Origen:** mlock.c  
  
## Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [\_unlock](../c-runtime-library/unlock.md)